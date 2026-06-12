---
title: "Basic File Upload Server"
date: 2011-05-12
forum: General Help
---

### Post by physic.dude on 2011-05-12
I only just started to get the hang of this web server stuff. I recently set up a basic web server using apache2 and Ubuntu, and in the future I would like to use part of it as a basic file upload/download server. 

HTML seems to be the only type of website coding I understand inside and out. PHP and all the other things are not exactly my forte. Also, I have not done any modifying to apache's default configuration files other then set the website root file directory away from /var/www.

I have searched Google and found many different and complex ways to  do such a task. Does anyone have any basic solutions for me to do this?  It wouldn't be anything special, just a basic HTML upload form that puts  the desired file into a directory I specify. Then later I can download  it using it's URL or just go into the directory I saved it in if  necessary.

---

### Post by physic.dude on 2011-05-13
Bump
Just a simple way for me or friends to send or store files.

---

### Post by Slim Odds on 2011-05-13
Dropbox  [https://www.dropbox.com/](https://www.dropbox.com/)

---

### Post by physic.dude on 2011-05-13
> **Slim Odds said:**
> Dropbox  [https://www.dropbox.com/](https://www.dropbox.com/)

Not exactly what I'm looking for,
I just want to make a working yet basic 'browse' and 'submit' form in HTML that uploads desired files. Its just that I'm not sure what tools or settings I might need on my server.

---

### Post by Bo Fussing on 2011-05-13
@physics.dude

You might like to consider using WebDAV on Apache which is designed for file sharing. I found this article on how to set it up on Natty [http://essayboard.com/2011/05/09/setting-up-webdav-on-ubuntu-11-04/]("http://essayboard.com/2011/05/09/setting-up-webdav-on-ubuntu-11-04/")

Bo

---

### Post by physic.dude on 2011-05-13
> **Bo Fussing said:**
> @physics.dude

You might like to consider using WebDAV on Apache which is designed for file sharing. I found this article on how to set it up on Natty [http://essayboard.com/2011/05/09/setting-up-webdav-on-ubuntu-11-04/](http://essayboard.com/2011/05/09/setting-up-webdav-on-ubuntu-11-04/)

Bo

Looks interesting, and I'll keep in in mind, but its still not exactly what I'm looking for. 

Any more suggestions?

---

### Post by MegaLoler on 2011-05-13
If you have PHP installed you can make an HTML form that uploads a file to a php script which saves it to a location on the server.

See [http://www.tizag.com/phpT/fileupload.php](http://www.tizag.com/phpT/fileupload.php) for a simple tutorial on how to do it.  It is just HTML and PHP.

---

### Post by physic.dude on 2011-05-14
> **MegaLoler said:**
> If you have PHP installed you can make an HTML form that uploads a file to a php script which saves it to a location on the server.

See [http://www.tizag.com/phpT/fileupload.php](http://www.tizag.com/phpT/fileupload.php) for a simple tutorial on how to do it.  It is just HTML and PHP.


Ah, yes, thats what I'm looking for, but there is a small problem I cant seem to find a solution to.
I have PHP installed, but the PHP file that is suppose to run, gets displayed as plain text. What do I do? I think it has something to do with a config file.

---

### Post by MegaLoler on 2011-05-14
You must put php code in these tags:

```
<?php
(code here)
?>
```Only then will it be executed by the server as PHP code, everything outside those tags is considered regular HTML.

---

### Post by physic.dude on 2011-05-14
> **MegaLoler said:**
> You must put php code in these tags:

```
<?php
(code here)
?>
```Only then will it be executed by the server as PHP code, everything outside those tags is considered regular HTML.

*Face-palm*

#-o

I knew that... 
Thanks, it works now. :mrgreen:

---

