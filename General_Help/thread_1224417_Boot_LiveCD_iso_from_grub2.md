---
title: "Boot LiveCD iso from grub2"
date: 2009-07-27
forum: General Help
---

### Post by phenest on 2009-07-27
I found an [article]("http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback") regarding the loopback feature of Grub2 where by you could boot from an iso. Does anyone know if it's possible, if so how, to do this with the Ubuntu Live CD?

---

### Post by blueridgedog on 2009-07-27
The article you linked to and the one it links to ( [http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/](http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/) ) have pretty clear instructions.  What part of the process is not working for you?

I would start by putting your iso in a known (such as boot) location and altering the line from the example from isofrom=/dev/sda1/grml/grml-small_2008.11.iso to isofrom=/dev/sda1/boot/myjaunty.iso (or whatever you called it).

---

### Post by phenest on 2009-07-27
Something like this:
```

menuentry "Ubuntu Jaunty Live CD" {
loopback loop (hd0,3)/steve/archive/iso/linux/karmic-desktop-amd64.iso
linux (loop)/casper/vmlinuz isofrom=/dev/sda3/steve/archive/iso/linux/karmic-desktop-amd64.iso root=/dev/sda3 boot=casper quiet splash noprompt
initrd (loop)/casper/initrd.lz
}
```
...just drops to a busy box.

---

### Post by blueridgedog on 2009-07-27
> **phenest said:**
> Something like this:
```

menuentry "Ubuntu Jaunty Live CD" {
loopback loop (hd0,3)/steve/archive/iso/linux/karmic-desktop-amd64.iso
linux (loop)/casper/vmlinuz isofrom=/dev/sda3/steve/archive/iso/linux/karmic-desktop-amd64.iso root=/dev/sda3 boot=casper quiet splash noprompt
initrd (loop)/casper/initrd.lz
}
```
...just drops to a busy box.

Did you verify the /casper/initrd.lz path and name on the image you are using?  It is /casper/initrg.gz on mine.  Also, try it without the root directive.  How did you arrive at boot=casper?  Did you try live?

---

### Post by phenest on 2009-07-28
On Karmic, it's initrd.lz, whereas it's initrd.gz on Jaunty. I've tried both Jaunty and Karmic with varying different options with no success.

boot=casper was taken from the boot options for Ubuntu.

---

### Post by phenest on 2009-07-28
The best I get is a BusyBox prompt.

---

### Post by blueridgedog on 2009-07-28
Try the commands one at a time at a grub prompt.  You may get some more debugging information.  I will mock it up on my end as well.  Is the partition with the image a primary one (I assume it is as the first partition in an extended one would be hd0,5 in grub speak)?

---

### Post by Herman on 2009-07-29
```
menuentry "Ubuntu Jaunty Live CD" {
loopback loop (hd0,3)/steve/archive/iso/linux/karmic-desktop-amd64.iso
linux (loop)/casper/vmlinuz isofrom=/dev/sda3/steve/archive/iso/linux/karmic-desktop-amd64.iso root=/dev/sda3 boot=casper quiet splash noprompt
initrd (loop)/casper/initrd.[COLOR=Red]**l**[/COLOR]z
}
``` Try replacing 'initrd.lz' with 'initrd.gz' and see if that helps. 
Regards, Herman :)

---

### Post by phenest on 2009-07-29
> **Herman said:**
> ```
menuentry "Ubuntu Jaunty Live CD" {
loopback loop (hd0,3)/steve/archive/iso/linux/karmic-desktop-amd64.iso
linux (loop)/casper/vmlinuz isofrom=/dev/sda3/steve/archive/iso/linux/karmic-desktop-amd64.iso root=/dev/sda3 boot=casper quiet splash noprompt
initrd (loop)/casper/initrd.[COLOR=Red]**l**[/COLOR]z
}
``` Try replacing 'initrd.lz' with 'initrd.gz' and see if that helps. 
Regards, Herman :)

POn Karmic alpha 3, it's 'initrd.lz'.

---

### Post by kewarken on 2009-07-30
I suspect none of this will work.  To me, it looks like the 'isofrom' option is specific to the grml distro he's using unless it's also a ubuntu option.  That is to say, unless there is some specific support in the init script for dealing with an iso, it's not going to happen.

Normal sequence:
- boot kernel and initrd
- mount some stuff like squashfs partitions or whatever from install media
- run init

Fancy grub2 sequence:
- boot kernel and initrd
- mount install media (using isofrom)
- loopback mount iso file from install media (using isofrom)
- NOW do the squashfs mounting, etc.
- run init

If you look at the isofrom option, it's giving both a device and a path to the iso so that steps 2 and 3 can happen.  If distros are going to support this, it would definitely be handy for everyone to standardize on something like 'isofrom' to be sure.

cheers,

Kris

---

### Post by arqbrulo on 2009-07-30
I have grub2 installed on my computer, and I "accidentally" noticed that I could boot from ISO images. I tried it with a distro that I had downloaded before, and it worked as expected. But when I tried with an Ubuntu iso, I would only get a busybox prompt. In the past, I've tried booting an Ubuntu iso with other bootloaders and it would do the same thing, but I think it's an Ubuntu iso thing.

---

### Post by phenest on 2009-07-30
I'm inclined to agree with the last 2 comments. Maybe this could be raised on brainstorm or launchpad? Not sure which one.

---

### Post by pxwpxw on 2009-08-01
Booting ubuntu live iso with grub.efi-
(shouod be essentially same  for gru2-pc, I just use efi on apple mac for externals)

uses ubuntu iso-scan/filename=/u904-64-live.iso

grub2.efi, on apple imac86,

booted u904-amd64-live.iso with grub.efi on imac86
using grub loopback and the ubuntu option 'iso-scan/filename=....iso'

iso was at /dev/sda4/u904-64-live.iso

```

menuentry "u904-64-live.iso" {
 fakebios
 search --set -f /u904-64-live.iso
 loopback loop /u904-64-live.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/u904-64-live.iso video=efifb noefi
 initrd (loop)/casper/initrd.gz
}

```

(fakebios,video=efifb, noefi are grub.efi options).

Note that iso was not found when on hfsplus (although installers do find iso's on hfplsu), had to move to ext3 , probably ok on fat32.

Very good reference found -
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
MultiBoot USB with Grub2 (boot directly from iso files)

---

### Post by defrag on 2009-08-12
But you know, the most popular formats of the compressed files in linux  cannot be changed.
So grub2 can use them too.

---

### Post by VMC on 2009-08-18
> **phenest said:**
> I found an [article]("http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback") regarding the loopback feature of Grub2 where by you could boot from an iso. Does anyone know if it's possible, if so how, to do this with the Ubuntu Live CD?

I couldn't find this topic earlier so I opened a [**new one**]("http://ubuntuforums.org/showthread.php?t=1243182") on this subject. I found out how to boot pmagic using grub2 loopback.

---

### Post by kagashe on 2009-10-27
The answer is there on [Community Docs.]("https://help.ubuntu.com/community/Grub2#Booting%20an%20ISO")

kagashe

---

### Post by drs305 on 2009-10-27
> **kagashe said:**
> The answer is there on [Community Docs.]("https://help.ubuntu.com/community/Grub2#Booting%20an%20ISO")

kagashe

I also just updated the [Grub2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") thread here. Not sure why I continue to sync the two, but for now they are.

---

### Post by musarraf172 on 2009-11-11
> **kewarken said:**
> I suspect none of this will work.  To me, it looks like the 'isofrom' option is specific to the grml distro he's using unless it's also a ubuntu option.  That is to say, unless there is some specific support in the init script for dealing with an iso, it's not going to happen.

Normal sequence:
- boot kernel and initrd
- mount some stuff like squashfs partitions or whatever from install media
- run init

Fancy grub2 sequence:
- boot kernel and initrd
- mount install media (using isofrom)
- loopback mount iso file from install media (using isofrom)
- NOW do the squashfs mounting, etc.
- run init

If you look at the isofrom option, it's giving both a device and a path to the iso so that steps 2 and 3 can happen.  If distros are going to support this, it would definitely be handy for everyone to standardize on something like 'isofrom' to be sure.

cheers,

Kris


Try this.. I am assuming that you have kept your live iso in your /boot folder. Make sure that the partition is a linux partition.

menuentry "Ubuntu Live 9.10 32bit" {
 loopback loop /boot/ubuntu-9.10-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/ubuntu-9.10-desktop-i386.iso noeject noprompt --
 initrd (loop)/casper/initrd.lz
}


It works... :D:D

---

### Post by Progressive on 2009-11-24
> **musarraf172 said:**
> Try this.. I am assuming that you have kept your live iso in your /boot folder. Make sure that the partition is a linux partition.

menuentry "Ubuntu Live 9.10 32bit" {
 loopback loop /boot/ubuntu-9.10-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/ubuntu-9.10-desktop-i386.iso noeject noprompt --
 initrd (loop)/casper/initrd.lz
}


It works... :D:D


That does work for me, but only if you are using an ISO on the same partition as the boot partition.

When I try to use a different one, it drops to busybox.

I am trying to use the ISO to resize my boot partition though, so I don't want the partition locked.

mine currently looks like this:

menuentry "Ubuntu LiveCD 9.10 64bit" {
loopback loop (hd1,1)/edward/kubuntu-9.10-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/dev/sdb1/edward/kubuntu-9.10-desktop-amd64.iso noeject n$
initrd (loop)/casper/initrd.lz
}

I'm not sure what to type into the iso-scan/filename section. Nothing seems to work.

---

### Post by drs305 on 2009-11-24
> **Progressive said:**
> That does work for me, but only if you are using an ISO on the same partition as the boot partition.

When I try to use a different one, it drops to busybox.

Progressive,

I have the Karmic Ubuntu iso on a separate partition and it works for me (and has mixed results with other users). Here is my menuentry:
```

menuentry "Karmic 64 ISO (sda7)" {
loopback loop (hd0,7)/iso/ubuntu-9.10-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu-9.10-desktop-amd64.iso noprompt
initrd (loop)/casper/initrd.lz
}

```

---

### Post by musarraf172 on 2009-11-24
> **Progressive said:**
> That does work for me, but only if you are using an ISO on the same partition as the boot partition.

When I try to use a different one, it drops to busybox.

I am trying to use the ISO to resize my boot partition though, so I don't want the partition locked.

mine currently looks like this:

menuentry "Ubuntu LiveCD 9.10 64bit" {
loopback loop (hd1,1)/edward/kubuntu-9.10-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/dev/sdb1/edward/kubuntu-9.10-desktop-amd64.iso noeject n$
initrd (loop)/casper/initrd.lz
}



I'm not sure what to type into the iso-scan/filename section. Nothing seems to work.





I made it work on other partitions also. Just have a look in the following configuration file.

#This has to be put in your grub.cfg
#The drive is an NTFS partition. Therefor I am using "insmod ntfs"
#The partition is on my first harddrive and on 6th partition (sda6).
#It is described by (hd0,6)
# If it is a Linux partition use "insmod ext2"
#The files vmlinuz and initrd.gz for puppy linux is kept on sda6.
menuentry "Puppy On drive E:" {
insmod ntfs
set root=(hd0,6)
linux /vmlinuz
initrd /initrd.gz
}

#The drive is an NTFS partition. Therefor I am using "insmod ntfs"
#The partition is on my first harddrive and on 6th partition (sda6).
#It is described by (hd0,6)
# If it is a Linux partition use "insmod ext2"
#The files vmlinuz and initrd.gz for puppy linux is kept on "sda6/Pup".

menuentry "Puppy-Mac On drive E:" {
insmod ntfs
set root=(hd0,6)
linux /Pup/vmlinuz
initrd /Pup/initrd.gz
}


#The drive is an NTFS partition. Therefor I am using "insmod ntfs"
#The partition is on my first harddrive and on 5th partition (sda5).
#It is described by (hd0,5)
# If it is a Linux partition use "insmod ext2"
#The file "ubuntu-9.10-desktop-i386.iso" is kept on sda5/SOFTWARES/Ubuntu/.

menuentry "Ubuntu Live 9.10 on D:" {
insmod ntfs
set root=(hd0,5)
 loopback loop /SOFTWARES/Ubuntu/ubuntu-9.10-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-9.10-desktop-i386.iso noeject noprompt --
 initrd (loop)/casper/initrd.lz
}

#The drive is an NTFS partition. Therefor I am using "insmod ntfs"
#The partition is on my first harddrive and on 5th partition (sda5).
#It is described by (hd0,5)
# If it is a Linux partition use "insmod ext2"
#The file "ubuntu-9.04-desktop-i386.iso" is kept on sda5/SOFTWARES/Ubuntu/.

menuentry "Ubuntu Live 9.04 on D:" {
insmod ntfs
set root=(hd0,5)
 loopback loop /SOFTWARES/Ubuntu/ubuntu-9.04-desktop-i386.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/SOFTWARES/Ubuntu/ubuntu-9.04-desktop-i386.iso noeject noprompt --
 initrd (loop)/casper/initrd.gz
}



Hope you understand this and it works..


@Progressive

If you want to resize your boot partition , then you must boot from a different hard drive or some usb flash. Then only you will get an exclusive access to your main hard drive to perform partition resize. For booting from USB you can use grub2 with an ubuntu iso but it is a long process rather I would suggest that you use unetbootin to creat usb flash bootable with ubuntu iso or even you can try ubuntu default "System/Administration/USB start up disk creator"

For using grub2 with iso first you have to install grub2 in flash drive and put the necessary iso on it. Then make a grub.cfg file on it and configure it as said in the first section.

Wish you a good luck.....

---

### Post by musarraf172 on 2009-11-25
Anybody tried to boot Fedora Core 12 iso with grub2??

I am having root file system mounting error.

The configuration is like this :



menuentry "Fedora Core 12 on E:" {
insmod ntfs
set root=(hd0,6)
 loopback loop /Transmission/Fedora-12-i686-Live/Fedora-12-i686-Live.iso
 linux (loop)/EFI/boot/vmlinuz0 root=live:LABEL=Fedora-12-i686-Live rootfstype=auto ro liveimg quiet  rhgb  boot=EFI/boot iso-scan/filename=/Transmission/Fedora-12-i686-Live/Fedora-12-i686-Live.iso noeject noprompt --
 initrd (loop)/EFI/boot/initrd0.img
}

---

### Post by RomanIvanov on 2009-12-02
Here is my experience:

DVD does not supported by grub2
```

menuentry "Ubuntu DVD Live 9.10 32bit" {
	insmod ext2
	set root=(hd1,1)
	loopback loop /boot/ubuntu-9.04-dvd-i386.iso
	linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/ubuntu-9.04-dvd-i386.iso noeject noprompt --
	initrd (loop)/casper/initrd.lz
}

```
Ubuntu images Works !!!!
```

menuentry "xubuntu-9.10-desktop-i386.iso" {
	insmod ext2
	set root=(hd1,1)
	loopback loop /boot/xubuntu-9.10-desktop-i386.iso
	linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/xubuntu-9.10-desktop-i386.iso noeject noprompt --
	initrd (loop)/casper/initrd.lz
}

```

Gparted does not work:
[http://osdir.com/ml/grub-devel-gnu/2009-08/msg00143.html](http://osdir.com/ml/grub-devel-gnu/2009-08/msg00143.html)
```

menuentry "gparted-live-0.4.5-2.iso" {
	insmod ext2
	set root=(hd1,1)
	loopback loop /boot/gparted-live-0.4.5-2.iso
	linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/gparted-live-0.4.5-2.iso noeject noprompt --
	initrd (loop)/casper/initrd.lz
}

```

---

### Post by musarraf172 on 2009-12-02
> **RomanIvanov said:**
> Here is my experience:

DVD does not supported by grub2
```

menuentry "Ubuntu DVD Live 9.10 32bit" {
	insmod ext2
	set root=(hd1,1)
	loopback loop /boot/ubuntu-9.04-dvd-i386.iso
	linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/ubuntu-9.04-dvd-i386.iso noeject noprompt --
	initrd (loop)/casper/initrd.lz
}

```
Ubuntu images Works !!!!
```

menuentry "xubuntu-9.10-desktop-i386.iso" {
	insmod ext2
	set root=(hd1,1)
	loopback loop /boot/xubuntu-9.10-desktop-i386.iso
	linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/xubuntu-9.10-desktop-i386.iso noeject noprompt --
	initrd (loop)/casper/initrd.lz
}

```

Gparted does not work:
[http://osdir.com/ml/grub-devel-gnu/2009-08/msg00143.html](http://osdir.com/ml/grub-devel-gnu/2009-08/msg00143.html)
```

menuentry "gparted-live-0.4.5-2.iso" {
	insmod ext2
	set root=(hd1,1)
	loopback loop /boot/gparted-live-0.4.5-2.iso
	linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/gparted-live-0.4.5-2.iso noeject noprompt --
	initrd (loop)/casper/initrd.lz
}

```



Your gparted live will not work because the "boot" and "initrd" parameter are wrong.....

You have given as "boot = casper"
"intrd (loop)/casper/initrd.lz"
boot parameter points the folder where the kernel files are available ( i.e vmlinuz and initrd ). Casper is not the folder for kernel files in gparted.

More over the kernel files for gparted are different not initrd.lz

"casper and initrd.lz " is specifically only for ubuntu 9.10 ...

Please check the kernel folder for gparted..


For DVD boot , I have not tried yet.. I will check that..

---

### Post by KillaB7 on 2009-12-03
Anyone figure out how to install using the Server ISO?

Here's my grub2 entry, however the install fails at detecting the CD-ROM drive.
```

menuentry "Ubuntu 9.10 Server 32bit" {
 loopback loop /boot/iso/ubuntu-9.10-server-i386.iso
 linux (loop)/install/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-9.10-server-i386.iso noeject noprompt --
 initrd (loop)/install/initrd.gz
}

```

Also, here's a simply entry for g4u for anyone interested.
Tried version 2.4, but it stalled out and wouldn't respond to keyboard input for some reason.
```

menuentry "g4u 2.3" {
  loopback loop /boot/iso/g4u-2.3.iso
  netbsd (loop)/netbsd
}

```

---

### Post by musarraf172 on 2009-12-03
> **KillaB7 said:**
> Anyone figure out how to install using the Server ISO?

Here's my grub2 entry, however the install fails at detecting the CD-ROM drive.
```

menuentry "Ubuntu 9.10 Server 32bit" {
 loopback loop /boot/iso/ubuntu-9.10-server-i386.iso
 linux (loop)/install/vmlinuz boot=casper iso-scan/filename=/boot/iso/ubuntu-9.10-server-i386.iso noeject noprompt --
 initrd (loop)/install/initrd.gz
}

```

Also, here's a simply entry for g4u for anyone interested.
Tried version 2.4, but it stalled out and wouldn't respond to keyboard input for some reason.
```

menuentry "g4u 2.3" {
  loopback loop /boot/iso/g4u-2.3.iso
  netbsd (loop)/netbsd
}

```



For your ubuntu server check the "boot"  parameter . You have given as "casper".. But kernel files folder are poited to "install" folder...

For netbsd you did not specify the kernel files.

Can you tell the folder name in the iso where the kernel files (vmlinuz and initrd) are residing ??

A menu entry in grub2 has the following important parameters

insmod -----> defines the partition type from where it will boot
set root----> defines the root 
loopback-----> monuts the iso
linux -------> points the linux kernel file in general to vmlinuz ( the name 'vmlinuz' may vary for different os..
initrd ------> points to the initial ram image to be loaded

Please read the grub2 introductions available in forum....

---

### Post by KillaB7 on 2009-12-03
> **musarraf172 said:**
> 
For netbsd you did not specify the kernel files.

Can you tell the folder name in the iso where the kernel files (vmlinuz and initrd) are residing ??


Actually that's all you need for g4u.  The iso only contains two files: boot and netbsd.
Both 2.3 and 2.4 boot fine, but 2.4 errored out on two different machines.

EDIT: Looks like the 2.3 image only contains two files, but the 2.4 image contains many more.


Thanks for the server entry help! I'll give it another try.

---

### Post by musarraf172 on 2009-12-04
> **KillaB7 said:**
> Actually that's all you need for g4u.  The iso only contains two files: boot and netbsd.
Both 2.3 and 2.4 boot fine, but 2.4 errored out on two different machines.

EDIT: Looks like the 2.3 image only contains two files, but the 2.4 image contains many more.


Thanks for the server entry help! I'll give it another try.

Dont forget to post your result...:D

---

### Post by musarraf172 on 2009-12-04
An Update ::

I have got success to boot Fedora 12 iso with grub2 in a different manner.

To boot FC12 iso with grub2 loopback, it does not recognize the 'root' parameter as looped iso . FC12 only accepts any linux partion or actual cdrom as root parameter. So I tried the following trick.

1. Extract the "isolinux" and  "LiveOS" folders from FC12 iso on your ubuntu root/

2. Then add the following entry in /etc/grub.d/40_custom



menuentry "Fedora Core 12 live on ubuntu root:" {
insmod ext2
set root=(hd0,3)
linux /Fedora-12-i686-Live/isolinux/vmlinuz0 root=UUID=6e9bf6ba-f80a-4009-81c8-fe0f21f48c66 rootfstype=auto ro liveimg quiet  rhgb rd_NO_LUKS rd_NO_MD noiswmd
initrd /Fedora-12-i686-Live/isolinux/initrd0.img
}

Do not forget to change the UUID with your linux partition's UUID where you have extracted the isolinux and LiveOS folders

3. Run " sudo update-grub2"

4. reboot.
5. Now you have the FC12 option to boot. 

Additionally you can omit the "quiet  rhgb rd_NO_LUKS rd_NO_MD noiswmd" to get a non quiet boot..


:popcorn::popcorn:

---

### Post by KillaB7 on 2009-12-04
Still getting a CD-ROM detection error with the following change:
```

menuentry "Ubuntu 9.10 Server 32bit" {
 loopback loop /boot/iso/ubuntu-9.10-server-i386.iso
 linux (loop)/install/vmlinuz [COLOR="Red"]boot=install[/COLOR] iso-scan/filename=/boot/iso/ubuntu-9.10-server-i386.iso noeject noprompt --
 initrd (loop)/install/initrd.gz
}

```

Are there any grub2 options to fool the installer into thinking my usb stick is a cd-rom drive?

---

### Post by musarraf172 on 2009-12-14
> **KillaB7 said:**
> Still getting a CD-ROM detection error with the following change:
```

menuentry "Ubuntu 9.10 Server 32bit" {
 loopback loop /boot/iso/ubuntu-9.10-server-i386.iso
 linux (loop)/install/vmlinuz [COLOR="Red"]boot=install[/COLOR] iso-scan/filename=/boot/iso/ubuntu-9.10-server-i386.iso noeject noprompt --
 initrd (loop)/install/initrd.gz
}

```

Are there any grub2 options to fool the installer into thinking my usb stick is a cd-rom drive?



Sorry for late answer. I was downloading the server iso.

Try the following. It worked for me!!



menuentry "Ubuntu Server Installer:" {
insmod ntfs
set root=(hd0,6)
loopback loop /Transmission/ubuntu-9.10-server-i386.iso
linux (loop)/install/vmlinuz boot=install isofrom=/dev/hda6/Transmission/ubuntu-9.10-server-i386.iso noeject noprompt --
initrd (loop)/install/initrd.gz
}


You have to edit the the "set root " and the path for the iso ...

---

### Post by arqbrulo on 2009-12-14
Question: has anybody tried to boot systemrescuecd from iso? I've tried it but was not able to. Thanks.

---

### Post by drs305 on 2009-12-15
> **arqbrulo said:**
> Question: has anybody tried to boot systemrescuecd from iso? I've tried it but was not able to. Thanks.

When G2 came out I did a lot of experimenting with the SRCD and the Ubuntu ISOs. I was able to boot to the Ubuntu CDs but don't recall if I had success with the System Rescue CD. I'm on the road and won't be able to check my home system for a few days.

One reason I don't recall is that I have had the SystemRescue CD files on my computer for quite some time. There was a link on their site on how to install the files on your system so no CD is required. I believe it was called "frugal install" or something similar. I also remember that there was talk of this feature being removed for some reason. 

In any case, I was able to extract the files from the ISO, move them around a bit following the link somewhere on the SRCD site, and can access them from the G2 menu with the following menuentry:
> [noparse]menuentry "System Rescue CD on hard drive" {
set root=(hd0,8)
linux   /isolinux/sysrcd subdir=sysrcd setkmap=us
initrd  /isolinux/initram.igz
}[/noparse]

---

### Post by arqbrulo on 2009-12-15
Yes, I know you can extract the files and boot them that way from USBs. I just did not want to do that every time a new iso came out. Thanks anyways.

---

### Post by RomanIvanov on 2009-12-16
musarraf172, thanks for sharing correct config! works like a charm!

---

### Post by musarraf172 on 2009-12-17
> **RomanIvanov said:**
> musarraf172, thanks for sharing correct config! works like a charm!

Thanks mate .. Ubuntu Rocks...:guitar:

---

### Post by drs305 on 2009-12-19
> **arqbrulo said:**
> Yes, I know you can extract the files and boot them that way from USBs. I just did not want to do that every time a new iso came out. Thanks anyways.

I spent an hour or so this evening experimenting with the SystemRescueCD iso and GRUB 2. I believe I have found a working solution.

*The following GRUB2 menuentry is for a systemrescuecd.iso located on /dev/sda6 of a 64-bit system.*, in the /iso folder. Tailor your entry to reflect the exact name of the ISO file and ensure the correct device (sdXY) is used. For 32-bit systems, replace [COLOR="DarkRed"]**rescue64**[/COLOR] with [COLOR="Navy"]**rescuecd**[/COLOR] in the "linux" line.

1. Download the SystemRescueCD ISO image from the  [http://www.sysresccd.org/Download]("http://www.sysresccd.org/Download") page. The ISO file does not have to have it's own partition; it can be stored in any folder.
2. Open /etc/grub.d/40_custom or other custom menu file for editing:
```
gksu gedit /etc/grub.d/40_custom
```
3. Add the following menuentry:
> 
menuentry "SystemRescueISO" {
loopback loop (hd**0,6**)/iso/systemrescuecd**-x86-1.3.2**.iso
linux (loop)/isolinux/rescue**64** subdir=/sysrcd docache setkmap=us 
initrd (loop)/isolinux/initram.igz
}
 
This is a **generic menuentry**: edit the menuentry title, iso filename, and rescueXX name (*rescuecd* for 32-bit operation, *rescue64* for 64-bit systems.
> 
menuentry "[COLOR="DarkRed"]TITLE[/COLOR]" {
loopback loop ([COLOR="DarkRed"]hdX,Y[/COLOR])/[COLOR="DarkRed"]path-to-iso-file[/COLOR]/[COLOR="DarkRed"]iso-filename[/COLOR]
linux (loop)/isolinux/[COLOR="DarkRed"]rescueXX[/COLOR] subdir=/sysrcd docache setkmap=us 
initrd (loop)/isolinux/initram.igz
}
 
4. Save the file.
5. Update GRUB 2:
```

sudo update-grub

```

Booting ISOs from Grub 2 is not an exact science for me. Please let me know if this menuentry works for you. If I can get verification from a few users I'll make up a HOWTO for it.


SystemRescueCD Homepage: 
[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

---

### Post by arqbrulo on 2009-12-29
Sorry, but it did not work for me. I also tried adding "cdroot=(loop)" "(loop)/" "/dev/sda1" and a few other options for cdroot to the kernel line and it only gave me a busybox shell. However, if I add root=/dev/ram0 to the kernel line it gives me "The root block device is unspecified or not detected. Please specify a device to boot, or "shell" for a shell..." I think it's a start.

---

### Post by drs305 on 2009-12-29
arqbrulo,

Sorry it didn't work for you. The Grub2/iso issue has been very inconsistent with other users I've tried this with (including the Ubuntu ISOs). The menuentries work for some users but not others, and I haven't been able to find the common link.

If you get it working please post the entry here. Thanks for the update.

---

### Post by pmt on 2009-12-30
Concerning SystemRescueCD: The following is working for me:

menuentry "SystemRescueCd 1.3.3" {
 loopback loop /boot/iso/systemrescuecd-x86-1.3.3.iso
 linux (loop)/isolinux/rescuecd isoloop=/boot/iso/SRCD_ISO rdinit=/linuxrc2 
 initrd (loop)/isolinux/initram.igz
}

The trick is the "rdinit=/linuxrc2" option, explanation for that you could find here: [http://www.sysresccd.org/forums/viewtopic.php?f=14&t=2808](http://www.sysresccd.org/forums/viewtopic.php?f=14&t=2808) 

CAUTION: It works, when I boot from BIOS, it DOES NOT work, if I try booting by qemu. If anyone have any idea, what the reason is for that, please, let me know.

What I also get working is: Ubuntu, Debian, GRML, Parted Magic, Sidux, Slax, Linux Mint, netboot.me, TinyCore, SystemRescueCD, xPUD, memtest.

You could find the grub2 settings (grub.cfg) here:

[http://blog.p-mt.net/wp-content/uploads/2009/12/grub.cfg](http://blog.p-mt.net/wp-content/uploads/2009/12/grub.cfg)

Some explanations and the whole article "MultiBoot USB Stick you could find here:

[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)

[IMG]http://blog.p-mt.net/wp-content/uploads/2009/12/multiboot-usb2.png[/IMG]

unfortunately in German language, 

I also tried Puppy, Backtrack, MoonOS but couldn't get them working. If anybody could help out with that, would be great :-)

---

### Post by drs305 on 2009-12-30
> **pmt said:**
> 

The trick is the "rdinit=/linuxrc2" option, explanation for that you could find here: [http://www.sysresccd.org/forums/viewtopic.php?f=14&t=2808](http://www.sysresccd.org/forums/viewtopic.php?f=14&t=2808) 


Good news!  :-)  

Would you just confirm that you didn't need to manually incorporate the linuxrc2 script into initram.igz? And that the iso you used is the current version of SRCD and not a beta version (which it doesn't appear to be according to the filename)?

Thanks.

---

### Post by pmt on 2009-12-31
> **drs305 said:**
> 
Would you just confirm that you didn't need to manually incorporate the linuxrc2 script into initram.igz? And that the iso you used is the current version of SRCD and not a beta version (which it doesn't appear to be according to the filename)?


That's true: linuxrc2 is already included in initram.igz, and this works with SRCD Vers. 1.3.3 as well as with 1.3.4 (which I just tested some minutes ago):
```

menuentry "SystemRescueCd 1.3.4" {
 loopback loop /boot/iso/systemrescuecd-x86-1.3.4.iso
 linux (loop)/isolinux/rescuecd isoloop=/boot/iso/systemrescuecd-x86-1.3.4.iso rdinit=/linuxrc2 
 initrd (loop)/isolinux/initram.igz
}

```

again: works fine, when booting from BIOS, but didn't work, when I boot via qemu: sudo qemu -m 512 -hda /dev/sdb
in that case, booting fails at a late stage (couldn't find media)

If anybody knows the reason and have a solution for that, would be great :-)

---

### Post by Jongi on 2010-01-02
I have the following for a sidux livecd

> 
menuentry "Sidux 2009-04 LiveCD" {
  insmod ntfs
  set root=(hd1.5)
  loopback loop /distros/sidux-2009-04.iso
  linux (loop)/boot/vmlinuz0.amd fromhd=UUID=7192F19D15BC0C0A fromiso=/dev/sdb5/distros/sidux-2009-04.iso noeject boot=fll vga=791
  initrd (loop)/boot/initrd0.amd

The error I get - [http://img69.imageshack.us/img69/5694/dsc00180c.jpg](http://img69.imageshack.us/img69/5694/dsc00180c.jpg)

---

### Post by ddcc on 2010-01-02
If you're using the Debian netinstall 700mb CD-image, it will boot using loopback, but then it'll fail to mount the cdrom drive and abort. Instead, you'll need to download the hd-media kernel/initrd, and boot that. It'll automatically locate the CD image, and everything should work out fine. Here's what I have:

```
menuentry "Debian 5.03 Netboot i386" {
 linux /boot/debian/vmlinuz vga=normal quiet --
 initrd /boot/debian/initrd.gz
}
```

I've also been able to get DBAN and Offline NT Password & Registry Editor working:

```
menuentry "Darik's Boot and Nuke" {
 loopback loop /boot/iso/dban-beta.2006042900_i386.iso
 linux (loop)/ISOLINUX/DBAN.BZI nuke="dwipe" silent --
}

menuentry "Offline NT Password & Registry Editor 2008-08-02" {
 loopback loop /boot/iso/cd080802.iso
 linux (loop)/VMLINUZ. rw vga=normal --
 initrd /boot/iso/initrd.cgz
}
```

Note that for Offline NT Password & Registry Editor, you'll need to use a modified initrd, because the iso image uses syslinux to boot two initrd images, which GRUB2 doesn't support. You have to manually extract initrd.cgz and scsi.cgz from the iso, then combine them to form one initrd image. Here's a script I wrote to automate the process:

```
mkdir temp
cd temp
gzip -dc < ../INITRD.CGZ | cpio -idum --no-absolute-filenames
gzip -dc < ../SCSI.CGZ | cpio -idum --no-absolute-filenames
find . | cpio -o -H newc > ../initrd.cpio
gzip -c ../initrd.cpio > ../initrd.cgz
cd ..
rm -fr temp
```

Also, there are newer versions of GRUB2 (1.97+20091130-1ubuntu1) and Memtest86+ (4.00-2ubuntu1) available in the Lucid repositories.

---

### Post by pmt on 2010-01-02
> **Jongi said:**
> 
The error I get - [http://img69.imageshack.us/img69/5694/dsc00180c.jpg](http://img69.imageshack.us/img69/5694/dsc00180c.jpg)


I also have problems with Sidux 2009-04, but Sidux 2009-03 works quiet well:

```

menuentry "Sidux 2009-03" {
 loopback loop /boot/iso/sidux-2009-03-momos-xfce-i386-200911110039.iso
 linux (loop)/boot/vmlinuz-2.6.31-6.slh.1-sidux-686 fromiso=/boot/iso/sidux-2009-03-momos-xfce-i386-200911110039.iso boot=fll noeject  
 initrd (loop)/boot/initrd.img-2.6.31-6.slh.1-sidux-686
}

``` 

works like a charm! 
the same thing with Sidux-2009-04 fails:

```

menuentry "Sidux Moros 2009-04 XFCE" {
 loopback loop /boot/iso/sidux-2009-04-moros-xfce-i386-200912310312.iso
 linux (loop)/boot/vmlinuz0.686 fromiso=/boot/iso/sidux-2009-04-moros-xfce-i386-200912310312.iso boot=fll noeject
 initrd (loop)/boot/initrd0.686
}

```

I get the following error message: "[color=red]**failed to identify filesystem type of iso**[/color]"

I discussed that at the Sidux-Forum here: 
[http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&p=147372#147372]("http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&p=147372#147372")

---

### Post by Jongi on 2010-01-05
This eventually worked

```

menuentry "Sidux 2009-04 LiveCD" {
  insmod ntfs
  set root=(hd1.5)
  loopback loop /distros/sidux-2009-04.iso
  linux (loop)/boot/vmlinuz0.amd fromhd=UUID=7192F19D15BC0C0A fromiso=/distros/sidux-2009-04.iso noeject boot=fll vga=791
  initrd (loop)/boot/initrd0.amd
}

```

notice that fromiso doesn't have the device reference

---

### Post by Jongi on 2010-01-05
> **pmt said:**
> That's true: linuxrc2 is already included in initram.igz, and this works with SRCD Vers. 1.3.3 as well as with 1.3.4 (which I just tested some minutes ago):
```

menuentry "SystemRescueCd 1.3.4" {
 loopback loop /boot/iso/systemrescuecd-x86-1.3.4.iso
 linux (loop)/isolinux/rescuecd isoloop=/boot/iso/systemrescuecd-x86-1.3.4.iso rdinit=/linuxrc2 
 initrd (loop)/isolinux/initram.igz
}

```

again: works fine, when booting from BIOS, but didn't work, when I boot via qemu: sudo qemu -m 512 -hda /dev/sdb
in that case, booting fails at a late stage (couldn't find media)

If anybody knows the reason and have a solution for that, would be great :-)

this is the format that worked for me for grub2 and sysrescuecd with the latest stable download.

---

### Post by billybisson on 2010-04-06
Hi all,

I am trying to boot a live iso using grub2 within the Mac EFI with rEFIt (v0.14) as the primary boot menu.

Grub2 is working fine, using refit to load it up. I can boot into the Mac partition without problems from the grub2 menu.

I cannot boot the latest system rescue cd iso or an Ubuntu 8.10 amd64 iso. 

Upon selecting from the grub2 menuitems it finds and reads the respective kernels, it reads the initrd line. But then hangs. It does not go any further. 

Here is what is on the screen before it hangs

[Linux-bzImage, setup=0x3400, size=0x2c09b0]
Video mode: 1280x800-32@59
Display controller:  0:2.0
Device id: 27a28086
MMIO(0) : 0x90380000
VMEM9(2) : 0x80000000
MMIO(3) : 0x90400000
Frame buffer base : 0x80000000
Video line length : 8192
[Initrd, addr-0x5bac7000, size-0x117bd7]

Here is a copy of my grub.cfg

set timeout=10
set default=0
set root=(hd0,2)
menuentry "MacOSX" {
  # Set the root device for Mac OS X's loader.
  root=(hd0,2)
  # Load the loader.
  chainloader /usr/standalone/i386/boot.efi -v
}

menuentry "SystemRescueCd (isoloop)" {
        loopback loop (hd0,4)/systemrescuecd-x86-1.5.1.iso
        linux (loop)/isolinux/rescue64 boot=systemrescuecd-x86-1.5.1.iso subdir=/sysrcd docache setkmap=us isoloop=systemrescuecd-x86-1.5.1.iso initrd=/linuxrc2
        initrd (loop)/isolinux/initram.igz -v
        boot
}

menuentry "Ubuntu 8.10 amd64" {
        set root=(hd0,4)
        loopback loop /Ubuntu_8.10amd64.iso
        linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/Ubuntu_8.10amd64.iso noeject noprompt --
        initrd (loop)/casper/initrd.gz
        boot
}

menuentry "Boot from MBR" {
  appleloader HD
}
menuentry "Boot from CD" {
  appleloader CD
}
menuentry "Boot from USB" {
  appleloader USB
}

menuentry "Microsoft Windows XP" {
        set root=(hd0,3)
        chainloader +1
}


Yet to try and boot Windows as I have not restored the partition and worried about the MBR fudge required.

The current partition for where the iso files live are type vfat.

I did move the systemrescuecd iso within /efi on the Mac partition which left me with the same problem. It locates the linux kernel and initrd fine but hangs after initialising initrd.

Both of the iso files boot fine from their cds.

Is this a problem due to an EFI setup and with no BIOS? Or do I need a boot.efi or something similar as for the Mac OS X menu entry? I am using the latest system rescue cd.

Any help will be great. I like to get all this working and learn about the new EFI system. Yet they boot without problems from cd?

My grub2 installation sits within the /efi folder on my Mac partition. Had to be complied on a Linux box and copied across. I dare not remove refit for grub2 just yet.

Thanks
Will

---

### Post by bond711 on 2010-05-02
> **musarraf172 said:**
> 
menuentry "Ubuntu Server Installer:" {
insmod ntfs
set root=(hd0,6)
loopback loop /Transmission/ubuntu-9.10-server-i386.iso
linux (loop)/install/vmlinuz boot=install isofrom=/dev/hda6/Transmission/ubuntu-9.10-server-i386.iso noeject noprompt --
initrd (loop)/install/initrd.gz
}

I'm attempting to try and put 10.04 server iso's on a grub2 usb key, but keep getting to the point of it failing to mount the cd. Has anyone successfully got 10.04 server working in a loopback?

(I've tried a few different isofroms/isoscan)
cheers

---

### Post by bond711 on 2010-05-05
here is my current entry, but it always fails when it gets to the point of mounting the cd, any advice anyone?

```
menuentry "ubuntu 10.04 server amd64" {
	set isofile="/boot/ubuntu-10.04-server-amd64.iso"
	loopback loop $isofile
	linux (loop)/install/vmlinuz file=/cdrom/preseed/ubuntu-server.seed iso-scan/filename=$isofile --
	initrd (loop)/install/initrd.gz
}
```

---

### Post by deepclutch on 2010-05-06
I am trying to do a fresh install(64-bit) of lucid  from alternate ISO.By copying ubuntu-10.04-desktop-amd64.iso to   / directory of My 9.10 Karmic and with /etc/grub.d/40_custom having lines:
```
 menuentry "UbuntuLucid" {
loopback loop /ubuntu-10.04-desktop-amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-10.04-desktop-amd64.iso noeject noprompt 
initrd (loop)/casper/initrd.lz
 }

```
Ubuntu 9.10 is at sdb5.I want to install on a freshly partitioned ext4 FS at /dev/sdb6.
^ I am able to boot into a livecd like environment(with Gnome GUI).I  formatted sdb6 via gparted.
but ,Ubiquity fails everytime asking to unmount /isomount(IIRC) which is /dev/sdb5 itself.

Is there any workarounds?

---

### Post by alexelprogramador on 2010-05-08
hello

I'm really interested on this post

I had installed grub2 into 8gb usb, and added lot of .iso but, I dint found a way to run pclinuxos in any of the versions:


[LIST]
[*]pclinuxos
[*]minyme
[*]tinyme
[/LIST]


also, there is an interesting version made with lxde

could anybody help me?

thanks for all

---

### Post by surfer on 2010-05-10
same problem here.

for ubuntu, the "desktop" and "netbook" versions work well on my pen drive (loop mounted from the iso), but the "alternate" and "server" editions fail when they try to detect the cdrom.

adding "cdrom-detect/try-usb=true" was no help...

i even extracted dists/ and pool/ from the iso and copied them to the root directory of my pen drive (an ugly workaround). no use. what is cdrom-detect looking for?

someone please find a solution to this!

---

### Post by deepclutch on 2010-05-10
> **surfer said:**
> same problem here.

for ubuntu, the "desktop" and "netbook" versions work well on my pen drive (loop mounted from the iso), but the "alternate" and "server" editions fail when they try to detect the cdrom.

adding "cdrom-detect/try-usb=true" was no help...

i even extracted dists/ and pool/ from the iso and copied them to the root directory of my pen drive (an ugly workaround). no use. what is cdrom-detect looking for?

someone please find a solution to this!
Check this thread:

[http://ubuntuforums.org/showthread.php?t=1475707](http://ubuntuforums.org/showthread.php?t=1475707)

---

### Post by surfer on 2010-05-11
deepclutch, thanks a lot!

it is a bit crude indeed, but it works nicely that way!


for completeness sake, here is what i did:

install grub on the usb stick:
```

$ sudo grub-install --no-floppy --root-directory=/media/boot /dev/sdb

```

copy the .iso to the usb stick (i put them in a iso/ directory).

edit boot/grub/grub.cfg:
```

menuentry "Ubuntu  Alternate 10.04 32bit (lucid lynx)" {
 loopback loop /iso/ubuntu-10.04-alternate-i386.iso
 linux (loop)/install/vmlinuz boot=install iso-scan/filename=/iso/ubuntu-10.04-alternate-i386.iso noeject noprompt --
 initrd (loop)/install/initrd.gz
}

```

for the *desktop* and *netbook* edition, you're good to go. 

for the *server* and *alternate* flavor, you have to follow the following steps during the installation on the target machine:


[LIST=1]
[*]boot from the usb stick
[*]when the installer appears, hit ctrl+alt+F2 and hit enter to activate the console
[*]# mount -t vfat /dev/sdb1 /mnt
[*]# ln -sf /mnt/iso/ubuntu-10.04-alternate-i386.iso /dev/sr0
[*] check:
   # ls -lh  /dev/sr0
   (and repeat the step above if this is not a link to the .iso)
[*]hit ctrl+alt+F1
   to get back to the installer.
[/LIST]

---

### Post by deepclutch on 2010-05-11
^^^ Great to know it Worked :D .BTW ,Ubuntu Desktop CD also can be tried this way.ie ,symlinking device file to iso.But ,for that "Ubiquity"(desktop installer) will have to be as "wise" as Alternate CD. ;) May be someone can test this and report back on that thread.

Regarding CD/DVD Drive's Device File ,New Kernels Mounts all drives irrespective of IDE/SCSI ,are mounted as Serial Devices(/dev/Sr0 ,Sr1..etc)
Thanks

---

### Post by sundar_ima on 2010-06-29
You may want to try **[MultiBootUSB]("http://multibootusb.sourceforge.net/")** script. I have started separate thread regarding it here [http://ubuntuforums.org/showthread.php?t=1518273]("http://ubuntuforums.org/showthread.php?t=1518273"). Pls try and give feedback...

---

### Post by drs305 on 2010-06-29
> **sundar_ima said:**
> You may want to try **[MultiBootUSB]("http://multibootusb.sourceforge.net/")** script. I have started separate thread regarding it here [http://ubuntuforums.org/showthread.php?t=1518273]("http://ubuntuforums.org/showthread.php?t=1518273"). Pls try and give feedback...

Thanks sundar_ima. I'll include a link to your script in my [Grub Basics]("http://ubuntuforums.org/showthread.php?t=1195275") thread.

---

### Post by sundar_ima on 2010-06-29
Pleasure to see [**MultiBootUSB**]("http://ubuntuforums.org/showthread.php?t=1518273") link in your most popular **[Grub Basics]("http://ubuntuforums.org/showthread.php?t=1195275")** thread.

---

### Post by C.S.Cameron on 2010-06-29
> **sundar_ima said:**
> you may want to try **[multibootusb]("http://multibootusb.sourceforge.net/")** script. I have started separate thread regarding it here [http://ubuntuforums.org/showthread.php?t=1518273]("http://ubuntuforums.org/showthread.php?t=1518273"). Pls try and give feedback...

+1

---

### Post by Gemu on 2010-09-14
I have Ubuntu 8.10 booting now by iso. I could not get it to work until I put the iso inside a folder titled iso. Here is my working menuentry

menuentry "ubuntu8.10amd64 (ISO = /dev/sda8)" {
insmod ext2
setroot=(hd0,8)
loopback loop (hd0,8)/iso/ubuntu8.10amd64.iso
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/iso/ubuntu8.10amd64.iso noeject noprompt
initrd (loop)/casper/initrd.gz
}


 I'm trying to understand the linux booting process a little more. Its pretty simple to get the first part of it to load and then either a no file system error or you need to load the kernel first error will kill the process. I was getting a kernel panick message in Ubuntu before putting it in a folder named iso on its own partition.

---

### Post by drs305 on 2010-09-15
> **Gemu said:**
>  I'm trying to understand the linux booting process a little more. Its pretty simple to get the first part of it to load and then either a no file system error or you need to load the kernel first error will kill the process. I was getting a kernel panick message in Ubuntu before putting it in a folder named iso on its own partition.

The system will boot to a certain point before it has to find the files designated by the root command. If the address is wrong, it will come to a halt - it can lead to hopes of success as it initially boots, but will ultimately fail.

The "iso" folder isn't required, you just have to make sure the path is correct for whatever folder contains the ISO. In my experimenting, I've found it's best for me to create whatever the file structure the guide uses as an example until I get it working and know everything is correct. Then I start moving things - and learn from my mistakes. ;-)

---

### Post by Gemu on 2010-09-15
> **drs305 said:**
> The system will boot to a certain point before it has to find the files designated by the root command. If the address is wrong, it will come to a halt - it can lead to hopes of success as it initially boots, but will ultimately fail.

The "iso" folder isn't required, you just have to make sure the path is correct for whatever folder contains the ISO. In my experimenting, I've found it's best for me to create whatever the file structure the guide uses as an example until I get it working and know everything is correct. Then I start moving things - and learn from my mistakes. ;-)


 I thought the iso folder might be required because of whats in the title - IS0 = /dev/sdxx. it sure wouldn't boot without adding it.



 I was trying to get knoppix 5.1 to boot by iso also.  It was trying to boot, now it doesn't even try to start. Im not sure what happened.

Here is the entry maybe you can see some fault in the entry. 

menuentry "KNOPPIX5.1 (ISO = /dev/sda5)" {
insmod ext3
setroot=(hd0,5)
loopback loop (0,5)/iso/KNOPPIX5.1.iso
linux (loop)/boot/isolinux/linux boot=isolinux iso-scan/filename=/KNOPPIX5.1.iso noprompt noeject
initrd (loop)/boot/isolinux/minirt.gz
}

 It got farther by using isofrom=/dev/sd:p/iso/KNOPPIX5.1.iso as opposed to iso-scan.

---

### Post by oldfred on 2010-09-15
What I see, but it may not be everything:

menuentry "KNOPPIX5.1 (ISO = /dev/sda5)" {
insmod ext3
setroot=(hd0,5)
loopback loop ([COLOR=Red]hd[/COLOR]0,5)/iso/KNOPPIX5.1.iso
linux (loop)/boot/isolinux/linux boot=isolinux iso-scan/filename=[COLOR=Red]/iso[/COLOR]/KNOPPIX5.1.iso noprompt noeject
initrd (loop)/boot/isolinux/minirt.gz
}

This was my entry for Maverick in sdc5 (but I boot sdc so it is hd0) and may files are in /boot/ISO in sdc5.

menuentry "Ubuntu 10.10 Maverick 64bit" {
    set isofile="/boot/ISO/maverick-desktop-amd64.iso"
 
    loopback loop (hd0,5)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

---

### Post by drs305 on 2010-09-15
> **Gemu said:**
> I thought the iso folder might be required because of whats in the title - IS0 = /dev/sdxx. it sure wouldn't boot without adding it.


If you mean what's inside the quotes on the "menuentry" line: You can have anything you want inside the quotes of a custom entry. I usually put the device (sda10, etc) just so I can keep track of where it is. But you could have "My ice cream" as the title and if the rest was correct it would still boot.  :-)

---

### Post by musarraf172 on 2010-09-16
Please follow my old reply in this thread!

---

### Post by Gemu on 2010-09-16
> **oldfred said:**
> What I see, but it may not be everything:

menuentry "KNOPPIX5.1 (ISO = /dev/sda5)" {
insmod ext3
setroot=(hd0,5)
loopback loop ([COLOR=Red]hd[/COLOR]0,5)/iso/KNOPPIX5.1.iso
linux (loop)/boot/isolinux/linux boot=isolinux iso-scan/filename=[COLOR=Red]/iso[/COLOR]/KNOPPIX5.1.iso noprompt noeject
initrd (loop)/boot/isolinux/minirt.gz
}

This was my entry for Maverick in sdc5 (but I boot sdc so it is hd0) and may files are in /boot/ISO in sdc5.

menuentry "Ubuntu 10.10 Maverick 64bit" {
    set isofile="/boot/ISO/maverick-desktop-amd64.iso"
 
    loopback loop (hd0,5)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

 When Knoppis 5.1 is booted by cd it mounts its hard drives as /dev/hda and I tryed every variation of all that you can iamgine and still nothing. 

 The error's I get now for this entry are - file doesn't exist, no file system found and you need to load the kernel first.


 I understand the boot= command points to the folder where the kernel resides. In Knoppix 5.1,  minirt.gz is inside /boot/isolinux. Im not sure where vmlinuz is. It may be deep inside the /boot/isolinux/linux compressed image.

---

### Post by bond711 on 2011-06-16
Still no change for the Ubuntu 11.04 Server;
'Incorrect CD-ROM detected'
Would be great if there wasn't mucking around to get it to work.
Desktop works fine.

```
menuentry "ubuntu maverick (11.04) 64-bit install" {
	#set root=(hd0,1)
	#set gfxpayload=keep
	set isofile="/boot/ubuntu-11.04-desktop-amd64.iso"
	loopback loop $isofile
	linux (loop)/casper/vmlinuz file=$isofile/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile noprompt only-ubiquity --
	initrd (loop)/casper/initrd.lz
}

menuentry "ubuntu server (11.04) 64-bit" {
#	set gfxpayload=keep
	set isofile="/boot/ubuntu-11.04-server-amd64.iso"
	loopback loop $isofile
	linux (loop)/install/vmlinuz file=$isofile/preseed/ubuntu-server.seed vga=788 iso-scan/filename=$isofile noprompt --
	initrd (loop)/install/initrd.gz
}
```

---

