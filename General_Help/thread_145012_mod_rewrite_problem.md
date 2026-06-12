---
title: "mod_rewrite problem"
date: 2006-03-15
forum: General Help
---

### Post by VinceDee on 2006-03-15
I posted this in the server talk forum, but it hasn't gotten any responses, so I'm hoping that somebody here has a answer:

I'm having problems getting mod_rewrite to work in on my LAMP server, and I can't figure out what's wrong. I've also already googled and searched the forums to no avail:


According to phpinfo.php:  mod_rewrite is loaded

Following the various directions available that are apparently working for other people (including the following link):
[http://www.ubuntuforums.org/showthre...ht=mod_rewrite](http://www.ubuntuforums.org/showthre...ht=mod_rewrite)

1. sudo a2enmod rewrite

2. made sure that the following was in either the apache2.conf, or .htaccess file of whatever website directory I'm working with:

<IfModule mod_rewrite.c>
RewriteEngine on
</IfModule>

3. modified the /etc/apache2/sites_enabled/000-default.conf file so that the directory entry read:

AllowOverride all

But the progam I'm installing (drupalCMS from drupal.org) on one of my virtual websites says:

"It appears your host is not configured correctly for Clean URLs. Please check for ModRewrite support with your administrator."

Any ideas?

---

### Post by emaxware on 2007-03-23
had a similar problem.  fixed it by uncommenting 

RewriteBase /drupal

in .htaccess in the drupal install directory.  Maybe this will help.

---

