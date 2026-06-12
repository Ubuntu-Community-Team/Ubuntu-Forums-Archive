---
title: "i think create usb boot disk killed my mp3 player(which i currentlyhavebackupfileson)"
date: 2009-07-07
forum: General Help
---

### Post by suckmypianist on 2009-07-07
(i'm not sure where to put this post so if you are an admin please dont delete this but if you can please move it to where it belongs in the forum)
 
my ematic em108vidb 8gb mp3 video player freezes when ever i plug it into my computer. it gets to the screen when i says ready usb 2.0 high speed but no computer will recognize it. also i've tried it on my winxp sp2 and i have tried it on my ubuntu 8.10 (intrepid ibex) it worked just 5 days ago. what i think may have messed it up in the first place was that i was using ubuntu 8.10 (intrepid ibex) and tried to create a usb boot disk (done by going to "system>administrative>create USB boot disk") it said "starting" but the bar wouldnt load even after i left it for an hour. so i clicked cancel an i think thats what messed it up. if you can help me it would be greatly, GREATLY appreciated. also if you could send me an email to help me out that would be great becausei wont have internet for the next few weeks but i get my email on my phone... my email: [EMAIL="jpaulding22@gmail.com"]jpaulding22@gmail.com[/EMAIL] 
thank you sooo much in advance.
~Jeremy

---

### Post by ajgreeny on 2009-07-07
Try attaching it to ubuntu and running sudo fdisk -l to see if it is recognised by ubuntu and what the format type is.  I wonder if you have messed it up with a full format, but have to admit that I don't even know if making a usb boot disk formats the disk in question (I assume it does) or if so, which filesystem it formats to.

You could also open gparted in your install or from a live CD to see if that sees the disk, and if there is still anything on it.

---

