---
title: "Vista Wiped My Grub Loader"
date: 2009-07-24
forum: General Help
---

### Post by SonOfWolf on 2009-07-24
My computer was setup with Ubuntu (9.04) On One Hard Drive and Windows Vista 64 On Another. 

I used to boot into Vista or Ubuntu by choosing them from the grub menu. 

I reinstalled Vista 

Now I can only boot into winows. 

I have used easyBCD to try and set up a new grub. I can choose Ubuntu from the boot list and then grub appears with all the Ubuntu kernels ect but no matter which one I choose it comes up with error 17 unable to find (something, sorry I forgot)

my NeoSmart NeoGrub Bootload Configuration File is as follows
> # NeoSmart NeoGrub Bootloader Configuration File
#
# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst
# Please see the EasyBCD Documentation for information on how to create/modify entries:
# [http://neosmart.net/wiki/display/EBCD](http://neosmart.net/wiki/display/EBCD)

find --set-root --ignore-floppies /boot/grub/menu.lst
configfile /boot/grub/menu.lst

# All your boot are belong to NeoSmart!

## ## End Default Options ##



title        Ubuntu 9.04, kernel 2.6.28-13-generic

uuid        aa8fab7c-a464-4c0f-aa33-f5c6d9c8c799

kernel        /boot/vmlinuz-2.6.28-13-generic 
root=
UUID=aa8fab7c-a464-4c0f-aa33-f5c6d9c8c799 ro 
quiet splash
initrd        /boot/initrd.img-2.6.28-13-generic

quiet



title        Ubuntu 9.04, 
kernel 2.6.28-13-generic (recovery mode)

uuid        aa8fab7c-a464-4c0f-aa33-f5c6d9c8c799

kernel        /boot/vmlinuz-2.6.28-13-generic 
root=
UUID=aa8fab7c-a464-4c0f-aa33-f5c6d9c8c799 ro  
single

initrd        /boot/initrd.img-2.6.28-13-generic



title        Ubuntu 9.04, kernel 2.6.28-11-generic

uuid        aa8fab7c-a464-4c0f-aa33-f5c6d9c8c799

kernel        /boot/vmlinuz-2.6.28-11-generic 
root=UUID=aa8fab7c-a464-4c0f-aa33-f5c6d9c8c799 ro 
quiet splash 

initrd        /boot/initrd.img-2.6.28-11-generic

quiet



title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)

uuid        aa8fab7c-a464-4c0f-aa33-f5c6d9c8c799

kernel        /boot/vmlinuz-2.6.28-11-generic 
root=UUID=aa8fab7c-a464-4c0f-aa33-f5c6d9c8c799 ro  
single

initrd        /boot/initrd.img-2.6.28-11-generic



title        Ubuntu 9.04, memtest86+

uuid        aa8fab7c-a464-4c0f-aa33-f5c6d9c8c799

kernel        /boot/memtest86+.bin

quiet



### END DEBIAN AUTOMAGIC KERNELS LIST
I manged to get the grub information by booting up from a live cd and copying it to my flashdrive. 

Please help me get my Ubuntu to work again as I have it set up just right and really dont want to install again :confused:

---

### Post by merlinus on 2009-07-25
It would have been quite simple to restore grub from the live cd this way:

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd1,0)
root (hd1,0) #use the numbers from the previous command
setup (hd0)
quit 
```but since you went for a windows-based solution, I do not know if this will work.

---

### Post by mthalis on 2009-07-25
Read this you can get more details
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by gastly on 2009-07-25
Well, to solve this you can follow **merlinus**'s instructions above, but I recommend the following if you ever want to reinstall vista again.

```

sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd1,0)
root (hd1,0) #use the numbers from the previous command
setup (hd1,x) # Replace the 'x' with the number of your root partition (or if you have a seperate boot partition, then replace 'x' with your boot partition's number'. And replace 'hd1' with what you got using the above find command.
quit

```

After that, using the EasyBCD add a new menu entry to the vista bootloader and point it to the partition where you install grub (using the above 'setup' command). 
And now you should be able to see a seperate menu entry to boot into Ubuntu.

The pro's of this method is that, if you ever re-install windows you will only need to add the menu entry of Linux to vista's bootloader (no need to reinstall grub again).

Cheers :)

- gastly

---

### Post by diggedy on 2009-07-25
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

this works for me every time. I have 5 operating systems on my pc (i like to tinker) and everytime my boot is messed up I run this and its fixed in a few very short and simple steps

---

### Post by pro003 on 2009-07-25
> **diggedy said:**
> [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

this works for me every time. I have 5 operating systems on my pc (i like to tinker) and everytime my boot is messed up I run this and its fixed in a few very short and simple steps

links are dead man, go to [http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

---

### Post by SonOfWolf on 2009-07-25
So yeah, me again. Followed a tut to reinstall the grub loader using a live CD.
What happens now all depends on which harddrive I set to boot first from the BIOS. 
If I choose the linux one GRUB appears. Vista is on the grub list but when you select it a message about BASH COMMANDS ARE ACCEPTED is show at the top of the screen and it justs sit there doing nothing. 

However if you choose the vista harddrive to boot first then Vista boot (Duh) and it dosnt even show a boot menu. 

How can I change my grub so that it lets me boot vista ??

> ## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        aa8fab7c-a464-4c0f-aa33-f5c6d9c8c799
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=aa8fab7c-a464-4c0f-aa33-f5c6d9c8c799 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        aa8fab7c-a464-4c0f-aa33-f5c6d9c8c799
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=aa8fab7c-a464-4c0f-aa33-f5c6d9c8c799 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        aa8fab7c-a464-4c0f-aa33-f5c6d9c8c799
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=aa8fab7c-a464-4c0f-aa33-f5c6d9c8c799 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        aa8fab7c-a464-4c0f-aa33-f5c6d9c8c799
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=aa8fab7c-a464-4c0f-aa33-f5c6d9c8c799 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        aa8fab7c-a464-4c0f-aa33-f5c6d9c8c799
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1Thanks

---

### Post by merlinus on 2009-07-25
If booting from your linux hdd, and vista is on the first partition of the second hdd, then change this (in /boot/grub/menu.lst):

title        Windows Vista (loader)
[COLOR=Red]rootnoverify    (hd0,0)[/COLOR]
savedefault
makeactive
chainloader    +1 			 		

to this:

title        Windows Vista (loader)
[COLOR=Red]rootnoverify    (hd1,0)[/COLOR]
savedefault
makeactive
chainloader    +1 			 		

and restart.

---

### Post by SonOfWolf on 2009-07-25
I try and edit the file but it says I do not have permission to save my changes? 
How do I get permission?
Thanks

---

### Post by merlinus on 2009-07-25
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by SonOfWolf on 2009-07-25
Message appears saying no boot 
press control+alt+delete to restart

---

### Post by merlinus on 2009-07-25
Post results of

```
sudo fdisk -l
```

---

### Post by diggedy on 2009-07-25
have you looked into the supergrub program yet? It really is worth trying if your stuck

---

### Post by SonOfWolf on 2009-07-25
I fixed it. Thanks for all your help guys. It was (hd3,0) :D

That supergrub thing didnt do much for me 

but it works :D

Got my desktop and my fresh vista all working and booting from the grub menu 

Thanks again

---

