---
title: "Compcache broken in 10.10 ?"
date: 2011-01-24
forum: General Help
---

### Post by blasted001 on 2011-01-24
Possibly related this bug: [http://ubuntuforums.org/showthread.php?p=10393531#post10393531](http://ubuntuforums.org/showthread.php?p=10393531#post10393531) , but I am using 32 bit ubuntu exclusively, so I felt a new thread title was appropriate. 

sudo swapon -s 

[lists nothing]

sudo swapon /dev/ramzswap0:
swapon: /dev/ramzswap0: read swap header failed: Invalid argument

NightwishFan's workaround:
sudo /usr/lib/initramfs-tools/bin/rzscontrol /dev/ramzswap0 --init && sudo swapon -p 100 /dev/ramzswap0

This works, but I'm not sure how to  automatically and securely run a "sudo" command on every startup.

I've tested compcache on 3 laptops (Dell, HP, Toshiba) and compcache does not work on any of them.  I've tried using the -u and -c options with update-initramfs. Tried specifying "xx%", "xx %", and  "xxx M" in the config file. 

Used 32 bit alt installer on all of the boxes. I haven't tested with 10.04 or earlier yet. A thirdhand report from the above thread implies it may not be broken for everyone, and the bug mentioned in the above thread appears to have been fixed, so...

---

### Post by ulukay on 2011-03-01
hi
i was trying to get compcache working on a virtual 10.10 too, but did not succeed

~# grep COMPCACHE /etc/initramfs-tools/initramfs.conf              
COMPCACHE_SIZE="50%"

seems to be correct
did an:
update-initramfs -u
and rebooted - well, nothing really changed
no new swap, not even a ramzswap device!

~# /usr/lib/initramfs-tools/bin/rzscontrol  /dev/ramzswap0 --init  
Failed to open /dev/ramzswap0: No such file or directory

---

### Post by smashman42 on 2011-03-15
I've updated the 2.6.32.x kernel in Mythbuntu 10.04 x64 to a 2.6.35.x one from 10.10 to get ATA TRIM working for the SSD in my new ION mythbox.  I had been using compcache for swap successfully previously with the stock 10.04 kernel as the SSD is the only local drive (myth data located on NAS), the kernel update broke it for me too so it isn't specifically a 10.10 issue, rather a kernel one.

I'm going to try 2.6.34 or 2.6.33 instead & see what happens.


Edit: 2.6.34 doesn't work for me on 10.04 either, switch back to 2.6.32.x & compcache works again.  1:25am so bed for me, will try 2.6.33 tomorrow

---

### Post by lithopsian on 2011-03-15
As of the 2.6.35 kernel, compcache was in the process of being updated.  The default version shipped with the kernel is widely reported not to work.  You should download and build what is now called zram:
[http://code.google.com/p/compcache/source/browse/](http://code.google.com/p/compcache/source/browse/)

As of 2.6.37 (2.6.36?), zram is included in the kernel itself and can be used to map any block device into compressed RAM, not just swap devices.  rzscontrol is no longer used with zram.

---

