---
title: "Simply: Ubuntu 9.10 to Vista?"
date: 2012-04-26
forum: General Help
---

### Post by simov on 2012-04-26
Hello,

After two and a half fantastic years of using Ubuntu 9.10 on my laptop for university, it's time to say goodbye and hand it down (after purchasing a newer laptop) to my father, an engineer who has been using Windows for work since, well, Windows was around. 

I would really prefer avoiding the headache of going through all the threads describing different situations because I've gone through quite a few for the past hour and haven't found something that has quite worked for me, unless someone will be so kind as to direct me to a very simple explanation of the easiest way to uninstall Ubuntu and re-install Windows Vista from the reinstallation CD that was provided with my Dell. I need this one dumbed down for me - exam time has fried my brain and I really need to relax!

I have since lost my Ubuntu start up CD and cannot follow through with the steps posted on a few of these threads.

**My situation:** When I run the Vista start-up, I click "Install Now". After waiting for a minute, a window pops up saying, "This computer does not have enough space for temporary files. Windows installation needs at least 460 MB of space on any partition for temporary files. To install Windows, free enough space and restart the installation. Error code: 0x80004005."

Anybody? ](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)

Thank you in advance!

---

### Post by techsupport on 2012-04-26
> **simov said:**
> Hello,

After two and a half fantastic years of using Ubuntu 9.10 on my laptop for university, it's time to say goodbye and hand it down (after purchasing a newer laptop) to my father, an engineer who has been using Windows for work since, well, Windows was around. 

I would really prefer avoiding the headache of going through all the threads describing different situations because I've gone through quite a few for the past hour and haven't found something that has quite worked for me, unless someone will be so kind as to direct me to a very simple explanation of the easiest way to uninstall Ubuntu and re-install Windows Vista from the reinstallation CD that was provided with my Dell. I need this one dumbed down for me - exam time has fried my brain and I really need to relax!

I have since lost my Ubuntu start up CD and cannot follow through with the steps posted on a few of these threads.

**My situation:** When I run the Vista start-up, I click "Install Now". After waiting for a minute, a window pops up saying, "This computer does not have enough space for temporary files. Windows installation needs at least 460 MB of space on any partition for temporary files. To install Windows, free enough space and restart the installation. Error code: 0x80004005."

Anybody? ](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)

Thank you in advance!

You would need a live bootable disc of Ubuntu. You would need to run Gparted to remove the paritions and create a new NTFS formatted parition for the entire drive. 
Then you will be able to install Vista again.

---

### Post by Bucky Ball on 2012-04-26
> **techsupport said:**
> You would need a live bootable disc of Ubuntu. You would need to run Gparted to remove the paritions and create a new NTFS formatted parition for the entire drive. 
Then you will be able to install Vista again.

... or a Gparted CD. 

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

You don't need to format the drive with anything (and you may not want the entire drive = 1 partition). Just delete Ubuntu partitions with Gparted, leaving free space, and create partitions for Windows when you're installing Windows. Simple.

---

### Post by simov on 2012-04-27
> **Bucky Ball said:**
> ... or a Gparted CD. 

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

You don't need to format the drive with anything (and you may not want the entire drive = 1 partition). Just delete Ubuntu partitions with Gparted, leaving free space, and create partitions for Windows when you're installing Windows. Simple.

Great! Silly question - I've downloaded gparted - Am I copying this to a CD?

---

### Post by Mark Phelps on 2012-04-27
> **simov said:**
> Great! Silly question - I've downloaded gparted - Am I copying this to a CD?

If you downloaded the application, that will do you no good.

You have to download the ISO image file and BURN that image to CD.  That will make a bootable CD, which you then boot from, to run GParted.

Sorry if that was not made clear.

---

### Post by mode7 on 2012-04-27
If you have a USB drive, use Unetbootin to easily burn an ISO of Ubuntu or Parted Magic onto the drive, then boot off of that.

---

### Post by Bucky Ball on 2012-04-28
> **simov said:**
> Great! Silly question - I've downloaded gparted - Am I copying this to a CD?

As mentioned, download the ISO, make a CD or USB to boot from, boot from that and you're away ...

---

### Post by Zukaro on 2012-04-28
You should be able to delete the partitions from the drive when installing Vista.  If you need a command prompt press Shift F10 while in the installer (I don't know any commands for formatting hard drives and such however; but if you're unable to delete the partitions/format the drive then there's a command called cleandisk or something like that (not sure exactly) but basically it fixes that error (or should)).

---

### Post by Cheesemill on 2012-04-28
> **Zukaro said:**
> You should be able to delete the partitions from the drive when installing Vista.  If you need a command prompt press Shift F10 while in the installer (I don't know any commands for formatting hard drives and such however; but if you're unable to delete the partitions/format the drive then there's a command called cleandisk or something like that (not sure exactly) but basically it fixes that error (or should)).
I don't think this is any use to the OP.

He is using a recovery disk, not a normal Windows installation disk.

---

### Post by Zukaro on 2012-04-28
Oh.  Well in that case I don't know.  :P
(*has never used a Windows recovery disk*)

The only thing I can think of in that case is what's already been suggested (using Gparted).

---

