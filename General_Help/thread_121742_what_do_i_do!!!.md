---
title: "what do i do??!?!!"
date: 2006-01-25
forum: General Help
---

### Post by shrimants on 2006-01-25
i tried to install ubuntu and it failed miserably. after the first time i tried it said to make sure there are no disks so that it can boot from the ubuntu disk. and when it reboot after i took out the disk (i thought thats what it meant) it said DISK BOOT ERROR, PLEASE INSERT BOOT DISK AND PRESS ENTER. i tried to unsuccessfully reinstall a couple of times but all i've been ablt to do is get a blank screen after the OS selector if i clicked windows and get a respawned too fast timeout thing for loading the other one.

i was trying to load it onto a 10 gb hard drive that was a primary slave. now i just want to get rid of everything and not even windows is loading anymore. what do i do to get my comouoter back to normal? (all of our critical files are on it)

---

### Post by aysiu on 2006-01-25
> **shrimants]now i just want to get rid of everything and not even windows is loading anymore.[/quote] Try [url=http://support.microsoft.com/default.aspx?scid=kb said:**
> this[/url].

[quote]what do i do to get my comouoter back to normal? (all of our critical files are on it) If you've installed Ubuntu *over* your previous Windows install, then your files are gone. The only way, ironically enough, to get your critical files (if they still exist) is to use a Linux live CD. It can be done with the Ubuntu live CD, but for a beginner, Knoppix is a lot easier for recovery of data.

---

### Post by siucdude on 2006-01-25
well i have had same problems before, if you files are on the windows portion you can reinstall windows but make sure you don't format the drive,  at boot up it gives you a question about partition, make sure you select same drive what it will do is install windows over existing one making files, windows.00 and mydocuments.00 all you have to do then is backup all your files and install everything from start,  first windows and then ubuntu.  good luck

---

### Post by siucdude on 2006-01-25
[QUOTE=siucdude]well i have had same problems before, if you files are on the windows portion you can reinstall windows but make sure you don't format the drive,  at boot up it gives you a question about partition, make sure you select same drive what it will do is install windows over existing one making files, windows.00 and mydocuments.00 all you have to do then is backup all your files and install everything from start,  first windows and then ubuntu.  good luck[/QUOTE]

one thing, if you did install ubuntu over windows then your files are gone but if not use windows since it seems as if your files were under windows, 
second don't create any users just administrator for windows, this will give you access to backup all.

---

### Post by shrimants on 2006-01-25
its giving me a bunch of grub errors. first 21 after i tried booting from just the primary with other one disconnected, then 15 after i tried to boot with both connected. the only live CD i have is WHAX, i think it should work. the main problem was that it couldnt format partition#1 in ext3. annd i cant use the above method because linux isnt fully installed, its like an aborted install. i wanna just delete the grub files off the original HD and format the 10 gig one. im gonna first see what the grub errors mean, and then try my home XP upgrade CD's recovery mode, which wasnt working earlier for some reason. i cant really reinstall XP because i have the home upgrade disc, but the full professional installed. is it gonna screw stuff up if i use the home disc to install?

EDIT** i went through the repair console and formatted the f: drive (the ten gig one) and i did fixmbr, to write a new master boot directory. i think that my windows files are screwed, and i need to reinstall them, as long as my documents and programs and stuff will remain. also, i am gonna need a winxp professional CD unless my home upgrade CD can safley fix my files. i think my parents are gonna kill me.

---

### Post by siucdude on 2006-01-25
its hard to say,  from past experiance and different distros i can tell you that forget about your windows settings,  I have never found a way to recover fully,  if you install home its going to work but two things to remember if you install home over current one from bootup, make sure you don't delet the partition for windows just install over it.  this will give you a basic system with windows but all your past files will be on there if you did not install ubuntu over them.  second most of the files after you boot to windows will be in backup or sencond user mode just copy them over to cd or something and you then can partion the entire disk all you want

---

### Post by shrimants on 2006-01-25
ok. i think i will try that. i have serious doubts though because the thing gave me a huge warning before installation, almost as if it ensured failure. i think that i will consult microsoft's site or mayB call them tomorrow. or, since i dont want my parents to find out, i will just try for now with WHAX to retrieve the my documents folder and put it on my external hard disk and then try the install.

---

### Post by stardotstar on 2006-01-25
You may be able to get windows to boot if you have not installed Ubuntu over the original windows partitions as mentioned above.  GRUB has been installed onto the Master Boot Record of your primary/master disk and failing to recognise the disks/paritions correctly.

When you were installing Ubuntu did it recognise the windows installation at the time when it updated the MBR with GRUB before restarting for the first time.

If it did then you may be able to get into windows two ways:
1) Use Grub Super Disk and learn a bit about how to identify the disk and partition name that your windows boot normally happens on and then launch it from the Grub command line:

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

``` 
OR

2) use a windows boot floppy from Win98 or something (can't remember) and use fdisk to restore the MBR (don't try this till you confirm it - I can't remember) fdisk -mbr or something...

Sorry no definite answers.

---

### Post by shrimants on 2006-01-25
i already did the rewriting of the mbr. i used the home repair console. the command was fixmbr. i did that and now it just doesnt recognise harware. whax doesnt even boot up. it gets stuck at creating /etc/fstab. i think that i will just have to go in to microsoft's chat and ask them.

i dont know anything about the grub thing. i dont even know if i can install it or not. the big hard drive i have is only detected when the slave HD is turned off, btw. i dont know if this helps or not. i appreciate the help.


edit: ok. i've been able to load whax, so mayB i can get the windows xp professional floppies, and then use those to install.

---

### Post by shrimants on 2006-01-25
nope. no such luck. the live CD doesnt communicate with the actual HD. im stuck unless i get an install disk.

---

