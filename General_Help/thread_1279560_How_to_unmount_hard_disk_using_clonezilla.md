---
title: "How to unmount hard disk using clonezilla"
date: 2009-10-01
forum: General Help
---

### Post by wailerc on 2009-10-01
I have just swiched from MS to Ubuntu and want to make a disk image of my current hard drive using clonezilla. When I run clonezilla Live, it won't let me make an image of the hard drive disk because it is mounted. How do I unmount the hard drive on the machine that I want to clone with the clonezilla CD in it? So, I want to use clonezilla to make an image on the machine and save it my USB drive to restore other identical computers? I am new to Ubuntu and hence linux, so I need careful instructions on how to use the terminal window in clonezilla to unmount my hard drive so I can make an image of it.
 
I have a working clonezilla CD working fine, I just do not know how to clone the internal hard drive on the machine I am running the clonezilla cd from.
 
Thanks

---

### Post by rbc on 2009-10-01
After the computer boots to CD, you will get a window about choosing the correct language, then an option about “keymap”. Choose “Don’t touch keymap”. The next window should be 
Start Clonezilla (or)
Enter shell

Choose the second option (Enter shell). Once you have gotten to terminal, type this command to see what is mounted
mount

Find the partition you want to unmount. For example, it is sda1, so type this command:
sudo umount /dev/sda1

It should now be umounted, so to restart Clonezilla, type these command consecutively:
sudo su
clonezilla

Please be aware of which drive is which, so that you are not cloning your empty drive to the one that Ubuntu is on

---

### Post by wailerc on 2009-10-01
Thanks for the   input. I followed your instructions but was unsuccessful. But as I stated before; I am a newbie to this world of Linux. When I booted from the clonezilla CD, the options given to me after the language and keymap options are as follows:

[0] continue to start x-window automatically to use drbl live
[1] run "forcevideo-drbl-live" to configure x-window by your self
[2] enter command-line prompt to configure x-window by yourself.

I tried all options. I followed your instructions to choose the second one, but  [2] on my computer [2] seemed to fit your request best. When I entered 2, this is what I saw,

root@debian:/# and when I typed mount, it showed only the live directories, not anything from my computer. I restarted and booted up ubuntu, went into the terminal and types the command mount and did see my hard drive that I want to clone as :
braves@braves-desktop: /dev/sda1

Sorry, but how do I navigate to my computer from clonezilla (debian) to unmount my hard drive so  can clone it? I am a high school teacher trying to get my lab up and running. My district techs do not know linux and are making me set up my own computers. I have 100 computers to setup and want to clone instead installing individually.

Many Thanks!

> **rbc said:**
> After the computer boots to CD, you will get a window about choosing the correct language, then an option about “keymap”. Choose “Don’t touch keymap”. The next window should be 
Start Clonezilla (or)
Enter shell

Choose the second option (Enter shell). Once you have gotten to terminal, type this command to see what is mounted
mount

Find the partition you want to unmount. For example, it is sda1, so type this command:
sudo umount /dev/sda1

It should now be umounted, so to restart Clonezilla, type these command consecutively:
sudo su
clonezilla

Please be aware of which drive is which, so that you are not cloning your empty drive to the one that Ubuntu is on

---

### Post by rbc on 2009-10-01
You got me stumped. Clonezilla is not mounting the partition you want but complains about copying it because it is mounted? What exactly is the error? And while we’re at it, let’s narrow down what you are actually trying to do. Cloning is, usually, copying one entire hard drive (sda) to another hard drive (sdb). One makes an image of a partition (sda1). It can be one big file, or broken up in chunks. You save it somewhere, and then use Clonezilla to port it to a pre-made partition. To image a partition, it obviously needs to be mounted. Which of these are you trying to do? Maybe post back with each step you are doing and/or try a different version of Clonezilla.
[http://partedmagic.com/download.html](http://partedmagic.com/download.html)
Download this and try the Clonezilla that this suite has. PartedMagic also has many other tools you will come to love, at least I hope so, since this encounter with Clonezilla has not seemed pleasant so far

---

### Post by louieb on 2009-10-01
Sounds like you got the server version of [Clonezilla]("http://www.clonezilla.org/"). Believe you need the Live CD version. **rbc** is right on suggesting getting a  [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic") Besides Clonezilla it has other useful stuff.

---

### Post by Casburn on 2009-10-09
I tried your suggestion to run Clonezilla Live instead of the Clonezilla Server and it worked! I have an image of sda1. However, I must have somehow installed the Ubuntu on my hard drive dev/sda instead of dev/hda? When I try clone 7 computers using the Clonezilla server over a network, it initially appears to run but then I get a failed dev/sda fail or dev/hda fail . What did I do wrong when I installed Ubuntu on the machine I want to clone? I thought the drive location should have path dev/hda as I only have one 19.8 GB  hard drive in the computer.

Thanks,

> **wailerc said:**
> Thanks for the   input. I followed your instructions but was unsuccessful. But as I stated before; I am a newbie to this world of Linux. When I booted from the clonezilla CD, the options given to me after the language and keymap options are as follows:

[0] continue to start x-window automatically to use drbl live
[1] run "forcevideo-drbl-live" to configure x-window by your self
[2] enter command-line prompt to configure x-window by yourself.

I tried all options. I followed your instructions to choose the second one, but  [2] on my computer [2] seemed to fit your request best. When I entered 2, this is what I saw,

root@debian:/# and when I typed mount, it showed only the live directories, not anything from my computer. I restarted and booted up ubuntu, went into the terminal and types the command mount and did see my hard drive that I want to clone as :
braves@braves-desktop: /dev/sda1

Sorry, but how do I navigate to my computer from clonezilla (debian) to unmount my hard drive so  can clone it? I am a high school teacher trying to get my lab up and running. My district techs do not know linux and are making me set up my own computers. I have 100 computers to setup and want to clone instead installing individually.

Many Thanks!

---

