---
title: "firefox does not open php files"
date: 2010-08-17
forum: General Help
---

### Post by migsy16 on 2010-08-17
Hi! Firefox doesnt read php files. my files are located at /var/www. html files are displayed without problems. Am I missing anything on my apache config? I've tried Modifying my apache2.conf file by adding an AddType ...... Any insight would be appreciated. Thanks.

---

### Post by DaithiF on 2010-08-17
firefox (or any browser for that matter) does not read & execute the php in php files.  you need php to be installed on the server then when serving a php file the server executes the php code, generates (usually) html output, and serves that html to your browser.  have you installed php?

---

### Post by migsy16 on 2010-08-17
I made a file info.php which basically just contains <?php phpinfo() ?> and firefox was able to parse it. I tried to make a basic html file with a .php extension and it wouldnt load up on my browser. I have checked my php version using dpkg  -l|grep -i php and it says I've got PHP 5 on. I am deeply puzzled .....thanks for the quick reply....

---

### Post by DaithiF on 2010-08-17
you're sure its not just firefox caching an earlier blank version of the file?  do a force-reload (ctrl + F5) of the page to check.

---

### Post by migsy16 on 2010-08-17
I've tried emptying my cache...... no go.......this is disturbing...... grrrrrr

---

### Post by ricks.wesley on 2010-08-17
i am facing the same problem..please help me out of this..

---

### Post by mitsios on 2010-08-17
Post your php file so we can see it.

---

### Post by Cilph on 2010-08-17
PHP is a server-side script. Firefox is not ever supposed to receive and/or read a PHP file. Check your webserver settings because Firefox is supposed to receive plain HTML.

---

### Post by mitsios on 2010-08-17
In order for Apache to parse php files, you need to access the file from firefox by its http address, "http://127.0.0.1/<path to file>"

---

### Post by migsy16 on 2010-08-17
<?php
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
    <title>Basic</title>
</head>
<body>
   <?php echo "trial"; ?>
</body>
</html>
?>



TNX!!!

---

### Post by WorMzy on 2010-08-17
If you are trying to view the page through your server (e.g. [http://127.0.0.1/pagename.php](http://127.0.0.1/pagename.php) or [http://localhost/pagename.php](http://localhost/pagename.php)), then you may have an error in your code. Post it here and we'll take a look, or enable error reporting in the php.ini file and see where the error is being found.

You can edit php settings by editing /etc/php5/apache2/php.ini, e.g. ```
gksu gedit /etc/php5/apache2/php.ini
```

After you've made your changes and saved the file, restart the webserver by running
```
/etc/init.d/apache2 restart
```
Or possibly
```
sudo service apache2 restart
```
I forget what Ubuntu uses these days.

---

### Post by WorMzy on 2010-08-17
> <?php
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Basic</title>
</head>
<body>
<?php echo "trial"; ?>
</body>
</html>
?>


The start "<?php" and end "?>" are superfluous. You're telling the PHP parser that all the code after the opening tag is PHP, which it isn't.

You code should look like this:

```

<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  <head>
    <title>Basic</title>
  </head>
  <body>
    <?php echo "trial"; ?>
  </body>
</html>

```

---

### Post by migsy16 on 2010-08-17
I think there might have been a problem with the dtd...... ive tried a different dtd for my html and it worked.... i still dont know why an xhtml strict would not parse though......thanks for all your help

---

### Post by WorMzy on 2010-08-17
There's nothing wrong with the DTD, I always use Strict (or HTML5) for my PHP pages.

---

### Post by migsy16 on 2010-08-17
tnx worMzy.... I tried it without the PHP tags......and it still didnt work....I tried a different dtd and minus the php tags just as what wormzy described and it finally worked ......Thanks everyone!  :)

---

### Post by migsy16 on 2010-08-17
funny how mine got an error with the dtd i posted ...... it worked right after i replaced it with a different dtd......hmmmmm

---

### Post by mitsios on 2010-08-17
<removed>

---

### Post by WorMzy on 2010-08-17
If you're really serving it as XHTML with the application/xhtml+xml MIME type, then you'll get an error from the lack of paragraph tags around the text. You could add those and see if it fixes things.

---

