---
title: "sed command -- need some help"
date: 2009-12-27
forum: General Help
---

### Post by sr_guy on 2009-12-27
I'm writing a script based on this wiki:

[http://www.joeterranova.net/wiki/index.php?title=Install_Asterisk](http://www.joeterranova.net/wiki/index.php?title=Install_Asterisk)

I need to use the sed command to change the below sections by using sed to search the particular files and auto change the text. Any help is appreciated.


cd asterisk-1.4.23.1
nano -w Makefile
(change all instances of "ASTVARRUNDIR=<something>" to "ASTVARRUNDIR=/var/run/asterisk"

----------------------------------------


Additional setup

We need to tell Asterisk to only use rtp ports 10000 - 10100. If you're some crazy telephony wiz kid you needs more that 100 simultaneous voice channels, increase this port range higher (up to 20000 if you want), and in both your router forwarding / firewall rules.

sudo nano -w /etc/asterisk/rtp.conf

change to:

rtpstart=10000
rtpend=10100

---------------------------------------------------


Configure Asterisk Files:

sudo nano -w /etc/asterisk/asterisk.conf

change astrundir =>  to /var/run/asterisk


sudo nano -w /etc/php5/apache2/php.ini
sudo nano -w /etc/php5/cli/php.ini

change these values:

post_max_size = 20M
upload_max_filesize = 20M
magic_quotes_gpc = Off
memory_limit = 100M

---

### Post by DaithiF on 2009-12-27
heres the first one, you can probably figure out the others from this:
```
sed -i.bak 's#ASTVARRUNDIR=.*$#ASTVARRUNDIR=/var/run/asterisk#' Makefile
```

The -i tells sed to make the change in-place, ie. to save the Makefile with whatever changes it makes, the .bak will create a back-up copy of the original file.

---

