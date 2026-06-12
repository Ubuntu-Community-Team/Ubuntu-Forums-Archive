---
title: "Grub Error! and re-install"
date: 2006-03-23
forum: General Help
---

### Post by infinitelink on 2006-03-23
I use a dual boot Dell Insipiron XPS which I was working-on today. I was deleting partitions with the Windows partition manager and I decided to delete Ubuntu as well, so that I could just do a re-install of an upgrade to 5.1. When I start the computer it states "Grub 1.5." and then something like "cannot load" and "Error 17"

then it says loading, but does nothing, is Grub still on the system, maybe trying to find an OS or something like that? Windows is still there, I need my ability to use it restored. Any help would be appreciated. Also, though I've used Linux for a while, I'm still not well versed in technical particulars. I know that having different partions (like /home  /temp -?-  etc.) is a good idea, but what do they do, what are they for, and what are the minimums/maxes recommended? I want a /home simply so that if I install another linux it can be shared, and can "/whatever" which is used as extra Ram (though I have two gigs installed, so I don't know that I'll need it much) be Fat32 (that way I can share it as a Windows's pagefile) ?

Thanks for any help in advance, it's always appreciated. Also, when fixing Grub, can I do it from a usb? I have a key waiting. JBB ; )~

---

### Post by Bluztrvler on 2006-03-23
You did almost exactly the same thing that I did. The problem is that the grub loader is looking for operating systems that are not there. 

You can get windows back is you have your windows installation disk. Begin as if you are going to reinstall windows and go to the point that gives you a chance to repair an existing Win installation by use of the recovery console. This is a DOS like comand prompt. When you get the prompt, type     fixmbr   After this runs just use Ctrl-Alt_Del to reboot. This will repair your Master Boot Record and you will have windows back.

All of this is assiming that you are running WinXP.

---

### Post by infinitelink on 2006-03-23
Thank you kindly. : )

---

### Post by Dennis Huffman on 2006-03-27
Will this work on win98?:-k

---

### Post by can_climber on 2006-03-27
Hey Dennis,

  I think for win98 you should boot with a recovery diskette containing fdisk. Then run "fdisk /mbr" to fix your mbr.  But hey, it didnt work for me, but I think the disk was old old old.

---

