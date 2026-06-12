---
title: "Ubuntu 10.04.02 amd64 freeze problem"
date: 2011-05-03
forum: General Help
---

### Post by daniel-strae on 2011-05-03
Today im experiencing many freezing issues with my office desktop running lucid amd64.

Every application i run, seem to randomly freeze and then crash.. i dont understand wy, yesterday the pc worked as usual.

I was using kernel .38, i tryed to switch back to .32, but nothing change;

This is my apt history (some packages has been updated yesterday):

```

Start-Date: 2011-05-02  09:22:51
Upgrade: ubufox (0.9~rc2-0ubuntu11~mfs~lucid1, 0.9-0ubuntu1~mfs~lucid1), php5 (5.3.2-1ubuntu4.7, 5.3.2-1ubuntu4.8), python-dockmanager (0.1.1~bzr91-0~10.04~dockers1, 0.1.1~bzr94-0~10.04~dockers1), firefox-globalmenu (4.0+nobinonly-0ubuntu1~mfs~lucid1, 4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~lucid1), libapache2-mod-php5 (5.3.2-1ubuntu4.7, 5.3.2-1ubuntu4.8), php5-gd (5.3.2-1ubuntu4.7, 5.3.2-1ubuntu4.8), firefox-branding (4.0+nobinonly-0ubuntu1~mfs~lucid1, 4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~lucid1), firefox (4.0+nobinonly-0ubuntu1~mfs~lucid1, 4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~lucid1), xulrunner-1.9.2 (1.9.2.16+build1+nobinonly-0ubuntu0.10.04.1, 1.9.2.17+build3+nobinonly-0ubuntu0.10.04.1), xul-ext-ubufox (0.9~rc2-0ubuntu11~mfs~lucid1, 0.9-0ubuntu1~mfs~lucid1), dockmanager (0.1.1~bzr91-0~10.04~dockers1, 0.1.1~bzr94-0~10.04~dockers1), ubuntu-tweak (0.5.10-1~maverick1, 0.5.12-1~lucid1), php5-mysql (5.3.2-1ubuntu4.7, 5.3.2-1ubuntu4.8), php5-cli (5.3.2-1ubuntu4.7, 5.3.2-1ubuntu4.8), php5-common (5.3.2-1ubuntu4.7, 5.3.2-1ubuntu4.8), firefox-gnome-support (4.0+nobinonly-0ubuntu1~mfs~lucid1, 4.0.1+build1+nobinonly-0ubuntu0.11.04.1~mfs~lucid1)
End-Date: 2011-05-02  09:23:36

```I dont see any packages that can cause this error.
The freezes seem to be related to the hard disk: if i try to copy/download large files, the freezes happen instantly; but i've tryed Smart test from disk utility, and GSmart from a live cd: the hard disk seem to be ok.

Even memtest doesnt report any error.

What can i do?

---

### Post by hgernhardt on 2011-05-03
Daniel—

> **daniel-strae said:**
> The freezes seem to be related to the hard disk: if i try to copy/download large files, the freezes happen instantly; but i've tryed Smart test from disk utility, and GSmart from a live cd: the hard disk seem to be ok.


Silly question, but have you performed a manual fsck on all your partitions?  If not, give it a shot and see what comes up.  Also, I'm not sure if the kernel ring buffer will record failure messages from the hard drive or not, so you may want to try tailing /var/log/messages during a failure scenario to see whether or not the HDD is reporting trouble.

While you're at it, you may want to check (with the power off) the physical security of the cable connections between motherboard, power supply, and HDD.  Disconnecting and reconnecting these physical connections may help matters some (it has for me in the past).

Oh, and if you haven't backed up your data recently, ***DO SO NOW***.  I see the *worst-case* scenario being an HD replacement.

---

### Post by daniel-strae on 2011-05-03
> **hgernhardt said:**
> Daniel—



Silly question, but have you performed a manual fsck on all your partitions?  If not, give it a shot and see what comes up.  Also, I'm not sure if the kernel ring buffer will record failure messages from the hard drive or not, so you may want to try tailing /var/log/messages during a failure scenario to see whether or not the HDD is reporting trouble.

While you're at it, you may want to check (with the power off) the physical security of the cable connections between motherboard, power supply, and HDD.  Disconnecting and reconnecting these physical connections may help matters some (it has for me in the past).

Oh, and if you haven't backed up your data recently, ***DO SO NOW***.  I see the *worst-case* scenario being an HD replacement.

Thanks for you reply hgernhardt!
I'll try fsck now.
I'll even try to do another bopy of big files monitoring /var/log/messages as you suggested, hope somethings come up.

I have to say that this kind of problem arent new tho this desktop; It was of a my collegue that have to format it about every 6 months becose an disk write error, but he was running Windows Seven so i thought the problem was S.O. related (i put a new hard-disk when taking the pc and installing ubuntu).. can some mainbord issue cause this problem over time?
Im using this pc from less than 1 month..

I'll do my test and come back with results.

---

### Post by frogotronic on 2011-05-03
Is this a desktop or a laptop?

If a desktop, it might be your IDE cable from your MOBO to your HDD.

- CH

---

### Post by daniel-strae on 2011-05-03
> **cement_head said:**
> Is this a desktop or a laptop?

If a desktop, it might be your IDE cable from your MOBO to your HDD.

- CH

Its a desktop, but the HD is a sata: ATA WDC WD5000AADS-00S9B0

Nothing from /var/log/messages, I reboot and try fsck.

---

### Post by hgernhardt on 2011-05-03
> **daniel-strae said:**
> I have to say that this kind of problem arent new tho this desktop; It was of a my collegue that have to format it about every 6 months becose an disk write error, but he was running Windows Seven so i thought the problem was S.O. related (i put a new hard-disk when taking the pc and installing ubuntu).. can some mainbord issue cause this problem over time?

Okay, scratch what I was about to write.  Another poster came up with this solution:  next step, replace cables.  This should be your first hardware level test.  If replacement of cables doesn't work, then you need to start looking at component-level testing.  My experience with this kind of troubleshooting involves simply replacing things.  Remember:  if you have to replace the motherboard, make sure it is an ***exact duplicate*** of the motherboard currently in the machine.

Good luck!

---

### Post by daniel-strae on 2011-05-03
> **hgernhardt said:**
> Okay, scratch what I was about to write.  Another poster came up with this solution:  next step, replace cables.  This should be your first hardware level test.  If replacement of cables doesn't work, then you need to start looking at component-level testing.  My experience with this kind of troubleshooting involves simply replacing things.  Remember:  if you have to replace the motherboard, make sure it is an ***exact duplicate*** of the motherboard currently in the machine.

Good luck!

This machine has been in maintenance from the vendor two times, and both the times the problem comes up after ~6 month (on windows), and now seems affecting me on ubuntu... the vendor say the last time changed completely the mainboard.. but i have some doubt they did.

Anyway, this is my fsck (on natty live):

```

#Filesystem, ext4
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda1: clean, 610315/29786112 files, 60119061/119124736 blocks

#Swap, extended + swap
ubuntu@ubuntu:~$ sudo fsck /dev/sda2
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2
Could this be a zero-length partition?
ubuntu@ubuntu:~$ sudo fsck /dev/sda5
fsck from util-linux-ng 2.17.2
fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sda5

```
Note i installed with the automatic ubuntu procedure (erase entire disk.. hey, 12Gb of swap looks a bit overkill for me!)

I try to change the cables, but my feelings is that the problem compromised the hard disk: while in windows, after a format'n'reinstall the system work great (..for awhile)...

Looks like i have to change pc and resintall all from the begin...

---

### Post by hgernhardt on 2011-05-03
For what it's worth, the Errors on fsck make sense considering it's trying to use e2fsck on a swap partition.  I tend to doubt that the HDD has been toasted unless you have some sort of funky BIOS virus that toasted it.  You might be able to try flashing the BIOS.  I'm seriously doubting that the problem is in software, or even firmware.  I'm thinking hardware, and now I'm starting to think it might be the power supply based upon what you're saying.  If that's the case, you're probably looking at *another* mobo replacement as well.

If you're looking at another vendor service call, and the machine isn't still under warranty or otherwise covered by service agreement, you should most likely replace the machine.  What's valuable is the data, not the hardware.  The time and trouble it's taking to hunt down and repair this issue is more than worth the cost of a new box.

Oh, and when you do replace it, make sure you don't get the same make and model.  You may simply have one bad box out of the bunch, but why tempt fate?

Good luck!

---

### Post by daniel-strae on 2011-05-03
I guess the HD data are compromised becose if format and reinstall everythings, the pc works well for 1 month (~6 on windows, but i have a more intensive use of the hd, while my collegue used to have the base data upon an ethernet disk over the lan)

Im not an hardware expert and neither a software one, but looks like there is something that affect how data get written/read on the disk, causing in 'long time' a disk failure.

---

### Post by daniel-strae on 2011-05-04
Just bought a new pc :P

The strange thing is that now i've put the hd into another pc to backup the data, and the transfer is going quite good, seems like the hd (and data within) are not compromised...

But this raise another question: so why if i format the pc again, it works great for 1-2 months?

---

### Post by bcschmerker on 2011-06-22
> **daniel-strae said:**
> Just bought a new pc :P

The strange thing is that now i've put the hd into another pc to backup the data, and the transfer is going quite good, seems like the hd (and data within) are not compromised...

But this raise another question: so why if i format the pc again, it works great for 1-2 months?What chipset is in your mobo?  [Intel®](http://www.intel.com/) had to recall several chipsets for LPGA 1155 due to an issue with SATA degredation over time, since fixed with the B3 steppings of the P61, P67, H67, Z68, and others.

---

