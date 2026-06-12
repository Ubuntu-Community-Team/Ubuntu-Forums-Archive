---
title: "Help! Error on Boot - Novice here"
date: 2010-11-12
forum: General Help
---

### Post by nikonelite on 2010-11-12
Hi there, 

I am recieving the following error on boot and am unable to get into ubuntu anymore :(

"EXT4-fs (sdc1) : Unrecognized mount option "nls=utf8" or missing value

An Error occurred mounting / "

I havent got a clue how to fix this, any guides/step by step instructions very helpful ...

thanks

---

### Post by Rubi1200 on 2010-11-12
Hi and welcome to the forums :)

We need some more information please.

What version do you have installed?

Are you booting other operating systems?

Are you able to boot into anything at all?

Is sdc an external drive?

Thanks.

---

### Post by nikonelite on 2010-11-15
Thanks for the reply,

i actually got it working by booting into a live distro and editing my fstab file.

i changed the sdc1 line to remove nls=utf8 and put only defaults.

and it worked.

---

### Post by Rubi1200 on 2010-11-16
Excellent! I am glad you got it sorted out :)

Please mark this thread Solved using the Thread Tools near the top of the page.

---

### Post by linux-hack on 2010-11-16
And you could post what you did so others may benefit !?

---

### Post by nikonelite on 2010-11-16
Of course, ill try to remember exactly but the rough instructions are.

Boot into a live Distro, i luckily had ubuntu Live lying about.

Mount your harddrive (in my case SDC)

Then open terminal ... and edit the fstab file on SDC.

when in terminal make sure you are on the hd you just mounted.

then "nano /etc/fstab" this is how mine fstab LOOKED


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc   proc    nodev,noexec,nosuid     0       0
/dev/sdc1       /        AUTO     defaults,***nls=utf8***,locale=en_GB.utf8      0       0
/dev/sda1       /media/System_Reserved  ntfs    defaults,nls=utf8,umask=0222    0       0
/dev/sda2       /media/Windows_7        ntfs-3g defaults,locale=en_GB.utf8      0       0
/dev/sdb5       none    swap    sw      0       0

the **nls=utf8** was causing the error. but when i just removed this i still go another error. So i just too the commands out and let it be defaults, See my new FSTAB file below.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc   proc    nodev,noexec,nosuid     0       0
/dev/sdc1       /       auto    defaults        0       0
/dev/sda1       /media/System_Reserved  ntfs    defaults,nls=utf8,umask=0222    0       0
/dev/sda2       /media/Windows_7        ntfs-3g defaults,locale=en_GB.utf8      0       0
/dev/sdb5       none    swap    sw      0       0

once i exit and saved, i restarted and it booted up fine with no issues.

Hope this helps anyone else, and any questions ask and ill TRY to help but i am a bit of a n00b

---

### Post by theozzlives on 2010-11-16
Good troubleshooting. See you're not as much of a noob as you thought.

---

### Post by mirearts KING SUNNY on 2010-11-16
Boot to an live distro and edit grub.lst

---

### Post by nikonelite on 2010-11-16
grub was booting fine, it was only when i selected.

at the time of hunting on google suggestions only said about fstab file.

---

