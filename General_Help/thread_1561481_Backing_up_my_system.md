---
title: "Backing up my system"
date: 2010-08-26
forum: General Help
---

### Post by kolo-01 on 2010-08-26
I think that it is time to accept that my system is broken and i will not be able to fix it, however before i wipe it clean i would like to back up my files, i know i should have done this while my system was working, but i will try to do this now through the command prompt as i cannot get onto ubuntu at all. can anybody offer help as to how to copy files to a usb hard drive through the command prompt? thanks

---

### Post by grief -l on 2010-08-26
If it were me I would not try CLI on a broken system - I would use a Live CD (doesn't even have to be ubuntu, can be puppy or slitaz) and move the /home directory to a backup medium.

---

### Post by hudsonl on 2010-08-26
Knoppix is perfect for this ....

[http://www.knoppix.net/](http://www.knoppix.net/)

---

### Post by kolo-01 on 2010-08-26
> **grief -l said:**
> If it were me I would not try CLI on a broken system - I would use a Live CD (doesn't even have to be ubuntu, can be puppy or slitaz) and move the /home directory to a backup medium.

i have tried using a live cd with the system but it doesnt look like it is able to boot in 'safe mode' either, i know this would be a lot easier, is there a way to use the cd in the command prompt as that is the only access to my system i have and boot up some sort of file shifting program through that?

---

### Post by grief -l on 2010-08-26
> **kolo-01 said:**
>  but it doesnt look like it is able to boot in 'safe mode' either, 

You didn't mention that you needed to boot into safe mode and you didn't explain why.  You should not need to boot into safe mode with a live CD since it runs mostly in RAM and doesn't use BIOS, Boot Record or Kernel files (it may make use of some modules if they are already installed but that's not going to destroy any data or hardware).

Just boot the Live CD, got to Places >> Computer and open the item labled  "File System" or "Hard Disk", navigate to /home and copy it to your USB

---

