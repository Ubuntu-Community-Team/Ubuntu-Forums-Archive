---
title: "Where is my web server ? (localhost)"
date: 2011-09-30
forum: General Help
---

### Post by sarahfoxnz on 2011-09-30
Hello.

I want to start a web server on my Pc (for my own personal use)

- PHP
- MYSQL


however, I went to [http://localhost/](http://localhost/) and there is already a website running - Just says "hello" etc...

If i put [http://localhost/random.html](http://localhost/random.html)  - it comes up woth an error -  Its an Apache/2.2.14 (Ubuntu) Server

1) how can I find out which directory the html files are in / stored ?

2) is there a guide / tutorial on how to install PHP and/or  MYSQL ?

(I could probably figure it out - if given time, once i locate the correct directory)


PS - If its stored outside of my own / home directory - Is there some process I need to edit the files ? (permission ?)

---

### Post by pqwoerituytrueiwoq on 2011-09-30
default location is /var/www/

---

### Post by sarahfoxnz on 2011-09-30
[http://ubuntuexperiment.wordpress.com/2008/11/10/installing-apache-php-mysql/](http://ubuntuexperiment.wordpress.com/2008/11/10/installing-apache-php-mysql/)

Hi.

i've found this - & everthing is working except MYSQL.. 


> 
update-initramfs: deferring update (trigger activated)
start: Job failed to start
dpkg: error processing eee-control (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libapache2-mod-auth-mysql (4.3.9-12ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic
Errors were encountered while processing:
 eee-control
E: Sub-process /usr/bin/dpkg returned an error code (1)



The above error was after I did :-  [I]sudo apt-get install mysql-server libapache2-mod-auth-mysql php5-mysql


It had a long list of 'installing'..  etc - & then a minute or so after, i got the above error  

What is EEE ?  ? 
[/I]

---

### Post by sarahfoxnz on 2011-09-30
Fixed EEE

> 
sudo cp /var/lib/dpkg/status ~/Desktop/status.bak gksu gedit /var/lib/dpkg/status


i removed the EEE section & re-ran the mysql support 

(nearly there...  ....  )

just got to find out how to set a master password

---

### Post by sarahfoxnz on 2011-09-30
PROBLEM FIXED

I've found / located the server files & can edit them no worries.

However - I've got a seperate issue, i'll create a new thread thats more relevant subject..

---

