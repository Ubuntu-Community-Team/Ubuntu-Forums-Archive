---
title: "system slowed down after i installed"
date: 2010-05-24
forum: General Help
---

### Post by crozar on 2010-05-24
Greetings , 

i have a problem , my ubuntu was running very fast and everything was good until i tried to burn a DVD , i have used brasero and the video file that i was trying to burn was a .avi and brasero will do the convert then burn in a DVD for me but however , since i tried to press burn it gave me an error that i am missing libraries and applications and please install them manually such as mplex ( Gstreamer plugin ) 
and dvdauthor and vcdimager
i went in synaptic , and typed brasero , i right clicked it and reinstalled it , after that i found out that in right click u can see recommended libraries with it and stuff like that so i saw DVD author and gstreamer plugins good and bad and all that  ,  i went in tried to reinstall each , however .... didnt work so i went to google and found something in[ bugs launchpad]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/270976") which said i have to install > configure: *** Plug-ins with dependencies that will NOT be built:
 mpeg2enc
 mplex

This results in brasero not being able to burn Video.

The issue can be fixed by adding libmjpegtools-dev (>= 1.9.0) to the build-depends.

after i installed libmjpegtools-dev it have installed other dependencies with it , now my system is running slow :S , maybe a i conflicted or did something because it removed things i remember and installed things from libmjpegtools . please help me how to revert this change is theyr like a system restore .

---

### Post by dino99 on 2010-05-24
when things goes wrong you might think to look at .xsession-errors (unhide it into /home with menu) and logs (system admin log viewer) about errors.

first:
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

have you a swap partition ? (fdisk -l)

---

### Post by crozar on 2010-05-26
ive checked , its randomly stating other things and not the thing that happened that slowed down my pc , i am really sure that it has to do with what was removed , i have tried to fix brasero to burn and i went into the search of google and with complication i tried to squeeze right in to fix it by installing that libmjpegtools-dev and i pressed ok quickly it have done something , it removed somethings from my system and installed other things which are old maybe , i dunno but maybe the grouping of those plugins or something is making my system run slow ?  now brasero still doesnt work when i tried to burn this eror comes
Please install the following manually and try again:
mplex (GStreamer plugin).

---

### Post by macey on 2010-05-29
[QUOTE=doesnt work when i tried to burn this eror comes
Please install the following manually and try again:
mplex (GStreamer plugin).[/QUOTE]

I have the same problem, will watch this thread for a fix!

---

### Post by supadupadad1 on 2010-08-05
I have just had the same exact problem with brasero! Was searching the web for a fix and came across this thread. Hopefully someone will answer it soon.

---

### Post by supadupadad1 on 2010-08-05
ok guys. I just fixed my problem! The answer is on this page. 
      [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/270976](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/270976)

 Good lucks guys

---

