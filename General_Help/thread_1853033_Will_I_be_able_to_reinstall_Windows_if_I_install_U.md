---
title: "Will I be able to reinstall Windows if I install Ubuntu on my netbook?"
date: 2011-10-01
forum: General Help
---

### Post by jackyboy633 on 2011-10-01
Hi all! ):P

I'm considering getting a netbook (Asus Eee PC 1015PX), and I would like to install Ubuntu on it. However, I would like the option of reinstalling Windows on it, (in case I have to return it, etc. However, the recovery Windows is on a partition, not a disc, and I would like to use the full disk space if possible. I do have a spare Windows 7 disc, but it is Home Premium, not Starter (what comes on the netbook). So, does anyone know a way how to create something that I can recover Windows without a recovery partition.

This can be moved if it is placed in the wrong forum.

Regards, Jackyboy633.

---

### Post by matt_symes on 2011-10-01
Hi

Have you considered imaging the entire hard drive using Clonezilla, dd or some such ? If you do it then make sure you verify the image before wiping windows.

Kind regards

---

### Post by MG&amp;TL on 2011-10-01
Several options:

1. Use *wubi*. An OS, shoehorned into an executable run at startup, you can run ubuntu as you wish, with little limitation, and uninstall it when you are finished. Can be buggy though.

2. Use Virtualbox. Setup virtualisation on your windows, allowing you to have a virtual pc to play with.

3. Boot from USB/CD (select the try button on the screen every time.)

4. Dual-boot. Partition the hard drive further, and run a bootloader at boot to allow you to choose between the two.

5. Install over it, then use you windows install disk to get windows back again.

---

### Post by prodigy_ on 2011-10-01
> **matt_symes said:**
> Have you considered imaging the entire hard drive using Clonezilla
+1, having a backup never hurts. And restoring from a backup is always the easiest (and often the fastest) way back if something goes wrong.

---

### Post by westie457 on 2011-10-01
Make two backups. The first one should be a copy of the recovery partition. The OEM supplied software should allow you to do that.
The second back up should be a full back up of your Windows system as it is now. That is the only back up Windows will do when that utility is first run.

A program like Clonezilla should be able to do both.

---

### Post by dave2001 on 2011-10-01
Short answer:

Yes, but you need to prepare for it.

Long answer:

If I was in your situation I'd do the following. Use a free program to make a back-up image of the hard drive. I prefer Macrium reflect for windows systems. It's user friendly and "just works." There are also plenty of instruction and tutorial pages out there.

Once you have a working hard-drive backup image, you'll be able to return that computer to it's "fresh-from-the-store" condition at any point.

Now your options for Ubuntu installation. You could just wipe the hard-drive and put only Ubuntu on there.. but your paying for a copy of windows, so why not have both? Setting up a dual-boot Windows/Ubuntu machine is not really much more complex than a regular installation of either. I've been running a dual-boot of Win7 and Ubuntu 10.04 for about a year now, and I love having both OS's at my disposal. There are some good tutorials on the web for this, but speaking from personal experience, here are my suggestions:

Start from Scratch! Create new partitions with an Ubuntu live-cd using G-parted. Create the partitions, in this order, on your disk: Windows OS (min 15-20Gb for win7), Personal Data, Ubuntu OS (min 10Gb), Ubuntu Swap (twice the size of your RAM). I'd use an NTFS file system for the Personal Data partition, but there is some debate on the subject, you can look around the web to see what you think. Also don't forget to make your OS partitions bigger if you plan on installing much other software.

Then do a fresh installation of both OS's. (you'll have to use some of the manual settings to get things to go into the partitions you've just made).

Use the Windows7 boot-loader for your finished dual-boot system! It is rock-stable and I've never had ANY problems with it.

When you install Ubuntu, make sure you place Grub (the Ubuntu boot-loader) on your Ubuntu partition, NOT the MBR (master boot record). Keep the Win7 boot loader on the MBR.

If you'd like to re-install the version of windows that comes with your computer, there is a way to make an install disc from a recovery partition. Sorry I can't recall how to do it anymore, but it does work. Also before you wipe out your original installation, use a free program like jellybean key-finder to grab all your software product keys (including windows of course!).

---

### Post by WasMeHere on 2011-10-01
hi jackyboy633,

We are many linux users that have done what you intend to do, and we have done it our own way. But basically there are some steps that all of us *should* have done.

0. Take your time and think about what you plan to do: *What do you need*? Use the input from this thread, there is good advice in the previous posts.

1. Backup images before and after

Make an image of the computer *before* you start your project. I like Clonezilla. Make another image of the computer *after* you finish your project. Keep them on an external hard disk (usb or esata).

2. Make a plan for your project.

3. Follow the plan in a systematic way. Make sure you understand what you do. This way you avoid problems and save time.
---
I would do something similar to *dave2001*

Have fun
Olle

---

### Post by roger_1960 on 2011-10-01
Hi

There is an option in the asus setup to create a recovery backup on an external drive (min 16GB). - you could use a USB key or USB external drive (but not an SD card) Suggest you read the manual and then use it.  It will create a recovery "disk"/USBkey which can boot from USB and reformat the whole of the hard drive to factory condition. 

Do this before you do anything else.

I installed 11.04 as a dual boot by erasing the recovery partition (the big empty one) and then using the "install alongside existing OS" option from the installer.

Regards

Roger

---

### Post by Mark Phelps on 2011-10-01
If you want the ability to restore your PC to the state it was in BEFORE you did the Ubuntu install, then I would second the recommendation to use Macrium Reflect.

When you run that, select ALL the partitions and back them off to an external drive.

Be sure to use the option to create a Linux boot CD.

Then, you can boot from that CD, attach the external drive containing the backup, and completely restore you netboook later -- should you need to do that.

---

### Post by jackyboy633 on 2011-10-01
Hello again.

I haven't actually got the netbook yet, since I was going to treat myself near Christmas. I'm going to be installing Ubuntu on its own (Ubuntu only), since I already have a recent Windows laptop (not a netbook). I'm not sure whether to use Clonezilla or the Asus utility that Roger_1960 recommended. The Asus one would take less space, but which one would be easier to restore from?

The reason I asked this question was because I wanted to know how to make a backup of Windows so if I ever need to send it back or Ubuntu goes AWOL (not that it will), I can use Windows for the time being. :D

Any suggestions will be good.

Jackyboy633.

---

### Post by dave2001 on 2011-10-01
> **jackyboy633 said:**
>  I'm not sure whether to use Clonezilla or the Asus utility 
Jackyboy633.

Well, I'd just use both. That way if one craps out on you, you've still got another option. You can never have too many backups! :)

---

### Post by dave2001 on 2011-10-01
On a side note, if you really want your netbook to fly like the wind you could try some different desktop environments. The default GNOME desktop is pretty good, but XFCE and LXDE have a much smaller draw on system resources. LXDE is lightning fast, but doesn't have quite as much eye-candy as XFCE. The Xubuntu and Lubuntu distributions use XFCE and LXDE respectively.

Of course if you want really pare things down, you can do a base-system install of Ubuntu and then grab whatever desktop environment you want straight from the repo's. (Probably not the best option if this is your first Linux experience).

---

### Post by jackyboy633 on 2011-10-02
I've been using Linux for two years now :) On a side note, I'll be using GNOME, since that's my preference.

---

