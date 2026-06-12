---
title: "resize ext3 for win7 dual boot"
date: 2010-02-17
forum: General Help
---

### Post by CarlC4 on 2010-02-17
I have a 320gb hard drive with Ubuntu 9.10 karmic fully installed on it. I need to know how to shrink the partition my ubuntu is on so i can create another partition for win7.

please help, thank you.

---

### Post by jamesisin on 2010-02-17
First, let me say that I usually recommend running a virtual machine rather than a dual boot.  For virtualization I use VirtualBox:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

You can follow the instructions under "Debian-based Linux distributions" to add a repository and keep up to date using Synaptic.

Ok, I feel better.

If you want to resize your operating system partition (or any partition used by your operating system), you will not be able to do so while signed into that operating system.  You cannot resize a mounted partition and any partition in use is by necessity mounted.

So, get a copy of the current installation CD and fire that up.  You will want to use the try Ubuntu without installing option.  This will allow you to boot into Ubuntu while leaving your installed Ubuntu partition unmounted.

Once you are in the Live Ubuntu environment you can start the partition editor.  It is called GParted (though it may be termed simply Partition Editor or something similar).  You will find that here:

System &#8212;> Administration &#8212;> Partition Editor [or] gparted

You can see a little information about using gparted on this post of mine:

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)

Now for the important bit: be very careful.  You can easily delete a partition and destroy all data on it if you don't make slow, calculated choices.  Also, I recommend shrinking the partition from the end of the drive rather than the beginning (moving the ending bit toward the left rather than moving the beginning bit toward the right).

Best of luck.

---

### Post by tom4everitt on 2010-02-17
The idea is that you can't resize partitions on a hard drive that is mounted (its risky, and therefore disabled). So what to do?

Burn yourself a live cd (or make a bootable usb with system->admin->usb startup creator) or use an old live cd or whatever. Boot into that. Open gparted (applications->system tools->gparted). do the resizing/partitioning. restart.

---

### Post by CarlC4 on 2010-02-17
thank you very much, i'll give it a try

---

### Post by jamesisin on 2010-02-17
Great.  Let us know how it goes.

---

### Post by CarlC4 on 2010-02-18
the resizing went perfectly, now just to install windows 7:)

---

### Post by CarlC4 on 2010-02-18
installed windows 7, but how do i get back to ubuntu i don't understand the directions ubuntu.com gives

---

### Post by jamesisin on 2010-02-18
What trouble are you running into?  You are likely now using the Windows boot loader and may need to add a line to include the Ubuntu installation among your boot choices.

---

### Post by jpl888 on 2010-02-18
You need to boot back off the live CD and reinstall grub ```
grub-install /dev/sda
```

Grub 2 should then automatically detect and add an entry for your Windows 7 install but YMMV :)

---

### Post by jamesisin on 2010-02-18
Grub is probably the preferred boot loader.  Take a look at this Ubuntu Help page:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by CarlC4 on 2010-02-18
according to that link i have grub legacy, anything i should watch out for?

---

### Post by jamesisin on 2010-02-18
Did you upgrade to 9.10 or purposefully install the old grub in installation?  I thought 9.10 included grub 2 in its installer.

---

### Post by CarlC4 on 2010-02-18
i upgraded with update manager

---

### Post by CarlC4 on 2010-02-18
@jpl888: is there a simple code like that for grub legacy?

---

### Post by jamesisin on 2010-02-18
Ah, that explains it.  I had oodles of troubles with my last 9.04 &#8212;> 9.10 upgrade.  In the end I abandoned the upgrade and built the 9.10 system from scratch.

---

### Post by CarlC4 on 2010-02-18
so what do i do D: i upgraded fine, it's just that i need to boot back into ubuntu, is there any way to put grub2 as the main boot from livecd?

---

### Post by jamesisin on 2010-02-18
From that grub page I linked above (emphasis added):

> If you ran previous version of Ubuntu and upgraded to Ubuntu Karmic 9.10, you are running Grub Legacy by default; **unless you have executed upgrade-from-grub-legacy, then you are running Grub2**.

So the answer must be "run upgrade-from-grub-legacy".  Do I know how to do that?  Not exactly, but surely it can be done from the Live CD.

Looks approximately correct, in fact:

[http://www.ubuntu-inside.me/2009/06/howto-upgrade-to-grub2-on-ubuntu-jaunty.html](http://www.ubuntu-inside.me/2009/06/howto-upgrade-to-grub2-on-ubuntu-jaunty.html)

---

### Post by gh4ever on 2010-02-18
Follow the directions at:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Make sure you follow the steps for "Grub Legacy" and make sure you do it off of a Jaunty (9.04) live cd.

---

### Post by jamesisin on 2010-02-18
> **gh4ever said:**
> Follow the directions at:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
Make sure you follow the steps for "Grub Legacy" and make sure you do it off of a Jaunty (9.04) live cd.

You realize that is the link we have been talking about, right?

---

### Post by CarlC4 on 2010-02-18
i'm using a 9.04 livcd, should i make a 9.10 livecd and try it from there?

---

### Post by CarlC4 on 2010-02-18
@gh4ever: i've looked at that and it won't work for me, i did something different apparently

---

### Post by jamesisin on 2010-02-18
That's what the second link seems to suggest.  Unless anyone sees reason to protest, I would try to upgrade grub.

---

### Post by jpl888 on 2010-02-19
Well I agree upgrading to Grub 2 isn't a bad idea. Particularly when it autodetects what OS you have on what partition. If you are allergic to the command line though I would give it a miss.

In response to the earlier post the same grub-install command works for Grub legacy but it won't detect operating systems.

---

### Post by CarlC4 on 2010-02-19
ok then how do i make it recognize windows 7

---

### Post by jpl888 on 2010-02-19
If you look at the end of /boot/grub/menu.lst you should see an commented entry for Windows XP. Assuming Windows 7 is on the first partition that should work as is.

If you have any trouble post your menu.lst and fdisk -l /dev/sda and I'll sort it out.

---

### Post by jamesisin on 2010-02-19
Just to be clear, you'll need sudo:

```
sudo fdisk -l /dev/sda
```

---

### Post by CarlC4 on 2010-02-19
menu.lst:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=65eb7be3-3543-4568-b70f-d652cbad0fc6 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=65eb7be3-3543-4568-b70f-d652cbad0fc6

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        65eb7be3-3543-4568-b70f-d652cbad0fc6
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=65eb7be3-3543-4568-b70f-d652cbad0fc6 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        65eb7be3-3543-4568-b70f-d652cbad0fc6
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=65eb7be3-3543-4568-b70f-d652cbad0fc6 ro  single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-17-generic
uuid        65eb7be3-3543-4568-b70f-d652cbad0fc6
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=65eb7be3-3543-4568-b70f-d652cbad0fc6 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-17-generic (recovery mode)
uuid        65eb7be3-3543-4568-b70f-d652cbad0fc6
kernel        /boot/vmlinuz-2.6.31-17-generic root=UUID=65eb7be3-3543-4568-b70f-d652cbad0fc6 ro  single
initrd        /boot/initrd.img-2.6.31-17-generic
file:///usr/share/ubuntu-artwork/home/index.html
title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        65eb7be3-3543-4568-b70f-d652cbad0fc6
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=65eb7be3-3543-4568-b70f-d652cbad0fc6 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        65eb7be3-3543-4568-b70f-d652cbad0fc6
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=65eb7be3-3543-4568-b70f-d652cbad0fc6 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, memtest86+
uuid        65eb7be3-3543-4568-b70f-d652cbad0fc6
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

fdisk -l:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbeed2fde

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       10443    83779584    7  HPFS/NTFS
/dev/sda3           10444       37508   217399612+  83  Linux
/dev/sda4           37509       38913    11285662+   5  Extended
/dev/sda5           37509       38913    11285631   82  Linux swap / Solaris

---

### Post by CarlC4 on 2010-02-19
i get this error when i run grub-install /dev/sda

mkdir: cannot create directory `/boot/grub': Permission denied

---

### Post by jamesisin on 2010-02-20
First, a bit of advice friendly forum advice.  Use code boxes to prevent loooooooooong posts:

```
[NOPARSE][CODE]put your code here
```[/NOPARSE][/CODE]

Have fun with that.

Ok, are you running grub install with elevated privileges?

```
sudo grub-install /dev/sda
```

---

### Post by CarlC4 on 2010-02-21
sorry haven't replied in a while. i get this when i put in sudo grub-install /dev/sda
```

Probing devices to guess BIOS drives. This may take a long time.
Could not find device for /boot: Not found or not a block device.

```

---

### Post by jamesisin on 2010-02-21
I am assuming you *do* have a /boot on sda(1)?

I would make a thread specifically for this error (cross-link with this thread for continuity) and see if you can drum up a grub expert to help with it.

---

### Post by CarlC4 on 2010-02-21
found this and it worked perfectly

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

---

### Post by jamesisin on 2010-02-21
Perfect.  Time to mark the thread as SOLVED then?

---

