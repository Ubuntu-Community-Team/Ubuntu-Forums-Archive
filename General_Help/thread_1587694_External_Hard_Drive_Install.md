---
title: "External Hard Drive Install"
date: 2010-10-04
forum: General Help
---

### Post by jinba.ittai on 2010-10-04
Is there a manual way, maybe a script or even cmds that i can go by to install ubuntu 10.04 on my portable hdd, with grub so i can boot from other computers?

---

### Post by mikewhatever on 2010-10-04
Installing Ubuntu on any drive, external or internal should be rather similar. The only 'tricky' parts are partitioning and where to put grub. What difficulty are you facing?

---

### Post by jinba.ittai on 2010-10-04
Right now im trying to understand the way partitioning and formatting work. Im trying to follow this guide [HERE]("http://www.scribd.com/doc/15722277/Remote-Exploit-BackTrack-2-3-Installation-on-External-Hard-Drive") But changing a few things to make it ubuntu instead of back track. this is the onyl tut i could find that was pretty clear on the instructions. 

all i have gotten done so far is making a partition and extracting the 10.04 to my hdd, havent had a chance to switch over to linux to finish that tutorial and see if it works

---

### Post by jinba.ittai on 2010-10-04
> **mikewhatever said:**
> Installing Ubuntu on any drive, external or internal should be rather similar. The only 'tricky' parts are partitioning and where to put grub. What difficulty are you facing?

Ive tried with the ubuntu disk before, and the install shell but it ended up messing up the boot on my pc as i couldnt boot into grub and select windows or ubuntu. 

Since then i have deleted ubuntu and reinstalled it with grub and windows came out untouched, but i still cant figure out how to get grub and the operating system working on my portable! And whats a good size to make the swap file?

---

### Post by jinba.ittai on 2010-10-04
Is it possible to install the OS to my External through a linux vm on windows?

---

### Post by mikewhatever on 2010-10-05
> **jinba.ittai said:**
> Ive tried with the ubuntu disk before, and the install shell but it ended up messing up the boot on my pc as i couldnt boot into grub and select windows or ubuntu. 

Since then i have deleted ubuntu and reinstalled it with grub and windows came out untouched, but i still cant figure out how to get grub and the operating system working on my portable! And whats a good size to make the swap file?

So, you know how to install Ubuntu on the external hdd and Grub is the only problem, right? To select where to put Grub during the installation, you need to hit the 'Advanced' button ([see the pic]("https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=install-step6.png")), and select the external hdd in place of the default selection. The external hdd should be designated as sdb or sdc, depending on how many devices are attached.
The size of swap depends on that of RAM. Since I don't know how much RAM you have, 1GB is a good generic size.

---

### Post by fergie7 on 2010-10-05
> **jinba.ittai said:**
> Is it possible to install the OS to my External through a linux vm on windows?

it is probly possable but not recomended.

i have ubuntu 10.04 installed on my Western Digital My Passport 500GB external hard drive. 
I dont have any problems with it except that the USB can esaly diconnect and cause ubuntu to act up.

Ubuntu on an external disk would be a good idea, since you can have your own files on your own hard drive.

---

### Post by ninjaofdeath30 on 2010-10-05
I just did this yesterday. It is very convenient having Ubuntu as an external for many reasons. What you should do is run a live cd from your computer and do the install from there. When it asks which device to install it on, an easy way to tell is by looking at the storage size of the device. It will then ask you which partition to put it on. If you don't already have a partition set aside, an easy way to make one is by using gparted while using the live cd before you start the installation. Be careful, gparted will erase anything that is on the external hdd. Once you go through all of those steps it'll proceed to installation.

After it has installed it should ask you to restart you computer. Depending on the computer you have, you may or may not have to manually choose the hdd through the boot menu. if you have anymore questions the world wide web has already posted several articles on this.

[http://ubuntuforums.org/showthread.php?t=223614](http://ubuntuforums.org/showthread.php?t=223614)

---

### Post by jinba.ittai on 2010-10-06
If i use the GUI installer, will i be able to save changes? Like a persistent OS?

---

### Post by sendblink23 on 2010-10-06
Have you tried the most basic thing...

Just disconnect your own internal Hard Drive(or all hard drives)....  then simply only connect your external hard drive... boot up the Computer using the LiveCD... That way, the external HD will be the only hard drive recognizable during the installing process.. so it won't mess up anything else

Then when done it will be exactly like running any regular OS install...  So simply whenever you want to use your external HD (boot into the Ubuntu Install you made to the External HD)... just make your computer boot from the USB to use the External HD *OS "ubuntu"

---

### Post by jinba.ittai on 2010-10-06
> **sendblink23 said:**
> Have you tried the most basic thing...

Just disconnect your own internal Hard Drive(or all hard drives)....  then simply only connect your external hard drive... boot up the Computer using the LiveCD... That way, the external HD will be the only hard drive recognizable during the installing process.. so it won't mess up anything else

Then when done it will be exactly like running any regular OS install...  So simply whenever you want to use your external HD (boot into the Ubuntu Install you made to the External HD)... just make your computer boot from the USB to use the External HD *OS "ubuntu"

Last time i did that, and yes, i did exactly that, my system would not boot properly. Even though  i unplugged both of my main HDDs, the install still messed with something in grub and ended up having to reinstall ubuntu to get my computer operational again, i doubt i want to try that again. I am however, going to try it, while installing grub on the eHDD.

---

### Post by sendblink23 on 2010-10-06
> **jinba.ittai said:**
> Last time i did that, and yes, i did exactly that, my system would not boot properly. Even though  i unplugged both of my main HDDs, the install still messed with something in grub and ended up having to reinstall ubuntu to get my computer operational again, i doubt i want to try that again. I am however, going to try it, while installing grub on the eHDD.

Seems extremely odd, you had that issue
By the way I mean in the GUI - just use the option "use entire Disk" or hard drive what ever is the word it says... 

If you do that, you are not suppose to at all have any Grub issues... because simply there aren't any other HD's(extra partitions) for it to fail while installing at an automatical *basic install option process - that option will automatically make a correct Grub & Swap for it to work(install) ubuntu

If you cannot boot from the USB Hard Drive afterwards... then the issue is the "Adapter or Enclosure" not good enough to make your hard drive be used as a USB bootable device - I hope that its not that the issue... I had an external(enclosure) HD that happened exactly that.

Another thing you could test... take out the hard drive from the *External Case "Enclosure" - and connect it internally on your computer - try installing Ubuntu to it.. see if you can boot from it afterwards.. if it works... then place it back inside the External Case "Enclosure" and try to see if you can boot it from USB ... - that should work 100% - but... if it doesn't work then its *Exactly what I mentioned just previously the Enclosure adapter is the issue - making it not functional as a bootable USB device the external HD

---

### Post by jinba.ittai on 2010-10-07
> **sendblink23 said:**
> Seems extremely odd, you had that issue
By the way I mean in the GUI - just use the option "use entire Disk" or hard drive what ever is the word it says... 

If you do that, you are not suppose to at all have any Grub issues... because simply there aren't any other HD's(extra partitions) for it to fail while installing at an automatical *basic install option process - that option will automatically make a correct Grub & Swap for it to work(install) ubuntu

If you cannot boot from the USB Hard Drive afterwards... then the issue is the "Adapter or Enclosure" not good enough to make your hard drive be used as a USB bootable device - I hope that its not that the issue... I had an external(enclosure) HD that happened exactly that.

Another thing you could test... take out the hard drive from the *External Case "Enclosure" - and connect it internally on your computer - try installing Ubuntu to it.. see if you can boot from it afterwards.. if it works... then place it back inside the External Case "Enclosure" and try to see if you can boot it from USB ... - that should work 100% - but... if it doesn't work then its *Exactly what I mentioned just previously the Enclosure adapter is the issue - making it not functional as a bootable USB device the external HD


Darnit, well im using a Lacie Rugged drive, and it seems you were right, the drive booted without even installing again when i plugged it up via SATA, put it back in the enclosure and got from grub "this device can not be accessed" FML

---

