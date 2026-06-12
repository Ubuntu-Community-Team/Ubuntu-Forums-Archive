---
title: "LAMP Install"
date: 2011-08-12
forum: General Help
---

### Post by zebraneo on 2011-08-12
I am trying to install LAMP and it get this message what do I do


me@me-laptop:~$ sudo apt-get install tasksel
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
tasksel is already the newest version.
The following packages were automatically installed and are no longer required:
  libdv-bin ttf-dejavu libxml++2.6-2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
me@me-laptop:~$ su apt-get autoremove
Unknown id: apt-get

This any help would be helpful

---

### Post by aeiah on 2011-08-12
'su' doesn't work like that - it logs you in as root. sudo runs the command as root.

but 'sudo apt-get autoremove' won't install lamp, it will just remove those things it told you it will. you can install lamp with tasksel (which is why you installed it). its simpler than running several apt-get commands for the different lamp components

```

sudo tasksel install lamp-server
```

---

### Post by PsyclonJohn on 2011-08-12
Check out my article on a full installation of LAMP and PhpMyAdmin:

[http://life.projektdeth.com/2011/04/30/installing-lamp-in-ubuntu-10-10/](http://life.projektdeth.com/2011/04/30/installing-lamp-in-ubuntu-10-10/)

---

### Post by zebraneo on 2011-08-12
I went to the  article on a full installation of LAMP and PhpMyAdmin:

[http://life.projektdeth.com/2011/04/...-ubuntu-10-10/]("http://life.projektdeth.com/2011/04/30/installing-lamp-in-ubuntu-10-10/")

I did what it said and I got to step 2  and and I do not see a blue menu, doesn't appear 
What do I do??

**Step 2.**
 After everything downloads and installs, do the following:
Type into the Terminal: sudo apt-get install phpmyadmin
 When the blue menu appears, make sure you select (**spacebar**) Apache2.
 It’s then going to ask you for a password for Root so you can access  PHPMyADMIN. I recommend having all the passwords the same so it’s easier  and you don’t end up forgetting the passwords for each login. 
 After that finishes, and all passwords are at input. Open up a web  browser and type in Localhost, and you should receive a page saying “It  works!”. All your files are located inside Computer/File System/var/www  and where files can be created and modified, but theres also a problem  there too! If your not under Root, you will not be able to work on  anything. 
 You may use this inside Terminal to create and modify files: *gksudo nautilus*

---

