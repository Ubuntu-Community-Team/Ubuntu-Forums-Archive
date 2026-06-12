---
title: "GoogleEarth starts only with sudo! Fatal error in driConfigOptions, ..caught signal 6"
date: 2010-07-20
forum: General Help
---

### Post by AstroPhysik on 2010-07-20
[SIZE=2][B]Hello,
[/B]**GoogleEarth starts only with sudo!**
**Fatal error in driConfigOptions, google earth has caught signal 6**
[/SIZE][SIZE=2]
I've installed googleearth yesterday, all was running fine. Until i restarted the SW, then a popup window came:  googleearth cannot write in a  config file.  Trying to write in  /home/user directory..
The terminal gives the  error message below.

i tried a bit of:
[/SIZE] 
[LIST]
[*][SIZE=2][https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)[/SIZE]
[*][SIZE=2][http://wiki.ubuntuusers.de/Google_Earth](http://wiki.ubuntuusers.de/Google_Earth)[/SIZE]
[/LIST]
 [SIZE=2]it seemed to be the root problem. but 
sudo rm -Rf .config/Google .googleearth[/SIZE][SIZE=2]did not help.

How can i avoid to run the SW without: **sudo googleearth**  ?
(I'm really surpriesed to give google root status on my computer!:()

Thanx for any help!
Astrophysik


My specs:
**ia32-libs (universe),** **lib32nss-mdns (universe)** for 64bit are installed.
dpkg -l | grep google
ii  googleearth-package     0.5.4.1~0ubuntu1     utility to automatically build a Debian pack
ii  libgdata-google1.2-1    2.26.1-0ubuntu2      Client library for accessing Google POA thro
[/SIZE]  [SIZE=2]ubuntu 9.04 AMD 64Bit
i have a HP dv5-Laptop (AMD 64Bit) Turion-ZM82 ultra processor.


terminal error message:
> Fatal error in __driConfigOptions line 1, column 0: unknown encoding.
Google Earth has caught signal 6. 

We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written
 to this text file:

    /home/benutzer/.googleearth/crashlogs/crashlog-4c449a82.txt
> Major Version 5
Minor Version 2
Build Number 0001
Build Date Jun 10 2010
Build Time 16:15:55
OS Type 3
OS Major Version 2
OS Minor Version 6
OS Build Version 28
OS Patch Version 0
Crash Signal 6
Crash Time 1279564723
Up Time 0,658792

Stacktrace from glibc:
./libgoogleearth_free.so[0xf76ca30b]
[0xf7723400]

Please include this file if you submit a bug report to Google.[/SIZE]

---

### Post by eliotv10 on 2010-07-20
Hello,

I am not sure about it,but a possible solution would be:

1)Right click at "applications"
2)Select "Internet",then click at "google earth"
3)Delete the launcher.
4)Prees "new item"
5)Type:Application in terminal
Name:Google Earth
Command:sudo googleearth
Comment:Explore the virtual earth(or watever you like)

---

### Post by Vaphell on 2010-07-20
this happens because some crucial file is created as owned by root for some reason, i don't remember exactly why.

check if anything is owned by root in your .googleearth and .config/Google
```
ls -la .googleearth
ls -la .config/Google
```

 and where GoogleEarthPlus.conf located in .config/Google points for cache.


PS. suggestion from post above, while working, is a dirty workaround and reinforces bad habits :) i encourage you to fix the problem entirely, you'll learn more and will know your way around better.

PS2. i think i remember why this happens. Installing requires root privileges so when installation is complete and you tell the isntaller to run GE immediately, app is launched with root privileges of installer, thus any file created is owned by root and you can't change it later if you run GE as ordinary user.

---

### Post by AstroPhysik on 2010-07-20
Hello!   Thank you !

i searched for the .config files and used chmod and chown to switch from root to user.
But without success. sudo was always necessary.

So i deinstalled it, and re-installed googleearth with the HOWTO: Alternate Installation:
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)
and did not press the run Button! ;)   i guess that was my mistake at the first installation.

But it did not work too. So i installed the Googleearth.bin  as user. (without:  sudo ./Googleearth.bin )
but it  always wants the sudo command for operating normally, otherwise the signal 6 error occures???

greetz A.P.

---

### Post by Vaphell on 2010-07-20
you tell strange stories indeed :)
paste ls output here, and what paths are set in config file - if it points to /root (home dir of root) - change it.

```
grep KMLPath ~/.config/Google/GoogleEarthPlus.conf
grep CachePath ~/.config/Google/GoogleEarthPlus.conf
```

(in case you don't know, you can highlight text and paste it with middleclick anywhere, including terminal, so you don't have to type all that stuff by hand)



i remember that i had such problem when i installed GE in 8.04. GoogleEarth actually wanted to write there.
check if there is some googleearth config created in /root that can mess things up.

```
sudo ls -la /root
sudo ls -la /root/.config

```

---

### Post by AstroPhysik on 2010-07-20
hahaha   indeed,
(yeah i can copy & paste );)

thank you very much for helping me! :)
greetz AP.

OK here's the output:

*grep KMLPath ~/.config/Google/GoogleEarthPlus.conf*
KMLPath=/home/user/.googleearth

*grep CachePath ~/.config/Google/GoogleEarthPlus.conf*
CachePath=/home/user/.googleearth/Cache

*sudo ls -la /root*
insgesamt 88
drwx------ 16 root root 4096 2010-07-19 17:19 .
drwxr-xr-x 22 root root 4096 2010-06-08 13:49 ..
**drwx------  4 root root 4096 2010-07-20 19:28 .googleearth**         [COLOR=Red]// hmm do i have to delete this?[/COLOR]
...

sudo ls -la /root/.googleearth
insgesamt 100
drwx------  4 root root  4096 2010-07-20 19:28 .
drwx------ 16 root root  4096 2010-07-19 17:19 ..
[B]drwx------  4 root root  4096 2010-07-19 14:55 Cache
lrwxrwxrwx  1 root root    10 2010-07-20 19:28 instance-running-lock -> /proc/9925
-rw-r--r--  1 root root 25754 2010-07-19 19:20 myplaces.backup.kml
-rw-r--r--  1 root root 25897 2010-07-19 19:20 myplaces.kml
-rw-r--r--  1 root root 25897 2010-07-19 19:20 myplaces.kml.tmp
drwx------  8 root root  4096 2010-07-20 19:28 Temp
[/B]

[I]sudo ls -la /root/.config
[/I]ls: Zugriff auf /root/.config nicht möglich: No such file or directory

*ls -la .googleearth/*
insgesamt 24
drwx------  4 user user  4096 2010-07-20 21:23 .
drwxr-xr-x 87 user user 12288 2010-07-20 21:08 ..
drwxr-xr-x  2 user user  4096 2010-07-20 19:50 Cache
drwx------  2 user user  4096 2010-07-20 21:23 crashlogs
lrwxrwxrwx  1 user user    11 2010-07-20 21:23 instance-running-lock -> /proc/14392
[I]
 ls -la .config/Google/[/I]
insgesamt 12
drwxrwxrwx  2 user user 4096 2010-07-20 19:23 .
drwxrwxrwx 18 user user 4096 2010-07-20 19:23 ..
-rwxrwxrwx  1 user user 1547 2010-07-20 21:23 GoogleEarthPlus.conf

*ls -la .googleearth/Cache*
insgesamt 12
drwxr-xr-x 2 user user      4096 2010-07-20 19:50 .
drwx------ 4 user user      4096 2010-07-20 21:23 ..
-rw------- 1 user user 134252032 2010-07-20 21:23 dbCache.dat
-rw------- 1 user user         0 2010-07-20 21:23 dbCache.dat.index
-rw-r--r-- 1 user user         0 2010-07-20 19:50 dbroot_cache

---

### Post by AstroPhysik on 2010-07-20
hmmm,
i deleted it with:
sudo rm -R /root/.googleearth

but it did not help..

greetz AP.

---

### Post by ratcheer on 2010-07-20
I have a similar problem with Google Earth on Lucid, but it runs ok. It just won't save anything because of root permissions needed.

I would think that there would be plenty of issues / bugs at Google, and they would be able to tell us how to install it correctly, so that it will work. I haven't taken the time to investigate, though. If I need to use GE, I can just do it on Windows, where it works almost perfectly.

Tim

---

### Post by Vaphell on 2010-07-20
hm, i don't see any permission issues, wtf -_-

GE 5.2?
a lot of people claim that they have problems
[http://www.google.com/support/forum/p/earth/thread?tid=5da393653cabeeb0&hl=en](http://www.google.com/support/forum/p/earth/thread?tid=5da393653cabeeb0&hl=en)

Google employee suggests:
> cd google-earth/
wget [http://librarian.launchpad.net/7037027/libGL.so.1](http://librarian.launchpad.net/7037027/libGL.so.1) -O libGL.so.1
and reportedly helped some people

by google-earth he apparently means /opt/google-earth or /usr/lib/google-earth/ - whatever the install dir is
sudo probably required

---

### Post by AstroPhysik on 2010-07-21
thank you Vaphell for your help,

well, lets see whats coming out.  (GE is so cool for planning holidays, you can look how far is the hotel to the sea ;) )

Hmm.. has anyone old binaries?  e.g. 5.0 or 5.1 to download?
maybe there is not the need for sudo to run the Appl.

greetz AP.

---

### Post by hamidoo on 2010-07-25
Thx man!
this works for me!
It was working on my radeon card, but when i switch to the intel i had this issue.
Now it's SOLVED
cheers

> **Vaphell said:**
> hm, i don't see any permission issues, wtf -_-

GE 5.2?
a lot of people claim that they have problems
[http://www.google.com/support/forum/p/earth/thread?tid=5da393653cabeeb0&hl=en](http://www.google.com/support/forum/p/earth/thread?tid=5da393653cabeeb0&hl=en)

Google employee suggests:

and reportedly helped some people

by google-earth he apparently means /opt/google-earth or /usr/lib/google-earth/ - whatever the install dir is
sudo probably required

---

