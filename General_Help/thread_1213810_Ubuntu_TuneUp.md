---
title: "Ubuntu TuneUp"
date: 2009-07-15
forum: General Help
---

### Post by Frantique on 2009-07-15
Hello all!
I just released  a small post install script for Ubuntu systems.
Here is the description:

**Ubuntu TuneUp** - v. 0.0.1
Coded by: *Frantique* (undernetangel@gmail.com)
*A small Bash script to make quick tuneup on a freshly installed Ubuntu system.*
---
**Usage:** sudo tuneup.sh OPTION
**Options:**
**-c **: By default sets concurrency to shell.
**-s** : Set swappiness to lower value. (Use it just if you have more than 1Gb of RAM)
**-i** : Disable IPv6.
**-g** : Install some extra packages like Flash plugin, extra fonts, Java, tweak-ubuntu, etc.
**-f** : Tune up Flash video playback. (Just if GPU can be used.)
**-a** : Execute all above.
**-h** : This help screen.
**-v** : Display version.

**How to install:**
1. Download from [http://artinvoice.hu/tuneup.tar.gz](http://artinvoice.hu/tuneup.tar.gz)
2. Unpack with: tar xvzf tuneup.tar.gz 
3. Start a Terminal and go to tuneup/ directory
4. Run the command: sudo ./tuneup.sh -a

Enjoy!

**Note:**
*The IPv6 disable has no effect in Jaunty. It makes no damage to the system if used, just it makes nothing. :) I hope that in the future I will find a good solution for this.*

---

### Post by jpeddicord on 2009-07-19
Nice script, though as it does not qualify as a tutorial I'm moving it to General Help.

One thing to note, though: "2&>1" is not the correct syntax for redirecting stderr to the first output (/dev/null). You want "2>&1." :)

---

### Post by Frantique on 2009-07-20
> **jacobmp92 said:**
> Nice script, though as it does not qualify as a tutorial I'm moving it to General Help.

One thing to note, though: "2&>1" is not the correct syntax for redirecting stderr to the first output (/dev/null). You want "2>&1." :)

Ouch, corrected, thanks! :D

---

### Post by Arup on 2009-07-20
Have you tried this on Jaunty btw?

---

### Post by Frantique on 2009-07-20
> **Arup said:**
> Have you tried this on Jaunty btw?

Yes, actually I made it on Jaunty... Why, is there any problem?

---

### Post by Arup on 2009-07-20
> **Frantique said:**
> Yes, actually I made it on Jaunty... Why, is there any problem?

Will try it out now and get back to you. How did you manage to disable IPV6, it needs a newer 2.6.30 kernel for that if I am not mistaken.

---

### Post by Frantique on 2009-07-20
Yes, that is an issue with Jaunty. Even if sysctl shows thet ipv6 is disabled, the kernel ignores it. I hope that it will be fixed soon. Meanwhile I am searching for a better, global solution...

---

### Post by Arup on 2009-07-20
> **Frantique said:**
> Yes, that is an issue with Jaunty. Even if sysctl shows thet ipv6 is disabled, the kernel ignores it. I hope that it will be fixed soon. Meanwhile I am searching for a better, global solution...

Sadly only solution is kernel upgrade and thats not truly practical.Also consider adding a revert back script.

---

### Post by Frantique on 2009-07-20
Actually you can revert if you change the values in the config file.

---

### Post by Frantique on 2009-07-20
**HELP NEEDED!**

If anyone can help me with localization to other languages, please contact me in email: undernetangel {at} gmail [dot] com.
Thank you in advance!

---

### Post by rocket16 on 2009-07-20
<MARQUEE]Great! Nice method! Thanks. </MARQUEE>

---

### Post by Frantique on 2009-07-20
**NEW VERSION RELEASED!** 
From now on you can update from within the script with -u parameter.

**Ubuntu TuneUp - v. 0.0.2**
Coded by: Frantique (undernetangel@gmail.com)
A small Bash script to make quick tuneup on a freshly installed Ubuntu system.
---
Usage: sudo tuneup.sh OPTION
**Options:**
-c : By default sets concurrency to shell.
-s : Set swappiness to lower value. (Use it just if you have more than 1Gb of RAM)
-i : Disable IPv6.
-g : Install some extra packages like Flash plugin, extra fonts, Java, tweak-ubuntu, etc.
-f : Tune up Flash video playback. (Just if GPU can be used.)
-a : Execute all above.
***-u : Checks for script updates and updating if needed.***
-h : This help screen.
-v : Display version.

---

### Post by Frantique on 2009-09-03
Hi people!
Version 0.0.4 is here! Check it out! The download moved to: [http://artinvoice.hu/tuneup/tuneup.tar.gz](http://artinvoice.hu/tuneup/tuneup.tar.gz) !
Enjoy!

---

### Post by Frantique on 2013-02-04
Hello all, Ubuntu TuneUp version 0.0.7 is out. 

Features:

Ubuntu TuneUp - v. 0.0.7
Coded by: Frantique (undernetangel@gmail.com)
A small Bash script to make quick tuneup on a freshly installed Ubuntu system.
---
Usage: tuneup.sh OPTION
Options:
-c : By default sets concurrency to shell.
-s : Set swappiness to lower value. (Use it just if you have more than 1Gb of RAM)
-i : Disable IPv6.
-g : Install some extra packages like codecs, tweak-ubuntu, Adobe flash plugin etc.
-f : Tune up Flash video playback. (Just if GPU can be used.)
-d : Tweak Gnome to be faster. (Log out and back again to apply changes.)
-j : Installing Oracle Java version 7 from webupd8team repository.
-a : Execute all above.
----
-t : Adding some parameters to fstab.
-p : Installing and enabling prelink.
-e : Fixing the Skype's "Fatal: QWidget: Must construct a QApplication before a QPaintDevice" error.
-u : Checks for script updates and updating if needed.
-h : This help screen.
-v : Display version.

You can get it at: [http://artinvoice.hu/tuneup/tuneup.tar.gz](http://artinvoice.hu/tuneup/tuneup.tar.gz)

---

