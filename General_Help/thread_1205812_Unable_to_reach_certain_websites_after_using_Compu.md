---
title: "Unable to reach certain websites after using Computer Janitor"
date: 2009-07-06
forum: General Help
---

### Post by gmakor on 2009-07-06
Hi there, 
 
I've been using Ubuntu since 2 weeks and am very very pleased to be out of the claws of Miscrosoft, especially the excrutiating slowness of XP and Vista compared to Ubuntu 904 and Microsoft's mindboggingly stupid error mesages (such as 'Exception Processing Message c0000013 Parameters 75b6bf9c 4 75b6bf9c 75b6bf9c').
 
Having said that, I must admit I am writing this in IE in Windows XP. The reason is that I cannot reach certain websites anymore, ubuntuforums being one of them. These are some Dutch sites (but not all), and many of the Ubuntu related sites I find. Also, and this is really bothering me, Synaptic is unable to reach any of the repositories anymore.
 
This all started after I used Computer Janitor to 'clean' my system last night. As a former Windows user of almost 25 years I am used to all kinds of utilities that clean my system without me having to understand all the technical details. I exptected CJ to work in the same way. 
 
However, it messed up my screen resolution on Ubuntu (which I managed to repair by downloading the correct drivers from the windows partition, sorry...). I suspect it messed with my flash installation to render certain sites unreachable.
 
Help would be appreciated.
 
What should I do now? 
Can I reinstall Ubuntu 9.04 without loosing everything I changed (such as new theme and login screen) and installed (such as Flock and a couple of other applications)?
What should I do to make Flock or Firefox and Synaptic reach sites and repositories again?
 
Thanks in advance!
 
Best regards,
Guido
 
PS:
My system - 
Ubuntu 9.04
Asus X58C laptop
3Gb RAM
dualboot Ubuntu/Windows
Ubuntu running on ntfs

---

### Post by Jebtrix on 2009-07-06
Try 

```
sudo apt-get install --reinstall firefox
```

---

### Post by Jebtrix on 2009-07-06
I know I've seen xulrunner-1.9 come up as no longer used one time, which IS used by firefox. Maybe:

```
sudo apt-get install xulrunner-1.9
```

---

### Post by Soul-Sing on 2009-07-06
Computer janitor should be used carefully, it suggests sometimes things you dont want to remove.(!)
- flock
- opera
did janitor suggest to remove firefox? What did you remove?

---

### Post by Jebtrix on 2009-07-06
Maybe I misread your post a bit. Open terminal try:

```
cat /var/log/dpkg.log | grep remove
```
```
cat /var/log/dpkg.log.1 | grep remove
```

This should tell what packages were removed. Just post the results of the commands.

---

### Post by Soul-Sing on 2009-07-06
> **jebtrix said:**
> maybe i misread your post a bit. Open terminal try:

```
cat /var/log/dpkg.log | grep remove
```
```
cat /var/log/dpkg.log.1 | grep remove
```

this should tell what packages were removed. Just post the results of the commands.

+1

---

### Post by anystupidname on 2009-07-06
What ^^they^^ said and if that doesn't work and you don't mind losing firefox settings: (make sure FF is closed)
```
mv /home/chris/.mozilla/ /home/chris/borkedmozillaprofile
```
or maybe even:
```
sudo aptitude reinstall sun-java6-plugin sun-java6-bin
```

Have you made sure this is isolated to firefox?

---

### Post by gmakor on 2009-07-12
Thanks everyone! I' ve been unable to read my e-mail for some time, so sorry for the late reply to your help.

Unfortunately (or is that the strength of Ubuntu?), Ubuntu recovered all by itself; to my amazement and delight I was able to connect to all the sites again that I mention in my original post. I have no idea why this is the case. I have not installed or recoverd anything. I do know that the problem was not isolated to firefox; in Flock I was unable to connect to those same sites.

The packages that were removed were (output of the command cat /var/log/dpkg.log | grep remove, as suggested by Jebtrix):
2009-07-05 21:16:30 remove awn-applets-python-extras 0.3.2.1-0ubuntu3 0.3.2.1-0ubuntu3
2009-07-05 21:16:33 remove awn-applets-python-core 0.3.2.1-0ubuntu3 0.3.2.1-0ubuntu3
2009-07-05 21:16:36 remove awn-applets-c-core 0.3.2.1-0ubuntu3 0.3.2.1-0ubuntu3
2009-07-05 21:16:38 remove python-awnlib 0.3.2.1-0ubuntu3 0.3.2.1-0ubuntu3
2009-07-05 21:16:39 remove python-awn-extras 0.3.2.1-0ubuntu3 0.3.2.1-0ubuntu3
2009-07-05 21:16:40 remove avant-window-navigator 0.3.2-0ubuntu2 0.3.2-0ubuntu2
2009-07-05 21:16:42 remove awn-manager 0.3.2-0ubuntu2 0.3.2-0ubuntu2
2009-07-05 21:16:43 remove python-awn 0.3.2-0ubuntu2 0.3.2-0ubuntu2
2009-07-05 21:26:10 startup packages remove
2009-07-05 21:26:10 remove avant-window-navigator-data 0.3.2-0ubuntu2 0.3.2-0ubuntu2
2009-07-05 21:26:11 remove vuze 4.2.0.2-1~getdeb1 4.2.0.2-1~getdeb1
2009-07-05 21:26:11 remove openjdk-6-jre 6b14-1.4.1-0ubuntu7 6b14-1.4.1-0ubuntu7
2009-07-05 21:26:12 remove icedtea-6-jre-cacao 6b14-1.4.1-0ubuntu7 6b14-1.4.1-0ubuntu7
2009-07-05 21:26:12 remove echovnc 1.1-2 1.1-2
2009-07-05 21:26:12 remove libgcj8-jar 4.2.4-5ubuntu1 4.2.4-5ubuntu1
2009-07-05 21:26:12 remove libgcj8-1-awt 4.2.4-5ubuntu1 4.2.4-5ubuntu1
2009-07-05 21:26:12 remove libswt3.2-gtk-gcj 3.2.2-5ubuntu3 3.2.2-5ubuntu3
2009-07-05 21:26:14 remove liblog4j1.2-java-gcj 1.2.15-4 1.2.15-4
2009-07-05 21:26:14 remove liblog4j1.2-java 1.2.15-4 1.2.15-4
2009-07-05 21:26:14 remove libcommons-cli-java 1.1-3 1.1-3
2009-07-05 21:26:14 remove libcommons-lang-java 2.4-1ubuntu1 2.4-1ubuntu1
2009-07-05 21:26:15 remove gij-4.2 4.2.4-5ubuntu1 4.2.4-5ubuntu1
2009-07-05 21:26:15 remove libgcj8-1 4.2.4-5ubuntu1 4.2.4-5ubuntu1
2009-07-05 21:26:15 remove gcj-4.2-base 4.2.4-5ubuntu1 4.2.4-5ubuntu1
2009-07-05 21:26:15 remove libgcj9-jar 4.3.3-5ubuntu4 4.3.3-5ubuntu4
2009-07-05 21:26:16 remove libgcj-bc 4.3.3-1ubuntu1 4.3.3-1ubuntu1
2009-07-05 21:26:16 remove libgcj9-0 4.3.3-5ubuntu4 4.3.3-5ubuntu4
2009-07-05 21:26:16 remove gcj-4.3-base 4.3.3-5ubuntu4 4.3.3-5ubuntu4
2009-07-05 21:26:16 remove hddtemp 0.3-beta15-45 0.3-beta15-45
2009-07-05 21:26:16 remove libawn-extras0 0.3.2.1-0ubuntu3 0.3.2.1-0ubuntu3
2009-07-05 21:26:16 remove libawn0 0.3.2-0ubuntu2 0.3.2-0ubuntu2
2009-07-05 21:26:16 remove libwww-search-perl 2.46-1 2.46-1
2009-07-05 21:26:17 remove libnet-google-perl 1.0.1-1 1.0.1-1
2009-07-05 21:26:17 remove libsoap-lite-perl 0.710.08-2 0.710.08-2
2009-07-05 21:26:17 remove libmime-tools-perl 5.427-2 5.427-2
2009-07-05 21:26:17 remove libconvert-binhex-perl 1.119+pristine-3 1.119+pristine-3
2009-07-05 21:26:17 remove libmime-lite-perl 3.023-1 3.023-1
2009-07-05 21:26:17 remove libemail-date-format-perl 1.002-1 1.002-1
2009-07-05 21:26:17 remove libfcgi-perl 0.67-3 0.67-3
2009-07-05 21:26:17 remove libgcj-common 1:4.3.3-1ubuntu1 1:4.3.3-1ubuntu1
2009-07-05 21:26:17 remove libggadget-gtk-1.0-0 0.10.5-0.1ubuntu1 0.10.5-0.1ubuntu1
2009-07-05 21:26:18 remove libio-socket-ssl-perl 1.18-1 1.18-1
2009-07-05 21:26:18 remove libjcode-pm-perl 2.06-1 2.06-1
2009-07-05 21:26:18 remove libmime-types-perl 1.26-1 1.26-1
2009-07-05 21:26:18 remove libxul0d 1.8.1.16+nobinonly-0ubuntu1 1.8.1.16+nobinonly-0ubuntu1
2009-07-05 21:26:18 remove libmozjs0d 1.8.1.16+nobinonly-0ubuntu1 1.8.1.16+nobinonly-0ubuntu1
2009-07-05 21:26:18 remove libnet-libidn-perl 0.07-1build1 0.07-1build1
2009-07-05 21:26:18 remove libnet-ssleay-perl 1.35-2ubuntu1 1.35-2ubuntu1
2009-07-05 21:26:19 remove libossp-uuid-perl 1.6.2-0ubuntu1 1.6.2-0ubuntu1
2009-07-05 21:26:19 remove libossp-uuid15 1.6.2-0ubuntu1 1.6.2-0ubuntu1
2009-07-05 21:26:19 remove libswt-cairo-gtk-3.4-jni 3.4-2ubuntu3 3.4-2ubuntu3
2009-07-05 21:26:19 remove libswt-gnome-gtk-3.4-jni 3.4-2ubuntu3 3.4-2ubuntu3
2009-07-05 21:26:19 remove libswt-gtk-3.4-java 3.4-2ubuntu3 3.4-2ubuntu3
2009-07-05 21:26:19 remove libswt-gtk-3.4-jni 3.4-2ubuntu3 3.4-2ubuntu3
2009-07-05 21:26:19 remove libswt-mozilla-gtk-3.4-jni 3.4-2ubuntu3 3.4-2ubuntu3
2009-07-05 21:26:19 remove libswt3.2-gtk-java 3.2.2-5ubuntu3 3.2.2-5ubuntu3
2009-07-05 21:26:19 remove libswt3.2-gtk-jni 3.2.2-5ubuntu3 3.2.2-5ubuntu3
2009-07-05 21:26:19 remove python-tunepimp 0.5.3-7ubuntu3 0.5.3-7ubuntu3
2009-07-05 21:26:20 remove libtunepimp5 0.5.3-7ubuntu3 0.5.3-7ubuntu3
2009-07-05 21:26:20 remove libuser-perl 1.6-2 1.6-2
2009-07-05 21:26:20 remove libxul-common 1.8.1.16+nobinonly-0ubuntu1 1.8.1.16+nobinonly-0ubuntu1
2009-07-05 21:26:20 remove peazip 2.6.2.-2 2.6.2.-2
2009-07-05 21:26:21 remove python-alsaaudio 0.2-1ubuntu2 0.2-1ubuntu2
2009-07-05 21:26:21 remove python-dateutil 1.4.1-2 1.4.1-2
2009-07-05 21:26:21 remove python-soappy 0.12.0-4 0.12.0-4
2009-07-05 21:26:21 remove python-fpconst 0.7.2-4 0.7.2-4
2009-07-05 21:26:22 remove python-musicbrainz2 0.6.0-2 0.6.0-2
2009-07-05 21:26:22 remove python-numeric 24.2-9ubuntu1 24.2-9ubuntu1
2009-07-05 21:26:22 remove python-pymad 0.5.4-3.2build2 0.5.4-3.2build2
2009-07-05 21:26:22 remove python-sqlalchemy 0.4.8-1 0.4.8-1
2009-07-05 21:26:23 remove python-xlib 0.14-2 0.14-2
2009-07-05 21:26:23 remove sqlite3 3.6.10-1ubuntu0.2 3.6.10-1ubuntu0.2
2009-07-05 21:26:23 remove truecrypt 6.2a-0 6.2a-0
2009-07-05 21:26:23 remove ttf-bengali-fonts 1:0.5.4ubuntu2 1:0.5.4ubuntu2
2009-07-05 21:26:37 remove ttf-kannada-fonts 1:0.5.4ubuntu2 1:0.5.4ubuntu2
2009-07-05 21:26:51 remove ttf-oriya-fonts 1:0.5.4ubuntu2 1:0.5.4ubuntu2
2009-07-05 21:27:03 remove ttf-telugu-fonts 1:0.5.4ubuntu2 1:0.5.4ubuntu2
2009-07-05 21:27:13 remove ttf-wqy-zenhei 0.8.34-cvs20081027-0ubuntu1 0.8.34-cvs20081027-0ubuntu1
2009-07-05 21:27:25 remove xorg-driver-sis671 1:0.9 1:0.9
2009-07-05 21:27:25 remove ca-certificates-java 20081028 20081028
2009-07-05 21:27:25 remove openjdk-6-jre-headless 6b14-1.4.1-0ubuntu7 6b14-1.4.1-0ubuntu7
2009-07-05 21:27:27 remove openjdk-6-jre-lib 6b14-1.4.1-0ubuntu7 6b14-1.4.1-0ubuntu7
2009-07-05 21:27:27 remove fortune-mod 1:1.99.1-3.1ubuntu3 1:1.99.1-3.1ubuntu3
2009-07-05 21:27:27 remove fortunes-min 1:1.99.1-3.1ubuntu3 1:1.99.1-3.1ubuntu3
2009-07-05 21:27:27 remove rhino 1.7R1-2 1.7R1-2
2009-07-05 21:27:27 remove librecode0 3.6-15 3.6-15
2009-07-05 21:27:27 remove tzdata-java 2009j-0ubuntu0.9.04 2009j-0ubuntu0.9.04
2009-07-05 21:27:28 remove libaccess-bridge-java 1.24.0-0ubuntu2 1.24.0-0ubuntu2

Output of the command cat /var/log/dpkg.log.1 | grep remove:
2009-04-20 14:09:38 remove linux-headers-generic 2.6.28.11.15 2.6.28.11.15
2009-04-20 14:09:38 remove linux-headers-2.6.28-11-generic 2.6.28-11.42 2.6.28-11.42
2009-04-20 14:09:39 remove linux-headers-2.6.28-11 2.6.28-11.42 2.6.28-11.42
2009-06-24 14:27:08 startup packages remove
2009-06-24 14:27:08 remove mountmanager 0.2.6-0ubuntu2 0.2.6-0ubuntu2
2009-06-25 15:51:59 remove listen 0.5-6ubuntu1 0.5-6ubuntu1
2009-06-26 16:43:41 startup packages remove
2009-06-26 16:43:54 remove google-gadgets-gtk 0.10.5-0.1ubuntu1 0.10.5-0.1ubuntu1
2009-06-26 16:43:54 remove google-gadgets-xul 0.10.5-0.1ubuntu1 0.10.5-0.1ubuntu1
2009-06-26 16:43:54 remove google-gadgets-gst 0.10.5-0.1ubuntu1 0.10.5-0.1ubuntu1
2009-06-26 16:43:58 remove google-gadgets-common 0.10.5-0.1ubuntu1 0.10.5-0.1ubuntu1
2009-06-27 14:01:37 remove gdesklets 0.36-5ubuntu1 0.36-5ubuntu1
2009-06-27 14:01:38 remove gdesklets-data 0.35.6-3 0.35.6-3
2009-06-29 00:17:16 startup packages remove
2009-06-29 00:17:16 remove azureus 3.1.1.0-4ubuntu1 3.1.1.0-4ubuntu1

As far as I am aware, I have not reinstalled any of these manually before the system resumed as normal.

Anyway, all is well now. I appreciate the help offered; thank you all!

All the best,
Guido

---

