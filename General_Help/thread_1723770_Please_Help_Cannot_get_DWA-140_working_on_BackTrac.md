---
title: "Please Help: Cannot get DWA-140 working on BackTrack 3"
date: 2011-04-07
forum: General Help
---

### Post by Vincenso27 on 2011-04-07
I have been trying for 3 days to get my DWA-140 usb wifi adapter working with Backtrack 3 (Final).  I am a total Linux noob.

I have read at least 30 threads on and related to this topic.  I have tried countless methods and tricks and different ways of installing this thing.  All fails.

I tried downloading the Linux ralink drivers.  I did all of the preliminary edits to config.mk.  Everytime I run the "make" command, the last two lines that get spit out are:

make: *** /lib/modules/2.6.21.5/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2


I also tried ndiswrapper, failing multiple times until finally I was able to say that it installed the rt2870 drivers successfully.

I then reformatted my Backtrack 3 usb stick to start with a fresh copy of backtrack 3, and only did the ndiswrapper driver install (successfully) to ensure that there was no junk leftover from all of my other messing around.

Still nothing from the DWA-140.  No lights on the stick.  No connection. No additional recognition of wireless devices.

What am I doing wrong?  What should I do?  

Thanks for any help or input

---

### Post by gwnoble on 2011-07-01
Hi,

Did you work out your problem?
I'm having exactly the same problem when trying to compile the driver. Bugger me if I can find a solution to it.
Any help would be appreciated.

---

### Post by linuxuser12345 on 2011-07-01
Have you tried NDISWRAPPER?

---

