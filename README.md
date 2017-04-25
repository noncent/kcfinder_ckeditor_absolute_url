### How To Setup KCFinder with absolute URL with CkEditor:

Recently in a project I need to use some Rich Text Formatter (RTF)/WYSIWYG text editor, I decided to select some of available in web.

I wanted to upload images via WYSIWYG text editor, so I used:

> A) - CKEditor

> B) - KCFinder as alternative of CkFinder

> C) - Prevent WYSIWYG upload access, if user not login


I wanted absolute url of upload image or selected image from WYSIWYG text editor
e.g. "http://localhost/CkEditor-KcFinder/upload/4856dkfgd674768.jpg"

I also found that many users are confuse to setup KCFinder with CKEditor. They all are searching "How to get absolute url in KCFinder?".

So I just made a demo about KCFinder setup with CKEditor. The code ready to use, what you have to do

> 1) download repository/clone
> 2) unzip the source code in your wamp/lamp/xamp root folder and access the url to start demo
> 3) open http://localhost/CkEditor-KcFinder/

### Version Details
> A) - CkEditor 4.6.2
> B) - KcFinder 3.12

### Path Details
> A) - Project 	Path - D:/wamp/www/CkEditor-KcFinder
> B) - Upload  	Path - D:/wamp/www/CkEditor-KcFinder/upload
> C) - CkEditor 	Path - D:/wamp/www/CkEditor-KcFinder/ckeditor
> D) - KcFinder 	Path - D:/wamp/www/CkEditor-KcFinder/kcfinder

### Setting Details - settings.php
Make the changes according to your requirement in "D:/wamp/www/CkEditor-KcFinder/settings.php"


### File information:
- KcFinder Core Changes
> File: D:\wamp\www\CkEditor-KcFinder\kcfinder\core\bootstrap.php

```php
# To check valid SESSION, I have added below code:
/**
 * Start the PHP SESSION if not started already
 */
if (!session_id()) session_start();
/**
 * First of all Check Valid SESSION to access rest 
 */
if (!isset($_SESSION[$_SESSION['AuthCheckKey']]) || $_SESSION[$_SESSION['AuthCheckKey']] === false) {
    die ('Unauthorized access detected.. Service terminated.');
}
```
- KcFinder Config Changes
> File: D:\wamp\www\CkEditor-KcFinder\kcfinder\conf\config.php

We don't need to set anything in 'config.php' actually, if we are using, 'KCFINDER' session variable to store the session configuration. 

This session variable can be set by integrating application to configure KCFinder before its opening. 
It should contain an array with dynamic settings. The settings which don't exists in the array will use their values 
set in conf/config.php file. For example, to enable KCFinder you should execute from your application:

Please see the details: https://kcfinder.sunhater.com/install

```php
$_SESSION['KCFINDER'] = array(
    'disabled' => false
);
```


```php
'disabled' => '',
'uploadURL' => '',
'uploadDir' => '',
 ```

Thanks to kcfinder and ckeditor to make these AWESOME tools.. :) 

1 - https://kcfinder.sunhater.com/install
2 - http://ckeditor.com/

# End Here




