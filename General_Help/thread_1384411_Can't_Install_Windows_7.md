---
title: "Can't Install Windows 7"
date: 2010-01-18
forum: General Help
---

### Post by 85Dave on 2010-01-18
Hi all! New user here. I'm new to Ubuntu, and not that good at computers. So bear with me.
When I installed Ubuntu 9.10, I had the partition thingy partition the whole hard drive. That was a mistake.
Now, I'm trying to install Windows 7 using the start-up disk and recovery disks. When I insert the start-up disk, it starts loading Windows files. Then it tries to re-boot, but it just starts reloading the Windows files. It just keeps doing this over and over.
How can I install Windows 7?

---

### Post by OrangeCrate on 2010-01-18
> **85Dave said:**
> Hi all! New user here. I'm new to Ubuntu, and not that good at computers. So bear with me.
When I installed Ubuntu 9.10, I had the partition thingy partition the whole hard drive. That was a mistake.
Now, I'm trying to install Windows 7 using the start-up disk and recovery disks. When I insert the start-up disk, it starts loading Windows files. Then it tries to re-boot, but it just starts reloading the Windows files. It just keeps doing this over and over.
**How can I install Windows 7?**

To dual boot with the least amount of problems, install Windows 7 first, then add Ubuntu 9.10. Here's list of instructions to use:

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

---

### Post by 85Dave on 2010-01-18
How do I install Windows first? I put the Windows install cd in, and it gets stuck in some kind of do-loop. It won't install. I don't have anything on the hard drive except Ubuntu.

Do I un-install Ubuntu and then install Windows? If so, how do I un-install Ubuntu? 

What about the grub? How do I delete it so that I can install Windows?

---

### Post by Mark Phelps on 2010-01-18
If your Win7 disk only boots you into Windows Recovery mode and then tries to do a restore from a file on your drive -- and if you wiped out that file when you chose the "whole disk" option, you've no way to restore Win7 at this point.  You would need to contact your machine vendor and find out what they recommend.

---

### Post by OrangeCrate on 2010-01-18
> **85Dave said:**
> How do I install Windows first? I put the Windows install cd in, and it gets stuck in some kind of do-loop. It won't install. I don't have anything on the hard drive except Ubuntu.

Do I un-install Ubuntu and then install Windows? If so, how do I un-install Ubuntu? 

What about the grub? How do I delete it so that I can install Windows?

To reinstall Windows, you're going to need an NTFS partition. The easiest way to get out of the mess, is probably to reformat your hard drive.

I'm currently on Windows 7, and I don't have Ubuntu, or an Ubuntu Live CD in front of me, but boot into yours...

When you have the desktop, go System > Administration > Partition Editor (or it may say GParted), and open up your partition dialog.

Turn off Swap (last listing?) and then delete all of the partitions. When they are deleted, click on New, and reformat the hard drive to "NTFS". Click "Apply", and you'll end up with a fresh NTFS formatted hard drive.

You then can reinstall Windows 7 onto the computer, using the installation disk. (Then, somewhere down the road, after you've healed up from all of this, if you want to dual boot, follow the instructions I already pointed you to in my previous post.)

Please don't just jump in to this without understanding what you're doing. Check the Help Files to be sure I remembered everything, though I'm pretty sure that I did, and search for other info along the same lines as I suggested.

Good luck.

---

### Post by gimcrack on 2010-01-18
Hey, lets face it you mess up. By wiping the whole drive and installing Ubuntu over your existing operating system Windows 7.

You now have Ubuntu and got rid of Windows 7. No Windows recovery disk will fix this. You need a full version of Windows 7. To reinstall Windows & to duel boot, you need to share the drive with Windows not get rid of it like you did before.

I don't think you did a bad thing. Getting rid of Windows is always a good thing in my book. Be happy with Ubuntu or any other Linux Distro if you are not fawn with Ubuntu. Yes you have to contact your vendor to see if you can get a copy of Windows 7 or pay a fee.

Enjoy Linux and forget about Windows, I sure did.

---

### Post by 85Dave on 2010-01-19
Thanks, OC.
I opened GParted on the Live CD disk. It shows the following partitions:
/dev/sda1        ext4         143.49 GiB size      4.84 GiB used     138.65 GiB unused     boot (Flags)
/dev/sda2        extended     5.56 GiB              ------                       -----
    /dev/sda5    linux-swap   5.56 GiB              ------                      ------

I don't see Swap anywhere on the window. Where should it be?
I see a button to Delete the selected partition.
And I see a button to Create a new partition.

So I delete the 3 above partitions, and Create a new one? When I click Create, I assume it gives me options for NTFS.

I don't have any files that I want to save, so I just start deleting the partitions, create a new one in NTFS, then I should be able to load Windows? Right?

What about Grub? Does it get deleted when I delete the partitions? Or is it hiding somewhere? I think it's the grub that prevented me from loading Windows. If the grub is hiding somewhere else, how do I remove it?

Again, thanks for your help.

If anyone else has any advice, I'm all ears.

---

### Post by 85Dave on 2010-01-19
There's a couple of things that Ubuntu won't do. For one, I can't access my work email unless I'm using Windows or OSx. Another thing, the printer I bought a few months ago does not have drivers for linux. I emailed Canon and asked about it, and they basically said they only support Windows and OSx. They suggested looking around on the internet to see if anyone else figured a work around. I did, and found that there are some drivers in Germany, but when I tried installing them, the printer still didn't work.

I like Ubuntu otherwise, and my son loves it. So I'll probably install it after I recover from this mess I created. But I've got to get Windows working somehow.

> **gimcrack said:**
> Hey, lets face it you mess up. By wiping the whole drive and installing Ubuntu over your existing operating system Windows 7.

You now have Ubuntu and got rid of Windows 7. No Windows recovery disk will fix this. You need a full version of Windows 7. To reinstall Windows & to duel boot, you need to share the drive with Windows not get rid of it like you did before.

I don't think you did a bad thing. Getting rid of Windows is always a good thing in my book. Be happy with Ubuntu or any other Linux Distro if you are not fawn with Ubuntu. Yes you have to contact your vendor to see if you can get a copy of Windows 7 or pay a fee.

Enjoy Linux and forget about Windows, I sure did.

---

### Post by john newbuntu on 2010-01-19
Well since you have anyway blown away your partitions, now is a good time to think on how much space you need to allocate for windows and linux(possibly even multiple versions of linux and windows in future).

It appears that you have about 150GB in your hard disk drive.  If you make it all NTFS, you will have to change that back later on to ext4 or ext3 when you install linux.

BTW, swap is presently on /dev/sda5.  Right click and choose swapoff in Gparted.

So, using Gparted on a liveCD, create the first partition /dev/sda1 - give it say 50GB and format it as NTFS. Mark this as primary/boot partition.  This is where you will be installing Windows 7.

Then create an extended partition right next to it.  (It will mark it /dev/sda2) - give it, say 40GB.

Now, within the extended partition, create a 2GB logical swap partition(/dev/sda5) and a 37GB ext4 partition(/dev/sda6) (both for Ubuntu for now.  The names will be automagically set by gparted).

That should be it for now.  You can always go back and increase (possibly even decrease partitions).  Now you have the flexibility to add more primary or logical partitions.  Feel free to play with the arbitrary numbers I added here.

Forget the GRUB2 for now.  It is not preventing you from loading windows. It is partly hiding before /dev/sda1 but will be overwritten soon.  Go ahead and install windows 7 first from your installation CD (not rescue/recovery CD.  I hope you have it) on /dev/sda1 (or first boot partition or "C" drive).

Once this is completely done, Insert Ubuntu Karmic liveCD and install it on partition /dev/sda6.  Use /dev/sda5 for swap space.  Let it complete the installation and you are all set.

---

