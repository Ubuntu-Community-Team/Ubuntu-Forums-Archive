---
title: "dual boot"
date: 2012-01-10
forum: General Help
---

### Post by greenman55 on 2012-01-10
hey, still trying new stuff and needed some help. any one know how to dual boot ubuntu 11.10 and ubuntu LTS (10.04) with 2 separate hard drives? if so please help me im really new :(

---

### Post by Bucky Ball on 2012-01-10
Install one on one hard drive and the other on the other! Update grub and then pick the install you want to use at boot (is the simple answer). There is no real trick to this (unlike dual-booting with installing Windows second).

---

### Post by pbpersson on 2012-01-10
The most complicated part is paying attention to what it is doing with the hard drives.  In other words, when you install the first OS it will probably choose one hard drive and assume that you want it to use the entire drive for the OS.  The second OS you install might automatically choose the second hard drive but I suspect it will want to replace the OS you have already installed.  You might have to choose the "manual partition configuration" and tell it that you wish to install on the second hard drive.

However, that is about as complicated as it gets.  Other than that, it should be a breeze.  I would install the older OS first if I were you.

---

### Post by Double.J on 2012-01-10
> **greenman55 said:**
> hey, still trying new stuff and needed some help. any one know how to dual boot ubuntu 11.10 and ubuntu LTS (10.04) with 2 separate hard drives? if so please help me im really new :(

How are the hard drives connected? if one of them is on USB, this is where 10.04 should go - 11.10 seems to fail to install on my USB HDDs


Basically the system is 

1) Go through the install process for 11.10 (as this isn't a more stable lts release, it's best practice to install it first, so that the lts manages the boot process) as you want to use all the drive just using the default install options will b fine.The only change you may want to make is where to install the drive. Your primary 2 drives (if internal) should come up as /dev/sda and /dev/sdb - make a note of which you're installing to. It should take around half hour.

2) once complete, run again, this time with 10.04 it's all much the same as before - just pay special attention to the install location, Ubuntu may want to shrink the last install and put itself on the same drive by default - don't let it do this. choose the other drive and full disk install. the installation of this install's boot-loader should configure the boot process just fine.

If you'd like some more info on best practice partitioning of your hard drives check out [Bodhi Zazen's how to]("http://ubuntuforums.org/showthread.php?t=282018")
 
All the best

Enjoy ubuntu!

---

### Post by Bucky Ball on 2012-01-11
Yea, and if done via the process described by gnu/mirow the 10.04 install will now be controlling the boot process (as it will have its grub), not the 11.10 install. 

This can be confusing so make sure you know which install's grub is controlling things at boot. ;)

I have a few OSs/releases installed and the one installed *last* is the grub being used generally (unless there is a way to prevent it installing grub during installation, which I'm unsure of but someone else may be, or you change things manually after install).

---

### Post by Mark Phelps on 2012-01-11
I've got different Ubuntu versions installed, each on its own physical drive, and the process I use is similar to what's already been said:
1) Have only ONE drive connected at a time
2) Install each Ubuntu version to its own drive
3) Reconnect all the drive
4) Boot from the Ubuntu drive I want to use most of the time
5) Run "sudo update-grub".

Now, when I boot, I get a GRUB menu listing all of the drives.

---

### Post by oldfred on 2012-01-11
While Mark Phelps's suggestion of disconnecting drive is the absolute safest way, I hate opening case and removing connections. I have yet to open case without accidentally bumping something and spending time finding what I did.

I always partition in advance, use manual install and use the combo box on which drive's MBR to install grub2's boot loader into. But I have done it so many times that I have clicked though too fast and installed to sda (the normal default) when I did not want to. But reinstall of  a boot loader once you have done it once or twice is not difficult.

Install to external drive 11.04.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

---

