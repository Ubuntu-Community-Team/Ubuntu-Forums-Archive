---
title: "Creating image of partitions"
date: 2011-01-06
forum: General Help
---

### Post by SARogers on 2011-01-06
I have what I thought was a simple task of creating ISO images of my Windows 7 system partion and boot partiton (the C drive) on my hard drive that I could use to load Windows 7 onto a virtual machine. Anyway, I'm running Ubuntu off the CD drive and I can see my drive partions (checked using the *fdisk -l* command). I have tried many iterations of the **mkisofs** command, but _no matter what I do I get the error message_: ***unable to open disk image file &#8216;dev/sdb/win7sys.iso&#8217;***. I don&#8217;t understand why it&#8217;s trying to open an ISO file it is supposed to be creating. The **[B]-o**[/B] FILE option sets the output file name, so the message makes no sense to me. Below is an example of a simple and longer version with more options that I have tried to create an image of my sytem partiton (sda1) and save it on an external drive (sdb) with the file name: win7sys.iso (the next step I think would be to create or merge both partition images as one iso file for the VM). But I can't get past this error.
 
_Can anybody tell me what I'm doing wrong_?
 
**sudo mkisofs -o dev/sdb/win7sys.iso /dev/sda1**
 
**sudo [B]sudo mkisofs -input-charset iso8859-1 -V win7sys -o dev/sdb/win7sys.iso /dev/sda1**[/B]
 
***** Note that the output after the **-o** parameter is the desired destination **/dev/sdb** (my external drive) for the image file and **/dev/sda1** is my Windows 7 system or boot partition (**sda2** is what Windows sees as the C drive).

---

### Post by HermanAB on 2011-01-06
Howdy,

> -o dev/sdb/win7sys.iso

Should probably be something like:
> -o /home/joesoap/win7sys.iso

Anyhow, turning Win7 into a VM that way will probably not work.  There are various problems: The hardware device drivers of a VM are different and if you fix them all, it will trigger the MS copy protection.

There is a special migration utility on the VMWare web site that should do the job.

---

### Post by mlentink on 2011-01-06
More likely, if you attached the external drive after booting up from the livecd, you'll find it at 'media/external_drive' or somesuch. 

But I agree with HermanAB. Trying to use such an iso to make a virtual machine is not going to work. Your virtual hardware has nothing to do with the hardware win7 was installed on, so it will scream at you

---

### Post by SARogers on 2011-01-06
Thanks guys.  I suspected I was going down a road with a dead end.  I had read a few things that hinted at this not working and the licensing problem.  Probably why I could not find anything explaining how to do this.  I will try to find the special migration utility on the VMWare web site to do this, but even if that works, I assume there is still the licensing issue that could prevent this w/o payment to Microsoft.  It is amazing to me why Microsoft with all the Windows problems over the years does not see the value in allowing users of a single machine to run Windows 7 on different VMs.  This would prevent one user from screwing the whole machhine up for the other users.  And what's the difference anyway.  Each user of one machine (like in my household) is not going to each pay a fee to use the same bloody computer.  Just one more frustration that will ultimately push me to Apple.

---

### Post by SARogers on 2011-01-06
Only way as mentioned in this thread is to install Win7 from install disks on the VM.  Something like Parallels Desktop 4 for Windows would work well to do that.  _I have looked at the special migration utility on the VMWare web site_, but that looks like it's for migrating Windows XP to Win7 and for use at the enterprise level.  Does not look like this will work for me.
 
So my question now is if I install Win7 on multiple VMs from install disks, setting aside the licensing issue for a moment which I will address with Microsoft, will this work?  I see now reason why one can't run Win7 on multiple VMs on the same machine.  Certainly this is being done all the time and done simultaneously from a server.  In may case only one VM at a time will be used.  Again, for me, it's all about isolating one user from another on the same machine.

---

