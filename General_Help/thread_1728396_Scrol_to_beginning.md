---
title: "Scrol to beginning"
date: 2011-04-13
forum: General Help
---

### Post by borgward on 2011-04-13
ls /usr/share/doc$

ibus-gtk                              mscompress
ibus-m17n                             mtools
ibus-table                            mtr-tiny
icedtea-6-jre-cacao                   myspell-en-au
icedtea6-plugin                       myspell-en-gb
icoutils                              myspell-en-za
ifupdown                              mysql-client-core-5.1

.........

libneon27-gnutls                      x-ttcidfont-conf
libnet-dbus-perl                      xulrunner-1.9.2
libnewt0.52                           yelp
libnice0                              zenity
libnih1                               zip
libnih-dbus1                          zlib1g

How do I scroll back up to the top, or get the output to display page by page?

Home, Page Up, only bring me back to the bottom of the output.

---

### Post by borgward on 2011-04-13
Problem solved.

ls -l /usr/share/doc | less

what is the most lines terminal can display of the results of ls? Any way to change that value?

---

### Post by vivek.pandey on 2011-04-14
you can use redirection as well
say you typed netstat on terminal it displays a whole bunch of lines which cant be scrolled till top under normal settings.. to get the complete output
```
 netstat>netstat
```
you will get a text file by name netstat in your current directory . you can view it with any text editor like gedit

---

