---
title: "Setting up Partitions? Ubuntu/windows"
date: 2009-09-20
forum: General Help
---

### Post by Zz Sniffy on 2009-09-20
I'm doing a clean install, new hard drive, the works!

What I want to do is dual boot( Ubuntu / Windows ), however I want to make Ubuntu the main OS I'm using. Thing is, partitioning is... well... I'm not familar with it? 

I hate to sound rude but... this really isnt my forte.

I have a 500GB HDD

Id like 60GB for windows
Then the other 440GB for Linux... 

Heres where im having trouble... Im used to having a seperate drive for my files

Example: C: was always my OS, and where i installed my program files
              E: was my documents... Where i stored everything.

Is this possible to do with Ubuntu? If so... how? Ive searched around the site for a bit... its the formates that are hitting me the hardest... ntfs i know i use with windows...  ext?? D:

thanks in advance:
 Sniffy

---

### Post by Random-penguin on 2009-09-20
My recommendation if you want windows and linux to "see" and access your document partition is to set it up as NTFS as windows does not (easily) read linux partitions.

It would be best to set up your desired partition layout of windows using the live Ubuntu cd and Gparted (a great partitioning tool), before installing windows. Perhaps have your c drice as 6oGB and 400Gb for your E drive. (or whatever). Both these partitions need to be NTFS. Then either leave the rest of the disc unpartioned (probably best for a beginner as ubuntu can set itself up in default state during install) or partion with a swap and root partition (/home as well is handy).

Next reboot and install windows, choosing the c drive as the install drive. Windows will take care of the rest. Once windows is happy, install Ubuntu from the live cd... as I said probably choosing the default install alongside windows. (there are help menus as you progress).

Further guidance look at:

[https://help.ubuntu.com/9.04/installation-guide/i386/index.html](https://help.ubuntu.com/9.04/installation-guide/i386/index.html)

Hope I've not muddied the waters and good luck!!!!!

---

### Post by Peacefulpieofdeath on 2009-09-20
I agree install windows first, i had so many problems doing the reverse i had to erace everything...
But you can but home and other files on another partition if you want, i would recoment to make an extended partition and not a primary.

-Peacefulpie

---

### Post by oldfred on 2009-09-21
Some info on partitioning:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

Install info:
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Both windows & Ubuntu can read & write to the NTFS partition which will be d: in windows and sda[COLOR=Red]y[/COLOR] where [COLOR=Red]y[/COLOR] (sda2 or sda3 etc) is the partition number you install it to. Windows will not see the ext3 or ext4 partitions of Ubuntu. You can install a add in to allow windows to read but not write the ext partitions, but it is better to have the shared data partition.

If you partition first make sure that windows is in a primary partition. Linux does not care if it is primary or extended.

---

### Post by hydrotemplar on 2009-09-21
Give a partition for Ubuntu (ext3/4), a swap partition, a Windows partition (NTFS), and a /home partition (ext3/2)

You can use this to get Windows to recognize your /home partition:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
(and yes, this does give rwx for ext2/3... not sure about ext4... and some sticky stuff may happen w/ ext3, it's documented on the site)

if this is a laptop, you should make your /home partition ext3, because if you have a 400GB non-journaling partition, and your battery dies, then you'll be waiting half an hour for the mandatory device check when the computer starts back up...

---

