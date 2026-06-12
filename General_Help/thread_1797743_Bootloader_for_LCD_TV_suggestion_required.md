---
title: "Bootloader for LCD TV suggestion required"
date: 2011-07-05
forum: General Help
---

### Post by vikrang on 2011-07-05
I have installed Fed 15 to my 3 partition - (other 2 being Ubuntu and  Windows 7)..I am using my LCD TV as a monitor ..The GRUB 2 loader installed by NATTY does  not seem to load in the proper way and only a blank screen is displayed  on boot.Thereafter after a long pause , Natty loads up.

I want to try Grub - Legacy ...I had installed fedora correctly from USB  but wrongly chosen the boot device as /dev/sdb as I thought the booting  device is always "sda" and since assumed HDD would be sdb...Now the  grub is installed in the USB and the OS is in HDD!

I am able to boot into the FC installation in my HDD ..If I try to run  "grub-install  /dev/sda" from the terminal , it is not installing and on  boot I get "grub rescue>"

How do I install a good bootloader which supports my LG LCD TV?

---

### Post by DawieS on 2011-07-05
Any boot-loader will support your LCD TV. My guess is that your **Grub** boot-loader on the Natty partition is now defective and needs repair.

First you need to check your BIOS settings that you are booting from the correct disk (not USB disk).

To select the correct boot partition on a specific disk, you can use **Gparted** to select the boot flag on the partition you want to boot from.

To repair your **Grub** boot-loader, the following **Howto** by forum member **talsemgeest** will point you in the right direction::smile:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by corrytonapple on 2011-07-05
Instead of rolling back, you should try to change your resolution to your screen size.  Open up a Terminal and run:
```
sudo gedit /etc/default/grub
```
Find the code block that says 
```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
```
One that final line, you just need to remove the "#", also known as uncommenting.  Then, throw in your resolution of the TV.  The size of the TV screen would be good here.....
Then save and quit.  Restart to see if it worked.
The same thing happened to me when my screen resolution was off....

---

### Post by vikrang on 2011-07-05
Thanks both of you

Legacy - Grub did the trick!

I spotted a small typo in menu.lst , then reinstalled grub from the live CD ...Everything is smooth and man it is so refreshing to see legacy grub which I was able to modify in seconds

Grub2 is a bit of a pain with too many files around ..Here I choose what I want ! No messing around with multiple lines of the same OS (slack has 5 entries as it has different kernels!) , editing 40_custom , updating grub , modifying grub.cfg and all of that nonsense

The resolution of Grub is perfect!

---

