---
title: "Need help with permissions"
date: 2011-03-25
forum: General Help
---

### Post by wildscribe on 2011-03-25
Hi Folks,

I am running 10.10 32-bit desktop and have successfully installed LAMP with phpmyadmin. I also installed Joomla 1.6. I am doing some website development work and want to do it locally before I upload it to a live site.

Here is my problem. I cannot get write permissions to work. The only way I can create and write to a file is by using Terminal and using the command line in /var/www, like $ sudo chmod pico index.html

It won't let me save files. I want to use the Blue Fish editor and Netbeans and I cannot save.

I tried doing $ sudo chown username -r www and even $ sudo chmod 755 -r www

And nothing works. Please help. I want to start this project soon.


All best,

WiLd

---

### Post by doas777 on 2011-03-25
easiest answer would be to run netbeans and bluefish as root with gksu. 

please post back:
```
ls -al /var/www/
```keep in mind though, for a secure system, you should not be able to do what you want to do. if this will be a public-facing system, just do it the hard way (save the files to your home and copy them to your www using root privledges. )

---

### Post by SmilePiper on 2011-03-25
You might also try running

$: gksudo nautilus

in the terminal.  doing this will open a file browser which will let you act as an administrator and override a lot of permissions.

---

### Post by wildscribe on 2011-03-25
Thank you Doas.

This is what I get after I do $ sudo ls -al /var/www


d-wx--x--x  3 stephen root 4096 2011-03-25 15:35 .
drwxr-xr-x 15 root    root 4096 2011-03-20 22:31 ..
-rw-r--r--  1 stephen root  177 2011-03-20 22:32 index.html
drwxr-x--x 15 stephen root 4096 2011-03-25 15:59 joomla
stephen@stephen-linux:/$ 

And I am running this PC behind a firewall and I have not plans to open up this server to the public Internet.

Thanks again!

---

### Post by wildscribe on 2011-03-25
This worked! Thank you SmilePiper. 

I still want to figure out how to do it the so-called "right way" because I want to eventually set up an Ubuntu server, but I can worry about that later.

Thanks again. 

QUOTE=SmilePiper;10600754]You might also try running

$: gksudo nautilus

in the terminal.  doing this will open a file browser which will let you act as an administrator and override a lot of permissions.[/QUOTE]

---

### Post by doas777 on 2011-03-25
kewl, glad that works for you. to keep your apache happy, you should probably chown those directories back to root:root
```

sudo chown -R root:root /var/www
```

cheers!

---

