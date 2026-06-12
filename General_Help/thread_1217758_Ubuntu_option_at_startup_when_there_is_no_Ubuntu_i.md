---
title: "Ubuntu option at startup when there is no Ubuntu installation present"
date: 2009-07-19
forum: General Help
---

### Post by n00bhaxor on 2009-07-19
I uninstalled Ubuntu (unfortunately) because I was just having one problem after another, and windows XP works. But one bad uninstallation, and I have a problem: At the boot menu, I have the options of XP and Ubuntu, but Ubuntu is not installed. How do I remove this boot entry so it will boot straight into XP?

Thanks

---

### Post by c0mput3r_n3rD on 2009-07-19
I found [this]("http://beconfused.com/2008/02/12/how-to-make-windows-vista-boot-first-using-grub-in-ubuntu/") as the first response from a google seach saying "Make windows boot first".

---

### Post by n00bhaxor on 2009-07-20
That's not exactly what I'm looking for- I mean their are only 2 options-Windows XP and Ubuntu. How could Ubuntu be there if it doesn't exist on my computer? I want to remove that option totally.

---

### Post by hetx on 2009-07-20
What booter are you using? GRUB? IT is obviously there even if you say Ubuntu isn't. Find out what boot loader you use and find out how to edit the menu file for it.

---

### Post by TeoBigusGeekus on 2009-07-20
You need to fix your master boot record (mbr). 
You might have removed Ubuntu but grub boot loader still exists on your hard drive.

Boot up with a winxp cd and go to recovery mode. Type
```
fixmbr
```
and you're done.

---

### Post by n00bhaxor on 2009-07-20
I did that already, but I can try again.

---

### Post by n00bhaxor on 2009-07-21
Nope, still didn't work. Another piece of info: When I try to select the Ubuntu option, it says "missing <Windows Root>/system32/hal.dll. I guess I'll try to find it online and stick it in their.

---

### Post by n00bhaxor on 2009-08-04
Ahhh. I fixed it. 

In windows- go to my computer-->properties-->Advanced-->Startup and Recovery-->Settings-->Edit-->Delete the line with "C:\Wubi\Ubuntu (or w/e it says, as long as it has the word Ubuntu in it). Save it, and reboot. No ubuntu option, will boot straight into Windows :D

---

