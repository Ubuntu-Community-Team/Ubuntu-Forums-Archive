---
title: "*facepalm* Installing Windows MBR Without Original Recovery Disk"
date: 2009-10-24
forum: General Help
---

### Post by PaulTR on 2009-10-24
So I deleted the Ubuntu partition I had on my laptop because the wireless just wouldn't work after a lot of trying, but now I'm getting the GRUB 22 error. Tried to fix that via a few guides, but during the find /boot/grub/stage1 part, it's not finding anything and I don't have the windows recovery vista CD since Acer thinks it's brilliant to just use a recovery partition, and I didn't have any blank DVDs at the time to make a copy <.<. Is there any way to download the MBR and burn it to a regular blank CD to run/install at boot, or a way to reinstall grub on the Windows partition (I extended the unallocated space from the Ubuntu partition in the Windows partition, so I have sda1 which is the recovery partition, and sda2 which is the windows partition). Or Hell, does the Windows 7 CD that they're mailing out for the upgrade have the options to repair like that? May just wait it out if it does :P Thanks.

---

### Post by Keith Hedger on 2009-10-24
Use super grub to fix mbr problems, see my sig for the address

---

### Post by PaulTR on 2009-10-25
The site in your sig didn't have any .iso files that I could download, but I looked around and found one, burned it and used it. Worked perfectly, and I'm incredibly excited to have learned something new :p Thanks a ton.

---

### Post by sea_monkey987 on 2009-10-25
also the idiot proof solution is the vista recovery disc which you can download from here [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

you just boot it and select the startup repair option and it handles the rest.  note that this will remove grub from the mbr so don't do this if you wish to keep grub.

---

