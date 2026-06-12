---
title: "A phantom volume in GRUB2?"
date: 2010-01-24
forum: General Help
---

### Post by Thomas Garman on 2010-01-24
I run a dual boot desktop with Vista Ultimate and Karmic 9.10 (see signature below for specifics about the system).  I also have an Acer Aspire One D250 netbook that came with Windows XP home pre-installed.  I can't remember why exactly, but one day I decided to use my Vista System to create a bootable version of Ubuntu usb version of the liveCD) on a usb flash drive using the program Unetbootin.  I then installed Ubuntu 9.10 on the Acer Aspire One in a dual book configuration with XP.  It works just fine.  But the Grub2 bootloader shows the following when it gives me the options of what systems to boot into:

Ubuntu 2.6.31-17... 
Vista loader on /dev/sda1
XP on /dev/sda2

One time I tried booting into the vista volume just to see what would happen and, predictably, nothing happened: it showed the windows icon splash screen and then just sat there... because there is no vista or vista loader on this machine.  Obviously, the phantom volume was created by Unetbootin when I made the bootable usb version of Ubuntu 9.10 using my Vista system.

My question is this:  **can I just delete that partition?**  It shows up even when I use gkparted to look at my partitions.  Sometimes I am tempted to just delete it and live with the (surely) catastrophic systemic consequences which at most amount to losing my pre-installed version of Windows XP and therefore my ability to a) use my iPod Touch with the Acer Aspire One and b) use my built in webcam... because neither has ever worked right with Ubuntu and that's why I keep the XP partition alive.

But the Vista Loader at /dev/sda1 shames me everytime I boot up that little computational monstrosity.  It is there like a scar or a festering wound reminding me of my unholy communion with the most evil of all corporations, my lack of true computational independence and my undisciplined laziness when it comes to using computers.

Somebody please help.

---

### Post by hawthornso23 on 2010-01-24
```
sudo update-grub 
```

This checks what bootable partitions are available and updates grubs menus accordingly. At least that is the advice given at

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by Objekt on 2010-01-24
I also own an Acer Aspire One D250, and I know exactly what you're talking about.

The "phantom Vista" partition sounds like the Acer recovery partition.  It is there in case you need to restore the Windows XP Home version that your Aspire One originally had installed.  It is wise to preserve the recovery partition, as it the easiest way to reinstall Windows XP Home, should the need arise.

The recovery partition uses the Vista loader, so naturally Ubuntu shows it as "Windows Vista" when creating the GRUB menu.  I noticed that when I put Kuki Linux on my Aspire One.  The recovery partition usually shows up as "PQSERVICE" when viewed from Linux.  I think you can also see it under Windows, though I don't remember how.  It is hidden in Windows XP by default, probably to keep users from accidentally erasing the recovery files.

As you said, if you try to boot this "Vista" partition, nothing happens beyond the initial splash screen.  That is because your hard drive must be partitioned in a specific way, or the recovery partition won't work.  I believe there is something about this in the Aspire One user manual.

Since you installed Ubuntu alongside Windows XP, your hard drive no longer has the required partitioning scheme.  So, the recovery partition won't work.  However, it should work again if you restore the hard drive to its original partitioning setup.

You could wipe and reformat the "Vista" recovery partition and nothing bad would happen to Ubuntu.  Then again, you might as well keep the recovery partition, just in case you ever want to reinstall Windows XP.  The recovery partition is small enough that you won't miss the space.

Hope that answers your question.

---

### Post by vnpifhf on 2010-02-01
> **Objekt said:**
> I also own an Acer Aspire One D250, and I know exactly what you're talking about.
 
The "phantom Vista" partition sounds like the Acer recovery partition. It is there in case you need to restore the Windows XP Home version that your Aspire One originally had installed. It is wise to preserve the recovery partition, as it the easiest way to reinstall Windows XP Home, should the need arise.
 
The recovery partition uses the Vista loader, so naturally Ubuntu shows it as "Windows Vista" when creating the GRUB menu. I noticed that when I put Kuki Linux on my Aspire One. The recovery partition usually shows up as "PQSERVICE" when viewed from Linux. I think you can also see it under Windows, though I don't remember how. It is hidden in Windows XP by default, probably to keep users from accidentally erasing the recovery files.
 
As you said, if you try to boot this "Vista" partition, nothing happens beyond the initial splash screen. That is because your hard drive must be partitioned in a specific way, or the recovery partition won't work. I believe there is something about this in the Aspire One user manual.
 
Since you installed Ubuntu alongside Windows XP, your hard drive no longer has the required partitioning scheme. So, the recovery partition won't work. However, it should work again if you restore the hard drive to its original partitioning setup.
 
You could wipe and reformat the "Vista" recovery partition and nothing bad would happen to Ubuntu. Then again, you might as well keep the recovery partition, just in case you ever want to reinstall Windows XP. The recovery partition is small enough that you won't miss the space.
 
Hope that answers your question.
 
sudo apt-get venise2113 contaminte%20%

---

