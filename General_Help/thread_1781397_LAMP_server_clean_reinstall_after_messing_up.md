---
title: "LAMP server clean reinstall after messing up"
date: 2011-06-13
forum: General Help
---

### Post by fnohe on 2011-06-13
Hello, I am trying to install Drupal locally.

I actually got Apache, MySQL, PHP, and Drupal 7 installed alright, but I started messing with the Apache server configuration when "clean URLs" were not working.

I have also in the meantime deleted /var/www and its contents and tried to install Drupal again. Now everything is messed up and I can't figure out what I've done. So what I'd like to do is start from scratch, but it's not so easy either. 

I have tried the following
```
sudo apt-get --purge remove apache2 php5-common php5-mysql libapache2-mod-php5 mysql-server
```But I got a few errors saying that some directories were not empty and thus not removed.
After reinstalling LAMP anyway I got blank pages when I tried to run the Drupal installation script. When I turned on PHP error reporting (don't ask me how), I got the following error on running the Drupal installation script:

```
Warning: require_once(/var/www/includes/bootstrap.inc): failed to open  stream: Permission denied in /var/www/index.php on line 25  Fatal error: require_once(): Failed opening required  '/var/www/includes/bootstrap.inc'  (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/index.php  on line 25
```Can anyone help me get a clean LAMP installation? No need to backup anything as I haven't done any work yet beyond creating a mess. I'm very frustrated because I had it running OK before I started doing things I had no idea of...

---

