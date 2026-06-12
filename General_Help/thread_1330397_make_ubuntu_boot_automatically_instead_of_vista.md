---
title: "make ubuntu boot automatically instead of vista?"
date: 2009-11-18
forum: General Help
---

### Post by confusedashell on 2009-11-18
hi all,

i have windows vista on a C drive on my laptop and ubuntu on a D drive. when i start up my laptop it asks me wich one do i want to load vista or ubuntu..... is there a way of making it loading ubuntu automatically? as at the moment the cursor howves over vista and is automatically loaded after 10 secs??

have tried using a gparted live cd to change the flag on the drive to boot???  but it comes up with "bootmgr missing"  

im pretty new to ubuntu and very impressed at the moment so go easy on me!

thanks in advance...

---

### Post by John Bean on 2009-11-18
You need to tell us which version of Ubuntu you are using.

---

### Post by oldfred on 2009-11-18
Windows uses the boot flag, Ubuntu does not. Although I have seen one or two users with some sort of boot loader that uses the boot flag to define what partition to boot from.

Is this a wubi install within windows? I do not know wubi. 

Or is this a normal dual boot install in a separate partition? If a dual boot what version of Ubuntu and grub.

versions  from command line in terminal:
grub-install -v 
uname -a

---

### Post by confusedashell on 2009-11-18
> **John Bean said:**
> You need to tell us which version of Ubuntu you are using.

sorry, its 9.04 jaunty?  that right?

---

### Post by arubislander on 2009-11-18
It shouldn't matter too much which version of Ubuntu you are using, although the information is relevant. But more so is how you installed it. Did you use wubi - installing Ubuntu from within Windows or did you install it after booting of the Live CD?
You mention having it on your D: drive which points to wubi, but then again it seems that the partition is dedicated to Ubuntu, which opens up other possibilities...

---

### Post by confusedashell on 2009-11-18
> **oldfred said:**
> Windows uses the boot flag, Ubuntu does not. Although I have seen one or two users with some sort of boot loader that uses the boot flag to define what partition to boot from.

Is this a wubi install within windows? I do not know wubi. 

Or is this a normal dual boot install in a separate partition? If a dual boot what version of Ubuntu and grub.

versions  from command line in terminal:
grub-install -v 
uname -a

i think it was installed within windows?  i put the install disc in when i was running windows and it guided me through the installation which i put on my D drive which (i have a hard drive partitoned into c and d drives from what i can gather..

no idea what a wubi is sorry?

us@ubuntu:~$ grub-install -v 
grub-install (GNU GRUB 0.97)
us@ubuntu:~$ uname -a
Linux ubuntu 2.6.28-16-generic #55-Ubuntu SMP Tue Oct 20 19:48:24 UTC 2009 i686 GNU/Linux

thanks.

---

### Post by confusedashell on 2009-11-18
> **arubislander said:**
> It shouldn't matter too much which version of Ubuntu you are using, although the information is relevant. But more so is how you installed it. Did you use wubi - installing Ubuntu from within Windows or did you install it after booting of the Live CD?
You mention having it on your D: drive which points to wubi, but then again it seems that the partition is dedicated to Ubuntu, which opens up other possibilities...


sounds like wubi then??? i ran the disc through windows, then it asked me where to install ubuntu so i put it in a seperate dedicated partiton D drive...

hope this helps?

---

### Post by arubislander on 2009-11-18
OK, I'll assume it's a wubi install then.

In Vista, go to the start menu, right click on Computer, then select Properties. On the left you'll see Advanced system settings. Click on that and then on the third Settings... button - the one by Startup and Recovery. You'll see a window titled System and Recovery. In System startup you can select the Default operating system. It will be on Windows Vista, but you should be able to select Ubuntu.

---

### Post by Cheesemill on 2009-11-18
As you installed using WUBI (**W**indows **UB**untu **I**nstaller) the Windows bootloader is in charge. To alter the default boot settings you can use [EasyBCD]("http://neosmart.net/dl.php?id=1") (if you're using Vista).
 
If you're using XP right-click on Computer and select properties. I can't remember which tab it's under but there is an option to edit boot.ini which you can use to edit the default boot settings.

---

### Post by sliketymo on 2009-11-18
OP's titles say's he's using Vista.

---

### Post by confusedashell on 2009-11-18
> **arubislander said:**
> OK, I'll assume it's a wubi install then.

In Vista, go to the start menu, right click on Computer, then select Properties. On the left you'll see Advanced system settings. Click on that and then on the third Settings... button - the one by Startup and Recovery. You'll see a window titled System and Recovery. In System startup you can select the Default operating system. It will be on Windows Vista, but you should be able to select Ubuntu.

thanks!  worked a charm!

would it be advisable to keep windows vista and my drive partitioned or try to remove the partiton and have ubuntu on the entire hard disk?

will ubuntu run quicker if it was the onlu operating system on the hard drive?

---

### Post by fluffman86 on 2009-11-18
It won't run quicker if it's the ONLY os, but it will run quicker with a full install instead of the Wubi install.  Here's what I would recommend: 

1. Uninstall Ubuntu from Programs and Settings under your Control Panel, and make sure that nothing else is stored on your D drive.  This will ERASE your D drive!

2. Download 9.10 from Ubuntu.com, and burn it to CD like you did with Jaunty.

3. Reboot your computer with the CD in the drive.  If it starts to boot into windows again, then Reboot again.  This time, look for options while your computer is booting.  On Dells, you see "Press F12 for Boot Options" and "Press F2 for BIOS".  You want to look for something like boot options so you can boot from CD, or if that's not available, then go into the BIOS and set your system to boot from CD.

4. When the Ubuntu logo comes up, press Enter to select "Try Ubuntu without any change to your computer" or something like that.

5. Make sure everything works.  Wireless probably won't work straight away, but you want to make sure you can play some of the sound in Places > Home > Examples.  If you've already been using Wubi, then this probably won't be an issue.

6. Go back to the Desktop and select Install.  Follow the prompts, and when it gets to the partitioning screen it will have a few options.  Choose "Manual"

7. In the manual partitioning screen, You will see either 2 hard drives or 2 partitions.  One will be the size of your D drive, and it should show up as being empty.  Ubuntu will call it either /dev/sdb or /dev/sda2.  Click on it, then choose "Delete.

8. Click on the freshly created Free Space, and choose Add.  This will be a primary partition, 1024 megabytes, and next to Use as select "Swap"

9. If the remaining free space is 40 GB or more, then create a new partition that's about 10 GB, this time choosing Ext4, and next to mount point choose "/".  Then Create another partition with the remaining space, again as Ext4, and Mount it to /home.

If the total size of D is LESS THAN 40 GB, just create the "/" and the swap, and home will automatically go inside of that.

10. Continue with the install, answer any of the questions, and eventually you'll be asked to reboot (after about 30 minutes to an hour of installing).  When you reboot you'll have a faster Ubuntu machine, and it will automatically boot into Ubuntu.  To boot Vista, you may need to hold down shift right after your computer powers on, and select it from the Grub menu. 

If you have any questions, just ask!

---

### Post by arubislander on 2009-11-18
I would suggest setting Windows Vista back as the default operating system before proceeding to try the above :)

---

### Post by fluffman86 on 2009-11-18
> **arubislander said:**
> I would suggest setting Windows Vista back as the default operating system before proceeding to try the above :)

> **fluffman86 said:**
>  Uninstall Ubuntu from Programs and Settings under your Control Panel, and make sure that nothing else is stored on your D drive.  This will ERASE your D drive!

That's what that does.

---

### Post by arubislander on 2009-11-20
Not when I uninstall it...

---

### Post by confusedashell on 2009-11-23
thanks guys, have done a full install now, unpartitioned my hard drive so i just have the one with ubuntu on it now....

only problem is my patop just crashes occasionaly, as if the power has been cut?  is ubuntu 9.1 unstable?

---

### Post by fluffman86 on 2009-11-23
If you're losing power altogether it's entirely possible that it's a problem with your laptop.  In my experience, if Ubuntu is going to crash it'll just freeze up for a bit, then either start working again or freeze permanently to where I have to force a reboot.

But no...9.10 is stable.  There's been some problems with it recognizing certain hardware, but it *IS* (mostly) stable.

---

