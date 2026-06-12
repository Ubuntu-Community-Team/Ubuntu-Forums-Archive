---
title: "Help!!!!!!!!!!!!!"
date: 2010-11-01
forum: General Help
---

### Post by stefanm91 on 2010-11-01
how to recover files on Ubuntu, I had win 7 before Ubuntu and I accidentaly formated my hard drive.........PLEASE HELP!!!!!

---

### Post by papibe on 2010-11-01
I think we need more details to offer you some help.

Did you install Ubuntu in your Win7 machine, right?

Are you concern how to recover files you deleted in Ubuntu? or

Did you lost the ability to boot to Windows?

Did you loose your Windows files?

Regards.

---

### Post by t0p on 2010-11-01
I take it you mean that you reformatted the whole drive, so now you have Ubuntu installed and the Win7 partition has been over-written?

Sorry to be the bearer of bad news, but I don't think there's anything you *can* do about it.  But there *may* be file retrieval software available that can do it.  So, the first thing you need to be told is: *do NOT write anything to that hard drive*.  This means, don't boot into your new Ubuntu installation.

Instead, use your Ubuntu installation CD to run Ubuntu as a live session - ie, insert the CD, reboot the machine so it boots from the live CD and choose the option to try Ubuntu without installing it.

Next, go to **System > Administration > Synaptic Package Manager**, click on Search, and do a search for "file retrieval" or "file recovery".  Synaptic will present you with a list of file recovery software available.

I don't know which package you should install.  Sorry; maybe someone else can suggest something?  But I will emphasize again: do NOT do anything to write to that hard drive or you risk over-writing your Win7 data and possibly losing it forever.

Good luck.

---

### Post by Mark Phelps on 2010-11-01
Actually, anytime you overwrite any partition with something else, the more you use the "something else", the poorer the chances of recovering the original information.

Installing any app to an Ubuntu system that overwrote Win7 (if that IS what happened) is only going to worsen chances of recovery, not improve them.

Best course of action is to (1) remove the affected drive from the PC, (2) obtain a second PC and on THIS one, install file recovery software, (3) hook up the original drive as an external drive to the second PC and run file recovery against the original drive.

---

### Post by crypto2600 on 2010-11-01
Hey there.

Another option for partial or total partition recovery is "testdisk". Boot up with a Live distro, then apt-get install testdisk and check for instructions online how to use it. It's a bit complex, but one of the most effective apps for this task

---

### Post by HiImTye on 2010-11-01
if you installed Ubuntu that means you likely installed an ext filesystem which means instead of just globbing things on any available block, randomly, your files are placed in the largest consecutive free space so likely most of or all of your original files are completely gone.

your FAT/NTFS tables are also gone making recovering data from the disk harder

it is likely that your files are irrecoverable. sorry to tell you.

now that all of that is out of the way, there may be some good news. you *may* have the ability to recover some or all of your files if you are careful and do as little writing to the disk as possible.

first off, boot a Live CD. as soon as you are booted in, go to the menu and navigate to accessories > terminal. type in the terminal
```
swapoff
```
this will tell the OS to not write to the hard disk for swap usage. now you may install programs to ram.
open up synaptic package manager or the ubuntu software center, whichever you feel more comfortable with. they each have their own strengths and weaknesses. while synaptic is much more powerful, the software center is much more user friendly. search for some recovery software in here.

best of luck!

---

