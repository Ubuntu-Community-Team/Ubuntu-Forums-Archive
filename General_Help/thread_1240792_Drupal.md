---
title: "Drupal"
date: 2009-08-15
forum: General Help
---

### Post by nipunreddevil on 2009-08-15
i just installed drupal with synaptic package manager.How do i use it.I have no prior experience of drupal
Running /localhost/drupal gave error 404.

---

### Post by sigixv on 2009-08-15
[http://drupal.org/Troubleshooting-FAQ](http://drupal.org/Troubleshooting-FAQ)

the error 404 seems to be only something of "page not found"

---

### Post by j0rd on 2009-09-01
You're going to want to make sure you have a web server like Apache installed with PHP enabled.

Make sure you can visit your [http://localhost](http://localhost) and see a website popup.

Then you'll want to install Drupal under the proper directory. I assume the package manager would do this for you. Otherwise you'll have to configure a site under /etc/apache/sites-enabled for it to use.

Once that's all done and the vhost is serving up the Drupal files, you'll want to create a database under MySQL and GRANT it the proper privileges. 

Then you'll need to edit the htdocs/sites/default/settings.php to reflect the database, user and password you created. 

After that's all done, you can visit your drupal site and go through the install process.

---

### Post by go2dell on 2009-09-10
> **j0rd said:**
> You're going to want to make sure you have a web server like Apache installed with PHP enabled.

Make sure you can visit your [http://localhost](http://localhost) and see a website popup.

Then you'll want to install Drupal under the proper directory. I assume the package manager would do this for you. Otherwise you'll have to configure a site under /etc/apache/sites-enabled for it to use.

Once that's all done and the vhost is serving up the Drupal files, you'll want to create a database under MySQL and GRANT it the proper privileges. 

Then you'll need to edit the htdocs/sites/default/settings.php to reflect the database, user and password you created. 

After that's all done, you can visit your drupal site and go through the install process.

The Ubuntu Drupal packages take care of all this garbage for you.  The one thing you need to remember is that if you actually care WHICH http server, database server, mail server, etc., you're using, then you should set them up before installing the Drupal package.

```
sudo tasksel install lamp-server
``` will install a basic Linux/Apache/MySQL/PHP system for you.

```
sudo tasksel install mail-server
``` will install a mail server, which is also required for Drupal.

Then you can install either the drupal5 or drupal6 package.  Installing either without first installing the LAMP and mail servers will let the Drupal packages make most of the decisions for you.  If you want to live on the bleeding edge, I've published a PPA with the latest versions of Drupal5 and Drupal6 [here]("https://launchpad.net/~scott-testerman/+archive/ppa").

In any case, if you use the Ubuntu packages, be absolutely certain to read /usr/share/doc/drupal5/README.Debian.gz or /usr/share/doc/drupal6/README.Debian.gz for the Ubuntu specifics that you'll need to know.

Your final install is located at http://yoursever/drupal5 or http://yourserver/drupal6.

---

