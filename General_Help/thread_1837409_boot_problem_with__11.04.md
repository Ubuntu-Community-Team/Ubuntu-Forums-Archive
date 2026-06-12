---
title: "boot problem with  11.04"
date: 2011-09-01
forum: General Help
---

### Post by frank4360 on 2011-09-01
Hello

My wife has a HP/Compaq netbook, and she has been running Ubuntu 11.04 for several months;

The only problem, normally, has been an occasional drop of the WiFi connection.

Today, though, the system froze, and after (many) forced reboots, including rebooting in safe mode and rebooting to an earlier version, the reboot stops completely after displaying "ubuntu".

The computer is dual-bootable with Windows 7, which boots up fine.  All her work is in the Ubuntu system, and so I need to be able to get the system back up and running.

Any ideas how to proceed from the "ubuntu" screen?

It doesn't help that we leave home in two days and need to rely upon the netbook for the next two months!!

---

### Post by MG&amp;TL on 2011-09-01
I can't help with the actual problem, but if you just want the files on the windows partition...

My suggestion would be to burn a cd of Puppy Linux:

[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm")

Boot it, and copy the important files onto a USB storage device (they are very cheap, the more the storage the lesss you will have to do, but the more the price). You WILL NOT NEED TO INSTALL PUPPY LINUX. All it is (for this application) is to copy files across. You could use an ubuntu live cd, but puppy is much quicker.

Then shutdown, remove the Puppy disk. Boot Windows. Copy files. Repeat if you could not get files across in one go.

I hope it helps.

What sort of non-boot are you getting? You say you can boot windows, so that means you can get to GRUB (purple boot screen?) Then what happens after that? Do you see any text or anything unusual apart from 'ubuntu'?

---

### Post by frank4360 on 2011-09-02
Thanks for the reply MG

The files are all backed up anyway, but I want (need) to get Ubuntu back without going through the hassle of re-installing - I haven't got the time!

On booting the computer I am presented with the Grub menu (version 1.99~rc1-13ubuntu3) with the selection Ubuntu, Ubuntu recovery mode, Previous Linux versions, memory tests, and Windows 7.

Unusually the Grub menu stays - previously it defaulted to a normal Ubuntu boot after a few seconds.

If I select normal Ubuntu boot, the purple background goes black with a cursor blinking for a few minutes, then the purple background returns with the word "ubuntu" underlined by 5 red dots. Nothing at all after that - no cursor and no reaction to mouse movements, function keys, escapes, etc.

If I select Ubuntu in recovery mode, the load process is displayed on screen but it hangs on "Begin: Running /scripts/init-bottom ... done".

I can boot Ubuntu, but only by selecting Previous Linux versions - of the two offered, only the second, 2.6.35-28-generic works. Unfortunately the Wifi connection doesn't! I have tried editing the wireless connections, deleting and recreating, but all in vain. 

As I am now in a desperate hurry as we leave home for two months on Sunday I am forced to ensure that Firefox, Thunderbird and all other programs my wife uses are set up on the  Windows 7 partition, as Windows connects, and boots, without a problem! 

Not good news for a committed Ubuntu user - but, sad to say, Windows works "out of the box" and Ubuntu simply doesn't.

---

### Post by MG&amp;TL on 2011-09-02
Boot live cd/USB. Navigate in the <filesystem> (not the USB/CD's filesystem) to /var/crash/ . If anything's crashed, it will be in there. :D

---

### Post by frank4360 on 2011-09-02
/var/crash is empty - I checked it after booting up with the Previous linux option, so it is certainly the correct directory. I do check for hidden files as well.

---

### Post by frank4360 on 2011-09-02
After copying Thunderbird and Firefox settings, bookmarks, etc to the Windows 7 partition (which involved booting up several times into the Previous Linux) I thought I would try the normal Linux boot again.

And it worked!!! Complete with the Wifi connection that did not work at all in the Previous Linux boots.

I have not changed anything knowingly, although something must have changed.

In some respects the "not knowing" is more worrying than the problem, as I have no idea what to do if (when) the problem recurs.

Thanks for your efforts.

---

### Post by MG&amp;TL on 2011-09-06
Oh well. Sorry, I would have been more helpful, but I had to go away unexpectedly.

---

