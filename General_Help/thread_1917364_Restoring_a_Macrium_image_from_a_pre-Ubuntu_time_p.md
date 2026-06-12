---
title: "Restoring a Macrium image from a pre-Ubuntu time period"
date: 2012-01-29
forum: General Help
---

### Post by UnderPar on 2012-01-29
I backed up an XP system in Sept. 2009 using Macrium Reflect 4.2.  The resulting image is only 10GB out of 110GB.  Since that time, I have turned it into a dual-boot Ubuntu 11.04, but now the XP side is 53GB out of 90GB total, since I gave 20GB to Ubuntu.

If I restore that 10GB image, overwriting the 53GB, will I also lose my boot menu upon startup that lets me choose to boot up Ubuntu, since it was was created pre-Ubuntu?

Also, is there an easy way to allocate an additional 10-20GB to Ubuntu either before or after the image restore?

Thanks!

---

### Post by UnderPar on 2012-01-30
*bump*

---

### Post by Mark Phelps on 2012-01-30
First of all, STOP bumping.  The rule around here is no more than once every 24 hours.

Second, the size of the saved image file(s) do not matter.  MR will restore the entire original partition.  So, if you imaged off a 11GB partition, even if the resulting file is only 15GB, MR will still need 110GB to restore the original partition.

You usually have an option regarding restoring the MBR.

---

### Post by holycow131415 on 2012-01-30
id imagine grub would be messed up as well, if not gone.

---

### Post by UnderPar on 2012-01-30
> **Mark Phelps said:**
> First of all, STOP bumping.  The rule around here is no more than once every 24 hours.

No problem.   Didn't know!  The thread had disappeared to page 3 and I  wanted to see if the daytime members had an answer.  Won't happen  again.  [IMG]http://img.photobucket.com/albums/v707/HandsomeTramp/smilies/shake.gif[/IMG]

> Second, the size of the saved image file(s) do not matter.   MR will restore the entire original partition.  So, if you imaged off a  11[COLOR=Red]0[/COLOR]GB partition, even if the resulting file is only 15GB, MR will still need 110GB to restore the original partition.I do not believe this is correct with v. 5.0.4.  When dragging the image  file to the destination partition, it adapts to that size, if there is  the available space.  I may be wrong, [but that's how it read to me]("http://www.macrium.com/help/v5/How_to/Restore/Restore_Disks_and_Partitions.htm").

[IMG]http://i.imgur.com/rFJD3l.png[/IMG]



> You usually have an option regarding restoring the MBR.This is what I am really asking.  Where and when would I be given this option? 

I'm just concerned that I will restore the automatic Windows XP boot and not know how to get into Ubuntu.

Thank you for your time.

---

### Post by xyzzyman on 2012-01-30
You should just be prepared for it wiping out GRUB, and have an ubuntu livecd ready. Also make sure your ubuntu is backed up incase something goes wrong.

---

### Post by Mark Phelps on 2012-01-31
> **UnderPar said:**
> I do not believe this is correct with v. 5.0.4.  When dragging the image  file to the destination partition, it adapts to that size...

That's news to me -- as I only use MR to do complete partition restores.  This would be interesting -- if it actually works -- because one of the major limitations of Clonezilla is that it can not restore a partition to a smaller space.


> Where and when would I be given this option? 
I believe that when you click Next, you will be taken to another screen where you have a box you can check to tell it whether or not to rewrite the MBR from the backup.

> I'm just concerned that I will restore the automatic Windows XP boot and not know how to get into Ubuntu.

Even if you do overwrite the MBR, it's a simple matter to then boot from an Ubuntu desktop CD and restore GRUB:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by UnderPar on 2012-02-01
Thanks to all for the useful info.  I think I will just backup well, and be ready to install Ubuntu again if it becomes too much of a hassle.

---

