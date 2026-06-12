---
title: "Recommended system backup or imaging program?"
date: 2009-09-22
forum: General Help
---

### Post by edwinw on 2009-09-22
I've spent way too many hours so far getting my install of Ubuntu 9.04 working (working around a boot hang issue, custom nvidia drivers, compiz, dual monitor setup).  I'm wondering what backup or system imaging program would suit my needs.

Specifically, I want to do a one-time backup of my system install.  I don't have documents or data on the system that I need to backup.  I just want a backup "image" or something similar that (something like Norton Ghost for Linux?), if my system gets all full and crufty at a later date, I can just "restore" it to its current setup.

I've done a bit of research, and programs that could be made to work for me are remastersys, sbackup, rsync - could somebody recommend one of these or another program, and hopefully point me to a guide showing me how to use it?  Thanks!

---

### Post by raymondh on 2009-09-22
I use rsync in conjunction with grsync (the GUI, found in synaptic) to do my weekly back-ups.  The GUI makes it easier to use.

I also use [PING]("http://ping.windowsdream.com/") to image my partitions or HD .... just in case.

---

### Post by edwinw on 2009-09-22
Thanks for the reply.

Message to myself: also check out Clonezilla, Partimage, Rescue Is Possible, FSArchiver, tar.

---

### Post by Xero Xenith on 2009-09-22
I use rsync for backup of my personal files, it does that magnificently, but for a whole install? Clonezilla :) my +1 goes to that.

---

### Post by gordintoronto on 2009-09-22
My vote is for remastersys combined with unetbootin.  You can take your complete environment with you and run it on other computers...

---

### Post by DWL52 on 2009-09-22
I would like to echo his thoughts. I'm a Ubuntu Newbie, and have spent a lot of time and effort setting up my Ubuntu OS. I would hate to take a chance of anything happening and having to start over. Here's my situation: I have a 60 gig hard drive on which Ubuntu 9.04 is installed.  I also have a 500 gig drive that I use for storage. I've tried  following  the instructions on using Partimage several times and ran into one problem after another, from "running out of space (I don't see how) to Partimage starting to work, but then stopping, to it not being able to create a temp file, etc. I just want something that works!!!!!! I'm still trying to understand how I can unmount the drive that contains the fstab  and mtab files that tell Ubuntu what devices I have, etc. If someone can take this newbie by the hand and lead me through this in little steps, and assume I know nothing (which  is almost true!), I would be very grateful. What I want is to create a disk image of the OS Drive,and  store it on the other hard drive, just in case. Any help as far as how to do this, or what programs to use and how to use them would be greatly appreciated.

---

### Post by louieb on 2009-09-22
It sucks when a dist upgrade makes a mess of your install. Happened to me a couple of times. After the 1st time I started using partimage to backup. Its easy, it works, and the program can be found on just about any live rescue CD.  [Howto: Backup with Partimage - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=287522")

---

### Post by Darkwing-Duck on 2009-09-22
Rsync actually sounds perfect for you. Here is a tutorial that will explain things further then I can here.

[http://gwos.org/udsf/doku.php/software:backup:rsync](http://gwos.org/udsf/doku.php/software:backup:rsync)

Hope that helps you out.

---

### Post by doas777 on 2009-09-22
if you want the system itself then go with images, and if you want content files, use backup. I don't particularly like either option for a sys drive on the restore end, but it does work most of the time.

---

### Post by DWL52 on 2009-09-23
Well, rsync sounds like it is for making bckups from one machine to another machine, since it mentions the source machine and the destination machine in the first paragraph. Let me  make my situation clearer: I have one machine, and two INTERNAL hard drives. I have Ubuntu 9.04 installed on the 60 gig hard drive, and want to make a mirror image and store it on the 500 gig hard drive, just in case something goes wrong with the 60 gig drive. I would hate to have to reinstall Ubuntu 9.04, then go through all the hassle I had learning and redoing all the swettings to make everything work. As I said before, I tried Partimage and ran into one problem after another, including it beginning to work, then said I didn't have enough room. I watched it while it was working and it started out with less than two gig, and when that was used up (it counted down to zero) I got the error message that it didn't have enough room to create the file. I'm assuming it meant a temproary file on the 60 gig drive, or one in memory (I have 2 gig of memory). I have well over 400 gig free on the 500 drive. Following the online instructions about using Partimage, I booted from the live CD and tried to unmount the 60 gig drive, but got the error message that the device wawsn't found in fstab or mtab files. I'm at a loss as to what to do now! Can anyone help??

---

### Post by louieb on 2009-09-23
> **DWL52 said:**
> Partimage  I'm at a loss as to what to do now! Can anyone help??
[Clonezilla]("http://www.clonezilla.org/")  has a nice front end for partimage. It might be easier to use it to get set up.

---

