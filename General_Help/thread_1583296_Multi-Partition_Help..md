---
title: "Multi-Partition Help."
date: 2010-09-27
forum: General Help
---

### Post by phizikal on 2010-09-27
Ok, sorry if I sound like a newbie or whatever.. But if you need more info let me know & i'll fetch them for you.

Anyways, I installed Ubuntu 10.0 the other day as a separate partition on my laptop alongside my Windows 7 OS. I really like Ubuntu and I decided i'm going to backup all my data on Windows 7 and fully install Ubuntu on my hard drive. But, I am having trouble erasing my current Ubuntu partition before I go ahead and re-install it fully. Please help me uninstall Ubuntu cleanly & resize my hard drive partitions to normal before I download Ubuntu to go over Windows 7. I'm not much a computer genius these days, I would love to get some help on this subject. Please make your tips understandable.

Ubuntu is an amazing OS, I hope I can get my partitions cleaned up before install it fully over Windows. Thank you!

---

### Post by cj.surrusco on 2010-09-27
You don't necessarily need to reinstall Ubuntu for that reason. All you would need to do is:

1. Backup files onto external source (external HDD, secondary internal HDD).

2. Delete the Windows partition using a partition editor such as GParted.

3. Resize your Ubuntu partition. This needs to be done from a live CD, it is not safe to resize a partition while it is mounted (running).

Keep in mind that you may need to reinstall Grub if you are currently using the Windows bootloader.

---

### Post by phizikal on 2010-09-27
Sorry, I forgot to add this to the thread.

Is it possible I can move my files over to my Ubuntu partition & keep my windows 7 without some sort of Flash Drive or something? I have alot of music, folder with files/pictures, and a couple of programs/games that I would like to have on Ubuntu when I re-install it over my current OS.

I went onto Windows Disk Management and saw that I have several partitions, they are; [blank], [Acer [C:], and [SYSTEM RESERVED]. I don't see anywhere about a Ubuntu partition even tho I do have one.

I really would like to know these things before I make any dramatic changed to my hard drive, please let me know how I can remove Windows 7 and extend the Ubuntu Partition please. 

Sorry if I am asking for too much, just don't want to ruin my only computer that I have and very much needed. :confused:

---

### Post by srs5694 on 2010-09-27
The Windows Disk Manager doesn't do a good job of identifying Linux partitions. I recommend you use a Linux tool, such as the GUI GParted or the text-mode fdisk, to identify your partitions.

For better advice, I recommend you post a screen shot of GParted showing your disk and an estimate of how much data you want to preserve from Windows (in megabytes or gigabytes). With that information, we'll be able to give you better informed and more precise advice. There may be ways to do this that will be safer than what cs.surrusco suggested; however, it depends on the current partition layout and how much data you want to preserve from the Windows installation.

---

### Post by phizikal on 2010-09-27
[[IMG]http://img685.imageshack.us/img685/6168/screenshothao.png[/IMG]](http://img685.imageshack.us/i/screenshothao.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

Here is the screenshot of my partitions,i want to remove windows and set ubuntu as my default OS.


Edit: I don't have a live CD tho.

---

### Post by cj.surrusco on 2010-09-27
You don't have an Ubuntu partition, so you must have a Wubi install. In this case, you would need to reinstall Ubuntu. You can follow the procedure in my previous post, except instead of enlarging the Ubuntu partition, you would want to create a new one over the whole drive during the install process.

---

### Post by phizikal on 2010-09-27
That's good news and made it much much easier for me, thank you. Can you give me the link to the real installation file for ubuntu?

---

### Post by cj.surrusco on 2010-09-27
[Here]("http://www.ubuntu.com/desktop/get-ubuntu/download")'s the download page where you can get a disk image (.iso) of the Ubuntu Installer. You'll need to burn a CD of it. Then you can boot from the CD and the installer will run. When the installer gets to the partitioning part, choose to erase the entire disk and use it for Ubuntu, but only after you've backed up your data, of course.

---

### Post by phizikal on 2010-09-27
Thank you soo much, I will most certainly back-up all of my date first. I will reply if I have any future trouble, won't be-able to this until I buy a flash drive or an external hard drive.

---

### Post by srs5694 on 2010-09-27
I concur with cj.surrusco's advice. A couple more minor points:


[list]
[*]If your computer is 64-bit capable (as most sold in the last few years are), I recommend using the 64-bit version of Ubuntu, despite the "not recommended for daily desktop usage" statement on the Ubuntu download page. The 32- vs. 64-bit topic has been hashed to death on this forum in other threads, although I don't happen to have URLs handy, so you'll have to search if you want to find these old threads. In a nutshell, though, the 64-bit version will produce a modest speed increase (perhaps 10%, on average, for most uses) and will better handle memory over 4GB. A small number of programs work better in 32-bit form, but for the most part you can run the 32-bit versions if you really need them. Flash is probably the most notable remaining 64-bit issue, but Adobe's recently released a new 64-bit Flash for Linux that's gotten some positive reviews.
[*]I recommend doing a manual partitioning. Set aside 10-20GB for the Linux root (/) filesystem, where the main OS files reside (given your disk size, you might as well go for 20GB); 1-2 times your RAM size for swap space; and the rest of your disk space for /home, where your user files go. This is different from the default install, which doesn't create a separate /home. Splitting off /home makes it easier to do certain types of upgrades in the future, since you can wipe out the root (/) filesystem where the OS itself resides without damaging your user files in /home.
[/list]

---

### Post by phizikal on 2010-09-27
And also, if I don't have a Ubuntu on a separate partition; then where is it?

And how do I remove it until I have the stuff for it to have it fully installed over Windows 7 later on?

---

### Post by phizikal on 2010-09-28
*cough* sorry, fall giving me troubles. =P

---

### Post by srs5694 on 2010-09-28
> **phizikal said:**
> And also, if I don't have a Ubuntu on a separate partition; then where is it?

As cj.surrusco has said, it appears you've got a WUBI install, which means that Linux installs itself in a file in a Windows partition rather than to its own partition. I'm not too familiar with WUBI, so I can't tell you how to verify this configuration, but clearly there's no Linux partition on your disk. (If you've got another hard disk, though, now's the time to tell us; Linux could be there.)

> And how do I remove it until I have the stuff for it to have it fully installed over Windows 7 later on?

If you don't care about your current Linux installation, don't worry about it; it'll be wiped out when you delete the Windows partitions. If you've got any data you want to back up from your current Linux installation, though, you should back it up to an external disk or a network-accessible computer before you re-install Linux.

---

### Post by phizikal on 2010-09-28
Ok, i changed my mind. I wanna keep Win7 on my laptop & add ubuntu onto my desktop for max performance.

How do I remove the Wubi or whatever off my laptop, it's kind of causing some weaksauce problems on my lappy.

---

### Post by cj.surrusco on 2010-09-28
Check the uninstallation section [here]("https://wiki.ubuntu.com/WubiGuide#head-61fe7beb6f9507b384ce19642d3dcb697b19aeb1"). You uninstall it just like any other program.

---

### Post by Serpher on 2010-09-28
In Windows right click on My Computer --> Manage --> Disk Management, and shrink your Windows partition. Ubuntu really only needs 30G. A swap partition really isn't needed unless you have under 2G of RAM. Keep in mind you're not copying the .iso to a disk. In Windows or Ubuntu right click on it and select "Write to Disc". When it's burnt and your partition is resized (And wubi is uninstalled and your files are backed up), put that disc in your tray, restart your computer and press whichever F key the BIOS menu's tell you to press to select your boot device or whatever it says.

---

