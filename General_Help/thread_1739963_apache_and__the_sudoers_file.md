---
title: "apache and  the sudoers file"
date: 2011-04-26
forum: General Help
---

### Post by slaz on 2011-04-26
Hi,
 
I am running ubuntu server 10.10, I have a perl script that I put in /var/lib/cgi-bin. This script has the sudo command in it. It seems fine when I run it from the terminal. When I open a browser and run the script it doesn't work. Looking at /var/www/apache2/error.log, this line keeps repeating:
 
sudo: no tty present and no askpass program specified
sudo: no tty present and no askpass program specified
 
I tried adding myself to the sudo group, but didn't work. The only thing the sript has to do is copy a file. This was originally done a slackware box, but I am trying to get this to work on ubuntu now.
 
thanks,
slaz

---

