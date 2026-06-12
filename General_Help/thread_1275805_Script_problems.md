---
title: "Script problems"
date: 2009-09-26
forum: General Help
---

### Post by J V on 2009-09-26
I have numerous scripts that just aren't working, after octruple checking the address and running a few chmods +x's, they still won't work...

```
#! /bin/bash
rm -rf ~/.mozilla/firefox/*/Cache/* 
rm -rf ~/.Trash/*
```This doesn't do anything at all for example...

As a little side question, what are all the files with ~ on their ends for? (I know what they do but why are they there?) Its getting hard to open a file with gedit...

---

### Post by credobyte on 2009-09-26
Does your Trash really is a hidden folder in home directory ( mine is under /usr ) ?
[B][COLOR=Green]
script.sh[/COLOR][/B]
```
rm -rf ~/.mozilla/firefox/*/Cache/* 
rm -rf ~/.Trash/*
```

```
sudo chmod +x script.sh
./script.sh
```~ ( tilde ), in most cases, means that it's a backup file - you can turn it off in Gedit preferences.

---

### Post by J V on 2009-09-26
Ok, after double checking, my trash isn't in my ~ or my /usr...

I do know the script doesn't work however, because the mozilla cache is still there...

Thanks for the gedit tip, got it...

---

### Post by credobyte on 2009-09-26
```
ls -al ~/.mozilla/firefox/*/*/

```Can you shows us the output ?

---

### Post by wojox on 2009-09-26
```
#!/bin/bash
CURKERNEL=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
LINUXPKG="linux-(image|headers|ubuntu-modules|restricted-modules)"
METALINUXPKG="linux-(image|headers|restricted-modules)-(generic|i386|server|common|rt|xen)"
OLDKERNELS=$(dpkg -l|awk '{print $2}'|grep -E $LINUXPKG |grep -vE $METALINUXPKG|grep -v $CURKERNEL)
echo -e "Local purge....#####################"
sudo localepurge
echo -e "Cleaning packages...#######################"
sudo apt-get autoremove
echo -e "Cleaning apt cache...#######################"
sudo apt-get autoclean
echo -e "Cleaning apt cache...#######################"
sudo apt-get clean
echo -e "Removing old kernels...#########################"
sudo apt-get purge $OLDKERNELS
echo -e "Emptying all the trash...##########################"
rm -rf /home/*/.local/share/Trash/*/** &> /dev/null
rm -rf /root/.local/share/Trash/*/** &> /dev/null
echo -e "Script Finished!"
```

---

### Post by J V on 2009-09-26
very large result...

Removed my username from it (replaced with MyName)
```
-rw-r--r-- 1 MyName MyName     2644 2009-09-26 14:55 /home/MyName/.mozilla/firefox/kf8gh63r.default/blocklist.xml
-rw-r--r-- 1 MyName MyName    28240 2009-09-23 23:05 /home/MyName/.mozilla/firefox/kf8gh63r.default/bookmarks.html
-rw------- 1 MyName MyName    65536 2009-09-26 14:32 /home/MyName/.mozilla/firefox/kf8gh63r.default/cert8.db
-rw------- 1 MyName MyName      164 2009-09-23 23:50 /home/MyName/.mozilla/firefox/kf8gh63r.default/compatibility.ini
-rw-r--r-- 1 MyName MyName   153522 2009-09-25 12:56 /home/MyName/.mozilla/firefox/kf8gh63r.default/compreg.dat
-rw-r--r-- 1 MyName MyName     7168 2009-09-23 23:06 /home/MyName/.mozilla/firefox/kf8gh63r.default/content-prefs.sqlite
-rw-r--r-- 1 MyName MyName    43008 2009-09-26 15:33 /home/MyName/.mozilla/firefox/kf8gh63r.default/cookies.sqlite
-rw-r--r-- 1 MyName MyName     8192 2009-09-25 18:29 /home/MyName/.mozilla/firefox/kf8gh63r.default/downloads.sqlite
-rw-r--r-- 1 MyName MyName      472 2009-09-25 12:56 /home/MyName/.mozilla/firefox/kf8gh63r.default/extensions.cache
-rw-r--r-- 1 MyName MyName      439 2009-09-25 12:56 /home/MyName/.mozilla/firefox/kf8gh63r.default/extensions.ini
-rw-r--r-- 1 MyName MyName     5700 2009-09-25 12:56 /home/MyName/.mozilla/firefox/kf8gh63r.default/extensions.rdf
-rw-r--r-- 1 MyName MyName    16384 2009-09-26 15:32 /home/MyName/.mozilla/firefox/kf8gh63r.default/formhistory.sqlite
-rw------- 1 MyName MyName    16384 2009-09-25 23:29 /home/MyName/.mozilla/firefox/kf8gh63r.default/key3.db
-rw-r--r-- 1 MyName MyName     6844 2009-09-26 14:46 /home/MyName/.mozilla/firefox/kf8gh63r.default/localstore.rdf
lrwxrwxrwx 1 MyName MyName       15 2009-09-26 15:30 /home/MyName/.mozilla/firefox/kf8gh63r.default/lock -> 127.0.1.1:+6084
-rw-r--r-- 1 MyName MyName     2385 2009-09-23 23:06 /home/MyName/.mozilla/firefox/kf8gh63r.default/mimeTypes.rdf
-rw-r--r-- 1 MyName MyName     2048 2009-09-23 23:06 /home/MyName/.mozilla/firefox/kf8gh63r.default/permissions.sqlite
-rw-r--r-- 1 MyName MyName   786432 2009-09-26 15:33 /home/MyName/.mozilla/firefox/kf8gh63r.default/places.sqlite
-rw-r--r-- 1 MyName MyName    82592 2009-09-26 15:33 /home/MyName/.mozilla/firefox/kf8gh63r.default/places.sqlite-journal
-rw------- 1 MyName MyName     7084 2009-09-26 15:30 /home/MyName/.mozilla/firefox/kf8gh63r.default/pluginreg.dat
-rw-r--r-- 1 MyName MyName     2508 2009-09-25 23:29 /home/MyName/.mozilla/firefox/kf8gh63r.default/prefs.js
-rw-r--r-- 1 MyName MyName     4096 2009-09-24 15:31 /home/MyName/.mozilla/firefox/kf8gh63r.default/search.sqlite
-rw------- 1 MyName MyName    16384 2009-09-26 15:30 /home/MyName/.mozilla/firefox/kf8gh63r.default/secmod.db
-rw------- 1 MyName MyName    23179 2009-09-26 15:30 /home/MyName/.mozilla/firefox/kf8gh63r.default/sessionstore.bak
-rw------- 1 MyName MyName    27366 2009-09-26 15:34 /home/MyName/.mozilla/firefox/kf8gh63r.default/sessionstore.js
-rw------- 1 MyName MyName      989 2009-09-24 19:30 /home/MyName/.mozilla/firefox/kf8gh63r.default/signons3.txt
-rw-r--r-- 1 MyName MyName 34922496 2009-09-26 15:33 /home/MyName/.mozilla/firefox/kf8gh63r.default/urlclassifier3.sqlite
-rw-r--r-- 1 MyName MyName      154 2009-09-26 15:30 /home/MyName/.mozilla/firefox/kf8gh63r.default/urlclassifierkey3.txt
-rw-r--r-- 1 MyName MyName     2048 2009-09-24 18:28 /home/MyName/.mozilla/firefox/kf8gh63r.default/webappsstore.sqlite
-rw-r--r-- 1 MyName MyName  2198705 2009-09-25 12:56 /home/MyName/.mozilla/firefox/kf8gh63r.default/XPC.mfasl
-rw-r--r-- 1 MyName MyName   107486 2009-09-25 18:29 /home/MyName/.mozilla/firefox/kf8gh63r.default/xpti.dat
-rw-r--r-- 1 MyName MyName  2509409 2009-09-25 23:23 /home/MyName/.mozilla/firefox/kf8gh63r.default/XUL.mfasl

/home/MyName/.mozilla/firefox/kf8gh63r.default/bookmarkbackups:
total 24
drwx------ 2 MyName MyName 4096 2009-09-25 11:19 .
drwx------ 7 MyName MyName 4096 2009-09-26 15:34 ..
-rw------- 1 MyName MyName 5717 2009-09-23 23:07 bookmarks-2009-09-23.json
-rw------- 1 MyName MyName 4981 2009-09-25 11:19 bookmarks-2009-09-25.json

/home/MyName/.mozilla/firefox/kf8gh63r.default/Cache:
total 1936
drwxr-xr-x 2 MyName MyName   4096 2009-09-26 15:33 .
drwx------ 7 MyName MyName   4096 2009-09-26 15:34 ..
-rw------- 1 MyName MyName 106867 2009-09-26 15:32 0734D5A3d01
-rw------- 1 MyName MyName  20574 2009-09-26 15:30 08317907d01
-rw------- 1 MyName MyName  21530 2009-09-26 15:31 141B2674d01
-rw------- 1 MyName MyName  26195 2009-09-26 15:32 2508F599d01
-rw------- 1 MyName MyName  21530 2009-09-26 15:30 314037D6d01
-rw------- 1 MyName MyName  31355 2009-09-26 15:30 48CA23E4d01
-rw------- 1 MyName MyName 102346 2009-09-26 15:32 59D0858Bd01
-rw------- 1 MyName MyName  72663 2009-09-26 15:33 59D1C6B3d01
-rw------- 1 MyName MyName  91418 2009-09-26 15:33 59D1C6F1d01
-rw------- 1 MyName MyName  35567 2009-09-26 15:30 7A8FEF1Dd01
-rw------- 1 MyName MyName  36559 2009-09-26 15:30 8320036Ad01
-rw------- 1 MyName MyName  64751 2009-09-26 15:32 9AF52865d01
-rw------- 1 MyName MyName  21512 2009-09-26 15:31 A6FF2BD6d01
-rw------- 1 MyName MyName  27540 2009-09-26 15:32 BA488FFFd01
-rw------- 1 MyName MyName 334407 2009-09-26 15:33 _CACHE_001_
-rw------- 1 MyName MyName 166346 2009-09-26 15:33 _CACHE_002_
-rw------- 1 MyName MyName 569547 2009-09-26 15:33 _CACHE_003_
-rw------- 1 MyName MyName    276 2009-09-26 15:30 _CACHE_MAP_
-rw------- 1 MyName MyName  54982 2009-09-26 15:32 DBF40E3Fd01
-rw------- 1 MyName MyName  28398 2009-09-26 15:30 E0F0BCFFd01
-rw------- 1 MyName MyName  64403 2009-09-26 15:31 FC0C1EB5d01

/home/MyName/.mozilla/firefox/kf8gh63r.default/chrome:
total 16
drwxr-xr-x 2 MyName MyName 4096 2009-09-23 23:05 .
drwx------ 7 MyName MyName 4096 2009-09-26 15:34 ..
-rw-r--r-- 1 MyName MyName 1078 2009-09-23 23:05 userChrome-example.css
-rw-r--r-- 1 MyName MyName  663 2009-09-23 23:05 userContent-example.css

/home/MyName/.mozilla/firefox/kf8gh63r.default/extensions:
total 8
drwxr-xr-x 2 MyName MyName 4096 2009-09-23 23:06 .
drwx------ 7 MyName MyName 4096 2009-09-26 15:34 ..

/home/MyName/.mozilla/firefox/kf8gh63r.default/searchplugins:
total 20
drwxr-xr-x 2 MyName MyName 4096 2009-09-24 14:59 .
drwx------ 7 MyName MyName 4096 2009-09-26 15:34 ..
-rw-r--r-- 1 MyName MyName 4857 2009-09-24 14:59 isohunt---bt-search.xml
-rw-r--r-- 1 MyName MyName 1713 2009-09-24 14:59 youtube-video-search.xml
```

---

### Post by J V on 2009-09-27
Is wojox' code correct? (The oldkernels value seems dangerous)

---

### Post by wojox on 2009-09-27
It works on my machine. I just threw it up there so you could see where Trash is. If you run my script you need to download localepurge. Like I said though you can pick and choose what commands to run and modify it as you want. The old kernels just cleans up anything older than your current kernel.

---

### Post by J V on 2009-09-27
Ok, cool... I shouldent worry about this destroying my /host? :P

Edit: The script locked apt-get and isn't actually doing anything...

Need a fix or I cant open synaptic...

---

