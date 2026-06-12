---
title: "Windows 7 doesn't work after installing ubuntu"
date: 2011-06-22
forum: General Help
---

### Post by magodiafano on 2011-06-22
I installed ubuntu 11.04 after windows 7. Now when I try to use windows 7, the system is rebooted and therefore I can't use windows 7.
What's the problem? please give me a very simple guide because I am a n00b with ubuntu.

---

### Post by sanderd17 on 2011-06-22
Is it this problem? [http://ubuntuforums.org/showthread.php?p=10968203#post10968203](http://ubuntuforums.org/showthread.php?p=10968203#post10968203)

---

### Post by jerrrys on 2011-06-22
in terminal enter **df **and post the results

---

### Post by magodiafano on 2011-06-22
administrator@administrator-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb6             36841040   3248796  31720784  10% /
none                   1020576       712   1019864   1% /dev
none                   1029812       200   1029612   1% /dev/shm
none                   1029812        96   1029716   1% /var/run
none                   1029812         0   1029812   0% /var/lock
/home/administrator/.Private
                      36841040   3248796  31720784  10% /home/administrator
administrator@administrator-desktop:~$

---

### Post by jerrrys on 2011-06-22
no indication of windows at all.  is this a wubi install or side by side?  to be sure, download "gparted" from the software center and check again.

---

### Post by magodiafano on 2011-06-22
I have two results. depending on the hard disk (I have 2 had disks)

[http://img8.imageshack.us/i/screenshot1dw.png/](http://img8.imageshack.us/i/screenshot1dw.png/)
[http://img805.imageshack.us/i/screenshot2u.png/](http://img805.imageshack.us/i/screenshot2u.png/)

---

### Post by jerrrys on 2011-06-22
looks like a bad install.  how did you install, what guide did you use?

since your windows seem to be intact, the easy way out in my opinion would be a reinstall.  and i would first remove the three worthless partitions on sdb1.

is one of these hdd's a usb?  if you installed ubuntu with a usb hdd plugged in, then it must remain plugged in to work.

also you did try the live cd without installing, right?

---

### Post by magodiafano on 2011-06-22
> **jerrrys said:**
> looks like a bad install.  how did you install, what guide did you use?

since your windows seem to be intact, the easy way out in my opinion would be a reinstall.  and i would first remove the three worthless partitions on sdb1.

is one of these hdd's a usb?  if you installed ubuntu with a usb hdd plugged in, then it must remain plugged in to work.

also you did try the live cd without installing, right?

do you believe that I have to reinstall ubuntu or windows 7?
and how could I remove the useless partitions? could you tell me which partitions are useless?

Besides I don't have any usb hdd plugged in.

I installed ubuntu without any guide: I plugged in an usb with ubuntu and it installed everything automatically.

---

### Post by jerrrys on 2011-06-22
sorry for not being clear.  ubuntu only for reinstall.  for reasons not yet known to us, ubuntu grub (boot menu) cannot boot windows.  so the easy fix would be reinstall (ubuntu) in my opinion.  this is why i asked about that second hdd.  

also if you want to post a pic to the forum, go to advance and click on the paper clip.

sdb5, sdb7 and unallocated should be removed.  really don't know how they got there in the first place.  thats why i wanted to know your install method.

did you run without installing first?  if the live cd will not work, your install wont...

---

### Post by magodiafano on 2011-06-22
ehm what is the live cd???

---

### Post by jerrrys on 2011-06-22
thats your install cd.  it will give you the option to try ubuntu without installing

---

### Post by FormatSeize on 2011-06-22
> **magodiafano said:**
> ehm what is the live cd???
A live cd is the medium by which one can install Ubuntu. Another method is the live usb. Live CDs and USBs are bootable media which can either be used to install Ubuntu, or to try it out by using the installation CD (live cd) to enter the desktop environment.
 
If you have either a Live CD or USB, boot from the media by making the appropriate changes in your BIOS, and then click "Try Ubuntu", which will allow you to enter the desktop environment. While this will not affect your computer at all, it does give you access to other parts of your machine, like other drives, and you can view and edit partition tables from the desktop environment.
 
To do that, you can either the partitioning tools provided by Ubuntu in the menu, which has an easy to use graphical interface. If you are a more advanced user, you can go to a terminal and type 
```
cfdisk
```
and use that to edit your partition table. I recommend using the first option.

---

### Post by magodiafano on 2011-06-22
> **jerrrys said:**
> sorry for not being clear.  ubuntu only for reinstall.  for reasons not yet known to us, ubuntu grub (boot menu) cannot boot windows.  so the easy fix would be reinstall (ubuntu) in my opinion.  this is why i asked about that second hdd.  

also if you want to post a pic to the forum, go to advance and click on the paper clip.

sdb5, sdb7 and unallocated should be removed.  really don't know how they got there in the first place.  thats why i wanted to know your install method.

did you run without installing first?  if the live cd will not work, your install wont...

I haven't run ubuntu without installing first... now I am gonna reinstall it hoping that it will work!

---

### Post by magodiafano on 2011-06-22
> **FormatSeize said:**
> A live cd is the medium by which one can install Ubuntu. Another method is the live usb. Live CDs and USBs are bootable media which can either be used to install Ubuntu, or to try it out by using the installation CD (live cd) to enter the desktop environment.
 
If you have either a Live CD or USB, boot from the media by making the appropriate changes in your BIOS, and then click "Try Ubuntu", which will allow you to enter the desktop environment. While this will not affect your computer at all, it does give you access to other parts of your machine, like other drives, and you can view and edit partition tables from the desktop environment.
 
To do that, you can either the partitioning tools provided by Ubuntu in the menu, which has an easy to use graphical interface. If you are a more advanced user, you can go to a terminal and type 
```
cfdisk
```and use that to edit your partition table. I recommend using the first option.

what's the name of the partitioning tool?

---

### Post by FormatSeize on 2011-06-22
> **magodiafano said:**
> what's the name of the partitioning tool?
It's referred to as "Disk Utility" and can be found by going to System -> Administration -> Disk Utility.

---

### Post by Mark Phelps on 2011-06-22
The BEST thing you can do right now is disconnect your Windows 7 drive.  That will prevent any more accidents using Linux utilities/installers.

You should then do any repairs/reinstalls with only the Linux drive connected.

After that, you should disconnect the Linux drive, reconnect the Win7 drive and see if Win7 will boot OK.

If it won't, you will need a Windows 7 DVD or a Win7 Repair CD in order to repair the boot loader.

---

### Post by magodiafano on 2011-06-22
I reinstalled ubuntu and the problem is not solved.
The main problem is in the fact that I don't have any win 7 DVD!
Please help me...

---

### Post by magodiafano on 2011-06-22
help me please...

---

### Post by jerrrys on 2011-06-22
would you please post some new pics of gparted.  lets see what you changed

---

### Post by jramshu on 2011-06-22
Did you add a new hdd or was it already there?

---

### Post by magodiafano on 2011-06-22
there is something very strange now because I am not able to see the  files in thw two hard disks... I can only see files in ubuntu partition.  When I try to open the other hard disks nothing happens.
These are the new images...

There is something very strange that I cannot understand...do the two different images correspond to the two different hard disks? because if it's true there is something strange.
The windows 7 is installed on sda1...

 > 
Did you add a new hdd or was it already there?

no...

---

### Post by jerrrys on 2011-06-22
the window rescue cd would be real handy right about now.  so lets do this the hard way. step by step.

first big question: you seem to have a backup of windows on your second drive. is this true?

what i suspect is either a bad burn or 11o4 itself.

what i suggest is:

removing the extended partition on drive one and this time install 10.10. running the live cd first before installing.

let's put this idea on hold till after lunch.  maybe someone else will come along with a better idea.

---

### Post by magodiafano on 2011-06-22
in the second drive I have several files but no backup! I believe that ubuntu created these backup in order to make the windows accounts reachable... it's an option of ubuntu 11.04... the only think I can do right now is installing xp... but since ubuntu creates a lot of problems I dont wanna use it anymore.

---

### Post by jerrrys on 2011-06-22
really can't blame you.  this is a lot of crap to go thru.  if you feel better off going with xp, then do so.
getting win7 bootable is the priority

---

