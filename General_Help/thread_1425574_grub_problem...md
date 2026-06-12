---
title: "grub problem.."
date: 2010-03-09
forum: General Help
---

### Post by noveevon on 2010-03-09
Hi,

i recently wanted to try Linux mint, so i installed it on another hd on my kubuntu computer, it all worked like a charm, however grub did load a bit slower for some reason?

but my problem came when i removed linux mint, then grub stopped working and all i get is the grub rescue screen...

now, ive tried installing grub from the live cd, from the manual i found online, but when i try to mount the /boot i get a error saying there is no such directory....i can however mount my home directory which is on a separate partition...but the guy from live cd guide said i should mount them both....

also when i am in live cd i see both partitions as volume...and i can enter them, but i cannot change the grub files on the /boot partition..

ive been at it for a few hours now and also a few hours yesterday, so any help would be much appreciated...

---

### Post by bumanie on 2010-03-09
Are you using grub 2? - I assume so when you are getting a grub rescue prompt. Reinstalling grub 2 from grub rescue should work without the need of a live cd - here are some instructions, obtained from [here]("http://ubuntuforums.org/showthread.php?t=1195275") and thanks to drs305 for the guide 

Booting from the Rescue Mode
At the grub rescue> prompt, accomplish the following actions to attempt to boot to the latest kernel:

    * ls This will display the known devices and partitions. From this information, the user must determine the device and partition on which the system is installed.
    * set Check the current settings. Note the prefix listing. If it is not pointing to the correct location:
          o set prefix=(hdX,Y)/boot/grub Examples: sda1 is (hd0,1), sdb5 is (hd1,5)
    * set root=(hdX,Y) X is the device/drive, starting with 0. Y is the partition, starting with 1. (Example: (hd0,1) is sda1. (hd3,5) is sdc5.
          o For Wubi installs, use: set root=(loop0)
    * ls /boot Inspect the contents. The user should see varioius kernels, initrd images and the grub folder. If not, use the ls command to inspect the device and attempt to find these files and folders. If necessary, set another device as root.
    * insmod /boot/grub/linux.mod Load the linux module. Without this module loaded, the user will receive an "Unknown command linux" message when trying to load the kernel.
    * linux /vmlinuz root=/dev/sdXY ro Load the linux kernel, substituting the correct designations for "X" and "Y" (example: sda1). The user will see a message showing the kernel has been loaded. (See graphic above)
          o Note: For Wubi installs within Windows, use this code: linux /vmlinuz root=/dev/sdXY loop=/ubuntu/disks/root.disk ro
    * initrd /initrd.img Load the initrd image. When pressing enter, the user may or may not see a message in the terminal. 
    * boot

It worked for me, I used it the other day. The trick will be to know which partition your kubuntu kernel is on.

---

### Post by ajgreeny on 2010-03-09
Alternatively you could download and use Supergrub CD.  You boot to that like any other live CD and use it to boot your various OSs on hard disk, or you can also use it to restore grub as it was before, though you will need to know which version of grub you are dealing with.

Which version of Kubuntu did you (do you) have?  If it was kubuntu 9.04, it will have used legacy grub, but the newest Mint 8 uses grub2.  To restore the two versions requires different activities, so it is important to know which is involved here and to try the right things to get it back.

---

### Post by noveevon on 2010-03-09
> **ajgreeny said:**
> Alternatively you could download and use Supergrub CD.  You boot to that like any other live CD and use it to boot your various OSs on hard disk, or you can also use it to restore grub as it was before, though you will need to know which version of grub you are dealing with.

Which version of Kubuntu did you (do you) have?  If it was kubuntu 9.04, it will have used legacy grub, but the newest Mint 8 uses grub2.  To restore the two versions requires different activities, so it is important to know which is involved here and to try the right things to get it back.


hi guys and thank you for the reply..

i am using a 9.10 kubuntu and i tried supergrub, but it diddnt work.. i will now try the first tip i got and go from there, my /boot is located on sda8 and so i need to figure out which that is in hd0 terms...

my choices are (hd0) (hd0.8) (hd0.7) (hd0.6) (hd0.5) (hd0.1) (hd1) (hd 1.1) (fd0)   i am guessing its 0.8..

---

### Post by ajgreeny on 2010-03-09
Using the new grub2 nomenclature sad8 (sda8, -I like your unintentional typo error) will be (hd0,8) as grub now uses zero as the starting point number for disks, and 1 as the starting point number for partitions, just to confuse us all.

---

### Post by noveevon on 2010-03-09
> **bumanie said:**
> 
          o set prefix=(hdX,Y)/boot/grub Examples: sda1 is (hd0,1), sdb5 is (hd1,5)
    * set root=(hdX,Y) X is the device/drive, starting with 0. Y is the partition, starting with 1. (Example: (hd0,1) is sda1. (hd3,5) is sdc5.
          


ive done this, but that is as far as i get..still no change...i will try and see if my root isnt on sda7 and not sda8....as its human to error...

ok here is what i typed in:

set prefix=(hd0.8)/boot/grub
set root=(hd0.8)

i guess i misunderstood something as after that i dont know what to do...ive rebooted but no change...

---

### Post by noveevon on 2010-03-09
ive decided to give up and do a fresh install...

---

### Post by aceracer24 on 2010-03-09
> **noveevon said:**
> ive decided to give up and do a fresh install...

Your situation is similar to mine...I might be doing the same thing as a result :(

---

