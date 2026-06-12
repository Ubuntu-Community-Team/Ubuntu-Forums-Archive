---
title: "Trouble booting from USB 3.0 Device"
date: 2010-11-22
forum: General Help
---

### Post by numb7rs on 2010-11-22
So I've got myself a nice little Atom board and mini case for the perfect HTPC build. Due to the low number of SATA ports on the board, I've chosen to boot from a USB 3.0 Flash drive. A Super Talent 16GB to be precise. Downloaded the Maverick .iso, used unetbootin to put it onto a second USB key, and installed to the Flash drive. No problems so far. Reboot to finish installation, and I get thrown to a BusyBox shell, after being told that it:

```
"Gave up waiting for root device."
```and: 

```
"ALERT! /dev/disk/by-uuid/[hex-code] does not exist. Dropping to a shell!"
```Harumpf.

I have:
- Checked that the correct uuid is given.
- Installed from a CD instead of the USB image.
- Booted a Live CD to check the file system accessibilty of the Flash Drive
- Tried manually loading the linux kernel from within a grub shell.

Note that I'm a bit of a beginner, so may not have done that last bit correctly.

As a last ditch attempt to get it to boot, I moved the drive from a USB 3.0 port to a USB 2 port. The system booted and was perfectly useable.* What.* Using this, I installed all available updates 

Any ideas how I can get this working over USB 3.0?

How can the device not be found when grub was loaded from it? This logic also applies to the motherboard not supporting booting from USB 3.0.


A curiosity: from the grub shell, the drive appears as three partitions:

hd0
hdo,msdos1
hd0,msdos5

Why are these called msdos when Ubuntu formatted the drive in ext4?

---

### Post by oldfred on 2010-11-23
msdos or MBR is the partitioning type. One other alternative is gpt others relate to totally different type of computers. gpt is used by Apple and some Microsoft servers, but windows will not boot from a gpt partitioned drive unless you boot with efi not BIOS. MBR maxs out at 2TiB, so with very large drives you need to convert to gpt.

Not sure why USB3 would not work. It sounds more like a BIOS issue or do you have efi?

---

### Post by numb7rs on 2010-11-23
Thanks for the reply. And for explaining why the partitions are labelled msdos.

I do not have EFI, just a plain BIOS. I cannot find any options relating to USB 3.0 in the BIOS, which is the latest version for the motherboard. If it is the BIOS, then how is grub loaded?

---

### Post by oldfred on 2010-11-23
Computer booting with BIOS & MBR has not really changed for 20 years. It started with just floppy drives, then added hard drives. Hard drives would only boot from the primary master. BIOS was just smart enough to know to jump to the MBR of the primary master hard drive for more code to keep booting. Then they started adding all the other devices as boot devices but a flash drive has a MBR or what looks like a MBR as far as I know. If it works for USB2 I would think it should work for USB3, but do not know what other changes they have made. I thought it was backwards compatible.

---

### Post by numb7rs on 2010-11-23
Yes, the drive is treated as a normal HDD, with an MBR and swap partition. It works fine in USB2, I can't think of a reason it won't in USB 3. As far as the software is concerned, I'd have thought it was just seen as a standard USB drive, but with faster speeds.

---

### Post by schlameel on 2010-12-01
I am experiencing the same problem.  GRUB loads and lets me select the OS to boot.  The Ubuntu boot screen comes up and there is little activity beyond there until the error message comes up.

I have a Thinkpad W510 running Ubuntu 10.10.  The USB ports work once the system is booted, though I only have a 2.0 device in those ports.  I will try to get a Live CD and see if the 3.0 drive works on the 3.0 ports.  

lsusb yields:
```
Bus 003 Device 002: ID 1058:0701 Western Digital Technologies, Inc. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 17ef:480f Lenovo Integrated Webcam [R5U877]
Bus 001 Device 004: ID 0a5c:217f Broadcom Corp. Bluetooth Controller
Bus 001 Device 003: ID 1058:0730 Western Digital Technologies, Inc. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

Bus 003 is the 3.0 ports, I have a second USB drive plugged in there.

usb-devices seems to recognize the bus as 3.0:
```
T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=5000 MxCh= 4
D:  Ver= 3.00 Cls=09(hub  ) Sub=00 Prot=03 MxPS= 9 #Cfgs=  1
P:  Vendor=1d6b ProdID=0003 Rev=02.06
S:  Manufacturer=Linux 2.6.35-23-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:0f:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
```

Perhaps the issue is GRUB?  I'll do what I can to track that down.

---

### Post by numb7rs on 2010-12-03
Hi schlameel, nice to know I'm not the only one.

What sort of device are you trying to boot from?

Doing some diggin, the W510 has an NEC USB 3.0 chipset, same as my motherboard. I have a suspicion this may be a driver related issue. I have been unable to find any standalone drivers for ubuntu for this chipset, as they're supposed to be included in the kernel. I'm going to keep digging.

Let me know if you have any luck.

numb7rs

---

### Post by schlameel on 2010-12-15
Good find.  I am using a Western Digital Passport I think.  1TB drive partitioned with about 100 GB for Ubuntu.

---

### Post by mgscox on 2010-12-21
> **numb7rs said:**
> ... Reboot to finish installation, and I get thrown to a BusyBox shell, after being told that it:

```
"Gave up waiting for root device."
```and: 

```
"ALERT! /dev/disk/by-uuid/[hex-code] does not exist. Dropping to a shell!"
```Harumpf.


I have exactly the same situation, so it's not you - as far as I can tell, you can't boot Ubuntu from an external USB3 HDD. 
Incidentally, Ubuntu can see USB3 drives, just can't boot from them; boot from a live CD and you'll see that drive is recognised and available. It seems to indicate to me that the problem specific to booting and  buried deep within the bootstrap or kernel.
I've searched the interweb high and low and no-one has so far indicated they've been successful.
Hopefully that last sentence will prompt someone to confirm that they've done it, so we can all then quiz them how they achieved it :)

---

### Post by gordintoronto on 2010-12-21
Is the flash drive a Super Talent Express DUO 16 GB?

---

### Post by numb7rs on 2010-12-21
> **gordintoronto said:**
> Is the flash drive a Super Talent Express DUO 16 GB?Why yes, I believe it is. Is this a known issue then?

---

### Post by gordintoronto on 2010-12-22
> **numb7rs said:**
> Why yes, I believe it is. Is this a known issue then?

No, I just thought it might be useful to identify the exact hardware.

I don't have access to any USB 3 hardware.

---

### Post by rkolb86 on 2011-01-10
I'm not very knowledgeable on the subject, but during my research in purchasing a new mobo, USB 3 is supported, but booting from USB3 is not. 


Just what I read...could just be old info.

---

### Post by hvanmunster on 2011-01-16
I don't know if this can help, but I have the impression that the system swaps from the USB 3.0 port to the USB 2.0 port during boot.

I have connected 2 external USB drives _at the same_ time on my pc. Both drives are made bootable (ubuntu 10.10 i386 placed with the usb-installer). One drive is connected to the usb 2.0 port, the other to the usb 3.0 port.
In this configuration I am able to force the computer (via bios settings) to start booting on the usb 3.0 port. The boot procedure runs fine until complete boot, but somewhere in the middle, the system takes the drive on the usb 2.0 port. 
I noticed this because I chose a different desktop background on both systems. Apart from that they are identical.
When I force the pc to boot from usb 3.0, I always obtain the background of the system that is on the usb 2.0 port.

PC : HP elitebook 8540w (64 bit processor, I chose ubuntu i386 for portability reasons)
Drive on usb 2.0 : Lacie 300 GB
Drive on usb 3.0 : Western Ditgital MyPassport 500 GB
Both drives are tested individually on different computers with a usb 2.0 port. They are both working fine if connected to a usb 2.0 port.

---

### Post by hvanmunster on 2011-01-16
I don't know if this can help, but I have the impression that the system swaps from the USB 3.0 port to the USB 2.0 port during boot.

I have connected 2 external USB drives _at the same_ time on my pc. Both drives are made bootable (ubuntu 10.10 i386 placed with the usb-installer). One drive is connected to the usb 2.0 port, the other to the usb 3.0 port.
In this configuration I am able to force the computer (via bios settings) to start booting on the usb 3.0 port. The boot procedure runs fine until complete boot, but somewhere in the middle, the system takes the drive on the usb 2.0 port. 
I noticed this because I chose a different desktop background on both systems. Apart from that they are identical.
When I force the pc to boot from usb 3.0, I always obtain the background of the system that is on the usb 2.0 port.

PC : HP elitebook 8540w (64 bit processor, I chose ubuntu i386 for portability reasons)
Drive on usb 2.0 : Lacie 300 GB
Drive on usb 3.0 : Western Ditgital MyPassport 500 GB
Both drives are tested individually on different computers with a usb 2.0 port. They are both working fine if connected to a usb 2.0 port.

---

### Post by kiyop on 2011-02-19
I set Buffalo IFC-PCIE2U3 USB 3.0 interface board with my PC and connected USB 3.0 HDD; pqi Portable HDD H566.

I downloaded
[http://cdimage-u-toyama.ubuntulinux.jp/releases/10.10/ubuntu-ja-10.10-desktop-i386.iso](http://cdimage-u-toyama.ubuntulinux.jp/releases/10.10/ubuntu-ja-10.10-desktop-i386.iso)
and burned to CD-R.

I booted with the burned CD-R. The USB-3.0HDD was found.

I installed Ubuntu into the partition made in USB-3.0HDD.
Both of Grub2 installation to MBR of the USB-3.0HDD and to PBR of the installed partition were failed.
So, I continued without installation of Grub2.

I restarted.
In BIOS settings screen, the USB-3.0HDD could not be found. 

I booted with Ubuntu installed in the internal HDD of my PC.

$ lsmod
displayed
> xhci_hcd
...
usbhid
hid
usb_storage
...I change-root into the installed partition (/dev/sdf1) of the USB-3.0HDD.
$ sudo mount -t ext4 /dev/sdf1 /mnt -o rw
$ sudo mount --bind /dev /mnt/dev
$ sudo mount --bind /sys /mnt/sys
$ sudo mount --bind /proc /mnt/proc
$ sudo chroot /mnt /bin/bash

First, I updated.
/# apt-get udpate
/# apt-get upgrade

Many packages were failed to be updated and there came many error messages.

I added the following lines:
> xhci_hcd
usbhid
hid
usb_storageto
/etc/initramfs-tools/modules

/# nano /etc/initramfs-tools/modules

I generated initramfs.
/# mkinitramfs -o /tmp/initramfs-$(uname -r)
/# mv /boot/initrd.img-2.6.35-25-generic-pae /boot/initrd.img-2.6.35-25-generic-pae-backup
/# mv /tmp/initramfs-2.6.35-25-generic-pae /boot/initrd.img-2.6.35-25-generic-pae

/# exit
$ sudo umount -l /mnt/dev
$ sudo umount -l /mnt/sys
$ sudo umount -l /mnt/proc

I mounted a partition, where BIOS can access, in the internal HDD to /media/windows. 
I copied generated initramfs and kernel into the partition.

$ cp /mnt/boot/initrd.img-2.6.35-25-generic-pae /mnt/boot/vmlinuz-2.6.35-25-generic-pae /media/windows/

I set up grub4dos-0.4.4 to the windows 7 system partition (/media/windows).
I copied grldr into /media/windows and edit /media/windows/menu.lst:
> title ubuntu on USB3.0HDD
kernel /vmlinuz-2.6.35-25-generic-pae root=UUID=[COLOR=red]UUID of the partition where ubuntu was installed[/COLOR] ro
initrd /initrd.img-2.6.35-25-generic-paeI added the grub4dos entry with BCDedit.

I restarted and select grub4dos with Bootmgr.

The GNOME of ubuntu installed in USB-3.0HDD successfully started.

In this case, the kernel and initramfs should be in the partition where BIOS (grub4dos) can access, in the internal HDD.

I wrote my own init script.
I involved my init script, "kexec-tools", "dialog", "file" and so on into initramfs.
Now, I can boot Ubuntu on a partition in USB-3.0HDD without the existence of the very kernel and initramfs in the internal HDD.

---

### Post by citium on 2011-03-07
kiyop your a legend.

I was looking for way to do what you did.

I have an ENYO 128GB and it refuse to boot.
I know the mother board dont support booting from usb.
So I made the ubuntu install the boot partition on usb2 and everything else on usb3. But it can't detect usb3 after the kernel is loaded.

Finger cross, I'll try kiyop solution tomorrow.

---

### Post by kiyop on 2011-03-08
I wish you will succeed.
Incorporation of correct necessary modules into initramfs is key point.

If you want to keep your kernel and initramfs of Ubuntu inside the partition in USB3.0 device, [this link]("http://kiyoandkei.blog68.fc2.com/blog-entry-47.html") may help you. It should be noticed that both initramfs'es of kernel loader (kiyoshi's help) and Ubuntu itself must have the correct modules.

---

### Post by kiyop on 2011-03-09
> **citium said:**
> So I made the ubuntu install the boot partition on usb2 and everything else on usb3. 

If you made /boot partition separately from / partition, you should mount /boot partition correctly so that you can "mkinitramfs" correctly in chroot circumstance.

I do not prefer separating /boot partition from / partition.

---

### Post by DannyLi on 2011-03-13
I can confirm kiyop's solution works. the principle is use a initramfs & kernel in the internal hard drive with usb 3 support to boot the external usb 3 hard drive.

but if you are using a kernel under 2.26.34, you need xhci module instead of xhci_hcd as xhci was renamed to xhci_hcd since 2.26.34.

my kernel is 2.6.32-29-generic,  so my /etc/initramfs-tools/modules file has the following lines:
xhci
usbhid
hid
usb_storage

good luck to everyone and enjoy the usb 3.0 speed.

---

### Post by meloade on 2011-03-13
> **numb7rs said:**
> So I've got myself a nice little Atom board and mini case for the perfect HTPC build. Due to the low number of SATA ports on the board, I've chosen to boot from a USB 3.0 Flash drive. A Super Talent 16GB to be precise. Downloaded the Maverick .iso, used unetbootin to put it onto a second USB key, and installed to the Flash drive. No problems so far. Reboot to finish installation, and I get thrown to a BusyBox shell, after being told that it:

```
"Gave up waiting for root device."
```and: 

```
"ALERT! /dev/disk/by-uuid/[hex-code] does not exist. Dropping to a shell!"
```Harumpf.

I have:
- Checked that the correct uuid is given.
- Installed from a CD instead of the USB image.
- Booted a Live CD to check the file system accessibilty of the Flash Drive
- Tried manually loading the linux kernel from within a grub shell.

Note that I'm a bit of a beginner, so may not have done that last bit correctly.

As a last ditch attempt to get it to boot, I moved the drive from a USB 3.0 port to a USB 2 port. The system booted and was perfectly useable.* What.* Using this, I installed all available updates 

Any ideas how I can get this working over USB 3.0?

How can the device not be found when grub was loaded from it? This logic also applies to the motherboard not supporting booting from USB 3.0.


A curiosity: from the grub shell, the drive appears as three partitions:

hd0
hdo,msdos1
hd0,msdos5

Why are these called msdos when Ubuntu formatted the drive in ext4?

I think you just need to extend the timeout time in the bios.

There's a certain amount of time the bios gives a device to find the OS before it times out and goes straight to the next device in the boot order sequence. Extending that time should do the trick.

---

### Post by kiyop on 2011-03-14
I do not know well about "BIOS timeout".

The following messages are neither given by BIOS nor GRUB, but given by kernel & initramfs.
```
"Gave up waiting for root device."
``````
"ALERT! /dev/disk/by-uuid/[hex-code] does not exist. Dropping to a shell!"
```I think the option for kernel: "rootdelay=[COLOR=red]time for waiting in seconds[/COLOR]" may help, but "BIOS timeout" may not.

---

### Post by kiyop on 2011-03-14
The name of necessary module for USB-3.0 device must be checked by "lsmod" as is written in [#16]("http://ubuntuforums.org/showpost.php?p=10472525&postcount=16").

To: DannyLi
Thank you :smile: for reporting that module name "xhci" should be used instead of "xhci_hcd" for older kernel than 2.6.34.

---

### Post by a_biswas on 2011-07-04
Hi,

I also tried a lot on this issue in different ways with different distributions only one success I got


[LIST=1]
[*]MBR & /boot partition I kept iin my internal HDD (hd0)
[*]From the grub.conf of that /boot partition I have given the grub menu entry for the other Linux distributions (Fedora 15, Debian, Ubuntu) present in my external HDD (WD 1TB USB-3.0)
[/LIST]
All OS works perfectly if I am connecting my WD 1TB USB-3.0 HDD to my native USB-2.0 port but **only Debian works properly if I am connecting the same external HDD to my USB-3.0 (NEC chip express card) port**.

None of OS directly boots from the same HDD directly if I keep the MBR to the same external HDD. But I have another Seagate USB-2.0 HDD, which can directly boot pre-installed Linux (Dreamlinux & Ubuntu) from that external HDD.

Thinking that this is the problem related to process of loading the kernel as Debian at least worked indirectly.

Please inform if someone gets some other alternative.

---

### Post by a_biswas on 2011-07-04
Another information to be mentioned as I found NEC chipset USB-3.0 controllers are not bootable
[http://wiki.digitus.de/en/USB](http://wiki.digitus.de/en/USB)

So booting from internal HDD and referring external HDD is only the option for running Linux on external HDD with USB-3.0.

---

### Post by a_biswas on 2011-07-04
Hi,

I also tried to use the debian kernel directing to ubuntu '/' partion but no success for ubuntu

---

### Post by cobradevil on 2011-07-14
not sure but if you are on ubuntu 10.10 or later you can try:

vi /etc/initramfs-tools/modules

and add the xhci-hcd module

then run update-initramfs -u and use that initrd
Also make sure you are using the same kernel on the usb drive as the initrd that you are building here

so copy the /boot/initrd-xxxxxx.img to the usb drive /xxx/initrd-xxxxxx.img
and also the kernel /boot/vmlinuz-xxxxx to the usb drive /xxx/vmlinuz-xxxxx

the sync umount and try to boot from the usb device in your usb 3.0 controller.

I have no hands on usb 3.0 hardware but i think that should work

With kind regards

William

---

### Post by kiyop on 2011-07-29
> **cobradevil said:**
> if you are on ubuntu 10.10 or later you can try:

vi /etc/initramfs-tools/modules

and add the xhci-hcd module

then run update-initramfs -u and use that initrd
+1

And if you use another distro, you should include correct module like xhci-hcd which enables USB-3.0 into initramfs and use the initramfs.

Even if some boot loader or kiyoshi's help can access USB-3.0, you cannot boot the distro if the kernel loaded with the loaded initramfs cannot access USB-3.0 device.

---

### Post by Gutta Perka on 2011-10-10
I'll pay for an almost ready cd-image from wich I can "softboot" my Iomega ego on the USB 3 port.

So far I have managed to do a "hardboot" with the the hd connected to the usb 2 port direct into ubunto.

Nor have I time nor the scill to do such a cd-image.


That is - I would like to boot a cd which then softboots through the usb 3 port.
Does Ubunto 11.04 have the drivers for USB 3 built in for running the OS?

/Love from Sweden

---

### Post by kiyop on 2011-10-10
Does BIOS on your computer recognize your Iomega ego (USB-HDD?) on the USB 3 port as a bootable media?
You can search on BIOS configuration (Boot order, and HDD configuration).

If not recognized, one way to boot linux on USB3.0 HDD is to put linux kernel loader in a partition which BIOS (and loaded kernel loader) can access.

In my case, unfortunately my USB3.0 port cannot be recognized by BIOS on one of my computers. PLoP could not boot it. Super Grub Disk could not boot it.
But my tool enables boot from a partition on my USB-3.0 HDD connected to USB 3.0 port.
My tool utilizes grub4dos and kexec-tools.
[http://kiyoandkei.blog68.fc2.com/blog-entry-52.html](http://kiyoandkei.blog68.fc2.com/blog-entry-52.html)

> **Gutta Perka said:**
> I'll pay for an almost ready cd-image from wich I can "softboot" my Iomega ego on the USB 3 port.
You need not pay. You can make and set up by yourself if you have will to learn.

> **Gutta Perka said:**
> 
Nor have I time nor the scill to do such a cd-image.
You need not use cd-image. You can install ubuntu into a partition in the external USB3.0 HDD with usual way like installing on a partition in an internal HDD.

> That is - I would like to boot a cd which then softboots through the usb 3 port.
Does Ubunto 11.04 have the drivers for USB 3 built in for running the OS?Kernel module "xhci-hcd" or so.

---

### Post by Gutta Perka on 2011-10-11
OK!

Thanks for your care.

Computer Dell Inspiron 630m - laptop with Win XP on ATA slow 80 gig disk. Outdated that is!

I have for my own learning on USB2 Ubuntu on  the Iomega disk (USB2 very slow) while I cannot boot it on nec USB3 expresscard. ( Tested: the Iomega 1 TB is 3-4 times faster than the 80 gig built in ATA 80 gig disk.)

While the partitions ( 1 main and a swap one) for ubuntu are formated with xt3 windows will not see them.) But I'm locked in to USB2 for running , working with Ubuntu.

So for running another linux to make changes in I must either make new partition on the Iomega on the USB2 port OR if it is possible boot an USB2 stick with Debian and the files/progs you directed me. (Debian I hope is not too "faar" from Ubuntu?

Questions: Are there Debian USB under 8 gig to be run from an USB stick and doing the preparations you directed me to? Then I could boot USB3 Iomega from there? Obvious if so I would like that solution - to start the Iomega on USB3 Debian on 8 gig memorystick. Perhaps booting from USB2 Debian also could be "automated".

This qustions are just the begining - the hardware.
The Ubunto and Debian addons is another question and I prosume a long learning curve in that area.

There are computers everywhere!
With the little Iomega and a USB-stick I could I could boot Ubuntu everyware - not scaring others from destroying there windows XP/7. 
That is fi my scills and time can get me there.


Again thanks!



I

---

### Post by kiyop on 2011-10-12
Thanks for your giving me much information on your problem.

There are many possible ways to boot Ubuntu on Iomega via USB 3.0 expresscard.

I write one way without using debian below. If you prefer another way, tell me so.

Connect your Ubuntu USB3.0 media (Iomega?) to USB2.0 port without connecting anything to USB 3.0 port (nec USB3 expresscard) and boot Ubuntu form Iomega. Then execute in terminal
```
lsmod|sort| tee module1
```Then connect USB stick to nec USB3.0 expresscard and execute
```
lsmod |sort|tee module2
diff -B module1 module2|grep \>|sed -e "s/^> //"
```Confirm xhci or such module name(s) is/are shown.
If nothing shown, please post the result of
```
lsmod
```If something (modules for USB3.0 port) are shown, go ahead.```
gksu gedit /etc/modules
```and add the modules shown and save.
```
gksu gedit /etc/initramfs-tools/modules
```and add the modules shown and save.

Then
```
sudo update-initramfs -u
sudo update-grub
```You should know the UUID of the Ubuntu / partition of your USB3.0HDD (Iomega)
```
sudo blkid $(mount|grep " / "|cut -d " " -f1)
```The UUID is shown after
UUID=
Neglect double quotation.

Mount the windows xp system partition and copy the current kernel and its initrams files into the root directory of the windows xp system partition.
The version of the current kernel is shown by
```
uname -r
```and the current kernel is like,
/boot/vmlinuz-...
The initramfs is like,
/boot/initrd.img-...

Download
[http://sourceforge.net/projects/grub4dos/files/GRUB4DOS/grub4dos%200.4.4/grub4dos-0.4.4.zip/download?_test=goal]("http://sourceforge.net/projects/grub4dos/files/GRUB4DOS/grub4dos%200.4.4/grub4dos-0.4.4.zip/download?_test=goal")
and decompress it by commands like
```
unzip [path]/grub4dos-0.4.4.zip
```Copy the following files in the decompressed directory.
grldr
grub.exe
menu.lst

Execute:
```
sudo sync
```And reboot and boot windows xp.

Add the following line to c:\boot.ini[FONT=monospace]
[/FONT]c:\grldr="grub4dos"

Add the following lines to c:\menu.lst
title ubuntu on Iomega
kernel /vmlinuz-... root=UUID=#### ro
initrd /initrd.img-...

The above "..." should be replaced with the version of the current kernel.
The above "####" should be replaced with the UUID of the ubuntu / partition.

Save c:\boot.ini and c:\menu.lst.

Shutdown and connect USB3.0HDD (Iomega) to nec USB3.0 card.

Boot and press F8 or Ctrl key to display the windows boot list menu.
Select
grub4dos

and then with arrow-down key, select
ubuntu on Iomega

God bless you!

=============
Below is my reply to your question.

> **Gutta Perka said:**
> So for running another linux to make changes in I must either make new partition on the Iomega on the USB2 port OR if it is possible boot an USB2 stick with Debian and the files/progs you directed me. (Debian I hope is not too "faar" from Ubuntu?
You can boot Debian liveUSB from USB2 stick.
Commands available in Debian is similar to those available in Ubuntu.

> **Gutta Perka said:**
>  Questions: Are there Debian USB under 8 gig to be run from an USB stick and doing the preparations you directed me to?
Yes.
[http://cdimage.debian.org/debian-cd/current-live/i386/iso-hybrid/debian-live-6.0.2-i386-lxde-desktop.iso](http://cdimage.debian.org/debian-cd/current-live/i386/iso-hybrid/debian-live-6.0.2-i386-lxde-desktop.iso)
Download the above and dd to USB2 stick. That is...
```
sudo parted -l
```to confirm the device file name (such as /dev/sdb) of your USB2 stick.
```
sudo dd if=[path]/debian-live-6.0.2-i386-lxde-desktop.iso of=/dev/sdb
```You should change the above "sdb" to correct one for USB2 stick. If you write wrong one, your windows xp or your ubuntu may be broken totally.

> **Gutta Perka said:**
>  Then I could boot USB3 Iomega from there?
Yes, if you incorporate correct modules for USB3.0 port into the initramfs of Ubuntu on Iomega and copy the Ubuntu kernel and the initramfs in a partition where your BIOS can access and set up linux kernel loader correctly.

Again I want to ask you the following:
[quote=kiyop]Does BIOS on your computer recognize your Iomega ego (USB-HDD?) on the USB 3 port as a bootable media?
You can search on BIOS configuration (Boot order, and HDD configuration).[/quote]

---

### Post by Gutta Perka on 2011-10-12
I deeply thanks you!
I just went by the laptop and did see your new contribution.

You asked:
 					Originally Posted by **kiyop** 					 				
 				[I][B]Does BIOS on your computer recognize your Iomega ego (USB-HDD?) on the USB 3 port as a bootable media?
You can search on BIOS configuration (Boot order, and HDD configuration).[/B]
[/I]

The answer is a strong NO! 

As I mensioned earlier - the computer is an "old" laptop: A dell inspiron 630m intruduced
around 2005 - but has a good processor and 1.5 gig memory. Primitive perhaps but still doing fine. The real shortcoming is the small and slow ATA drive (75 Gig). That was to be cured by the fast usb3 port and the fast usb 3 Iomega and the ability to run other OS-es.

As said also earlier: *Neither have I the time nor the scills*

However - now you have tagged me!
Time is to be streched and scills are to be bettered!

---

### Post by Gutta Perka on 2011-10-12
By the way!

Beeing in the grossary shop (!!) I bought an extra 7 dollar 8 gig USB stick.
Then I did put a "Bootable Live Debian on it" (A sort of CD Live Debian)
In that OS I can make real intime changes and save them - which I cannot on a CD.

Intresting to see is that Debian can see the Iomega (give me a folderlook) - but can,t use it. But I'm totaly unable to mount it or use the Iomaga in any way.

Anyhow - LiveDebian sees something.
That means the drivers are there but they are to primitive!

OK?

---

### Post by kiyop on 2011-10-12
> **Gutta Perka said:**
> As said also earlier: *Neither have I the time nor the scills*
I could not understand the meaning of the word "scills".
I have gotten it. "skills". I see.

> **Gutta Perka said:**
> Intresting to see is that Debian can see the Iomega (give me a folderlook) - but can,t use it. But I'm totaly unable to mount it or use the Iomaga in any way.

Anyhow - LiveDebian sees something.
That means the drivers are there but they are to primitive!

OK?
:confused:
You could not mount it....
What is shown if you execute the following in the terminal in Live Debian just after inserting the Iomega into the USB3.0 port?
```
dmesg|tail
mount
sudo su
blkid
fdisk -lu
lsmod
```
You can copy the result and post it in this forum by LiveDebian, do not you?

---

### Post by Gutta Perka on 2011-10-12
Yep!

I cant write everything coming out of that.
Trying to take what I think is important:

Notes and from memory.

[B]hdmesd|tail
[/B][sdb]ATTACHED scsi generic sg2 type 0
........15974744 512-byte logicalblock 8.17GB/........
........writeprotect is of
........cashe write through
........Attached scsiremovable disk
**mount**
.......rootfs on /type rootfs lrw
.......noneon/proc typeproc (rw, realtime)
.......none on /type sysfs (rw, realtime)
.......tmpfs on /dev type sysfs (rw, realtime)
....... on /dev/pts typedevpts
**sudo su**
......./bin/sh: not found
**blkid**
.......dev/sda1:"EE0C69080C6......" Type NTFS
.......dev/sdb1:sec_TYPE="msdos" Label "Debian Live uuid="E88B-9321" Type="vfat"
**fdisk -lu**
/bin/sh: not found
**lsmod**
#......................
#Much Much - your famous uhci_hcd
#................... here som....
......much of uhci_hcd
more hrdwar referenses drivers
......usbcore usbhid
......usb_storage
......uhci_hcd
......ehci_hcd
......ahci

Missed a lot there!!!!

But it might be enought for you?

---

### Post by kiyop on 2011-10-13
> **Gutta Perka said:**
> I cant write everything coming out of that.
Trying to take what I think is important:

...

Notes and from memory.
Could you view this page on debian in USB flash?
As I wrote:
> **kiyop said:**
> You can copy the result and post it in this forum by LiveDebian, do not you?
I can drug the result shown on terminal and right-click to copy the result and then I can open this forum and paste the result by right-click and selecting "paste" and post the result.
You need not write down nor memorize. 

> **Gutta Perka said:**
> **hdmesd|tail**
Huh? :confused:
I did not suggested you to execute "hdmesd".
> **kiyop said:**
> ```
dmesg|tail
```
But,...
> **Gutta Perka said:**
> [sdb]ATTACHED scsi generic sg2 type 0
 ........15974744 512-byte logicalblock 8.17GB/........
 ........writeprotect is of
 ........cashe write through
 ........Attached scsiremovable disk
I hope you certainly executed "dmesg|tail". Then, USB 3.0 HDD (Iomega) is not accessed.

> **Gutta Perka said:**
> 
 **mount**
 .......rootfs on /type rootfs lrw
 .......noneon/proc typeproc (rw, realtime)
 .......none on /type sysfs (rw, realtime)
 .......tmpfs on /dev type sysfs (rw, realtime)
 ....... on /dev/pts typedevpts
Did you really inserted the Iomega on USB 3.0 port and then executed "mount" on debian?

 > **Gutta Perka said:**
> 
  **sudo su**
 ......./bin/sh: not found
Did you really downloaded [http://cdimage.debian.org/debian-cd/current-live/i386/iso-hybrid/debian-live-6.0.2-i386-lxde-desktop.iso](http://cdimage.debian.org/debian-cd/current-live/i386/iso-hybrid/debian-live-6.0.2-i386-lxde-desktop.iso) , which I recommended, and executed "dd" to write to your USB 8.17GB flash?
> **kiyop said:**
> 
[http://cdimage.debian.org/debian-cd/current-live/i386/iso-hybrid/debian-live-6.0.2-i386-lxde-desktop.iso](http://cdimage.debian.org/debian-cd/current-live/i386/iso-hybrid/debian-live-6.0.2-i386-lxde-desktop.iso)
Download the above and dd to USB2 stick. That is...
```
sudo parted -l
```to confirm the device file name (such as /dev/sdb) of your USB2 stick.
```
sudo dd if=[path]/debian-live-6.0.2-i386-lxde-desktop.iso of=/dev/sdb
```You should change the above "sdb" to correct one for USB2 stick. If you write wrong one, your windows xp or your ubuntu may be broken totally.
I have one USB flash which I dd'ed [http://cdimage.debian.org/debian-cd/current-live/i386/iso-hybrid/debian-live-6.0.2-i386-lxde-desktop.iso](http://cdimage.debian.org/debian-cd/current-live/i386/iso-hybrid/debian-live-6.0.2-i386-lxde-desktop.iso) .
I booted with the USB flash and executed "sudo su" in "LXterminal" or "Root Terminal".
In both terminals, it did not reply "/bin/sh: not found" but replied "/home/user#" which means I got root privilege.
I think you did what I did not suggest.

 > **Gutta Perka said:**
> **blkid**
 .......dev/sda1:"EE0C69080C6......" Type NTFS
 .......dev/sdb1:sec_TYPE="msdos" Label "Debian Live uuid="E88B-9321" Type="vfat"
:confused:
Huh.....
In my case, "blkid" gives
/dev/sdc1: LABEL="Debian squeeze 20110828-00:37" TYPE="iso9660"
/dev/loop0: TYPE="squashfs"

Again I think you did what I did not suggest.

 > **Gutta Perka said:**
> **fdisk -lu**
 /bin/sh: not found
Again I think you did what I did not suggest.

I want to know the detail of the situation.
> **Gutta Perka said:**
> Intresting to see is that Debian can see the Iomega (give me a folderlook) - but can,t use it. But I'm totaly unable to mount it or use the Iomaga in any way.

If you cannot understand how to do what I suggested, please let me know.

---

### Post by Gutta Perka on 2011-10-13
Sorry -Sorry.
I could not keep up with you.

What I did was what you asked me to do in another earlier post.

The post you are referring to -** I have printed it that out**.
To learn - I study all the commands in the manual for a bit
of better understanding you - trying to better my sKills.
See - I spelled Skills right here - that is a sign of better skill being here.

There is a certain differens using Open Word in Ubuntu  vs rebulding the OS
and changing devices in the kernel with unsupported hardware devices/drivers.
But ... I'm working on it.

So now I ask you - please be patient.
**I love you helping me to another level.**

So what do you say about this testrig.

(Iomega contains importent backups - in a way
now, I should have one more Iomega to test on!)
[B]
1-Windows XP left on the laptop HD.
2-Debian Live booted on USB2 port
3-Hirens boot usb on USB3[/B]  ( [http://www.hiren.info/](http://www.hiren.info/) )

**Then go throu your exellent three page instructions.**

If it works with that simple setup it should with the Iomega. (?)

I see I must learn how to keep my results first.

How do I easely start a logfile of  of an whole terminal session.

In the sixties and seventies (Yes I was a pioneer then programming FORTRAN
but that is another story) 64 **kb** ram in total for OS, progs and multitasking.
There I recall was a "command xy > /dev/lib/file" to save
the result and not using the the teleprinter used by others (Piping????).

For me it like beeing dead for fourty-fifty years beeing away from UNIX
on the computer center at Lund Technical University.
In a way, this Linuxing, is a way to recall those days again.
Lots of dejavus here now! 

Again sorry for not keeping up with you. Yes I have a job as well.

**I love you helping me!**

But give me time to keep up with you.
I'm tagged now and wants to understand at least partsof what I'm doing.

I'm sure it would be a waste of time me just being a sort of zomby typing
down curious UNIX letters and hitting carriage return.
It also would be an offens to me having a MsC - Engineering.


I hope for and long for your FINE guidens!
Don't give up.

Regards
Gutta
[]("http://www.google.se/search?hl=sv&client=firefox-a&hs=Pkf&rls=org.mozilla:sv-SE:official&sa=X&ei=gdSWTsO5MMXN4QSb0sj4Aw&ved=0CBkQvwUoAQ&q=carriage+return&spell=1")

---

### Post by kiyop on 2011-10-13
> **Gutta Perka said:**
> What I did was what you asked me to do in another earlier post.

The post you are referring to -** I have printed it that out**.
To learn - I study all the commands in the manual for a bit
of better understanding you - trying to better my sKills.
See - I spelled Skills right here - that is a sign of better skill being here.

...

So now I ask you - please be patient.
**I love you helping me to another level.**
OK! Excuse my hurrying you.

> **Gutta Perka said:**
> (Iomega contains importent backups - in a way
now, I should have one more Iomega to test on!)
[B]
1-Windows XP left on the laptop HD.
2-Debian Live booted on USB2 port
3-Hirens boot usb on USB3[/B]  ( [http://www.hiren.info/](http://www.hiren.info/) )
You need not buy a new one.
You need not change your current Iomega so much.
Just add necessary modules into Ubuntu initramfs.
You will not lose your data.

> **Gutta Perka said:**
> How do I easely start a logfile of  of an whole terminal session.
As you wrote, redirection, for example, ">" is useful.
To save the standard error also with the standard output into a file (out.txt),
```
COMMAND > out.txt 2>&1
```Also, "tee" is useful. "tee" writes the output into both of the standard output and a file.
```
COMMAND | tee out.txt
```But, if you use gnome-terminal, LXTerminal or so, it is easier to drug what you want to copy and right-click and select "Copy" and paste by right-click and selecting "paste", as I wrote.

If you use Xterm, you can drug what you want to copy and middle-click where you want to paste it.

Do not you use GUI?
Do you use tty1-6?

***OFF TOPIC***
This topic gradually changes to "How to use terminal - basic skill" rather than how to enable booting from USB 3.0 ;)

---

### Post by Gutta Perka on 2011-10-13
You wrote:
*This topic gradually changes to "How to use terminal - basic skill" rather than how to enable booting from USB 3.0 :wink:*

That one hit!
I feel ashamed!! Sorry!

But I don't want to lose you!

OK - better me being frank and display myself as is.

I asure you - I'm a fast learner.
The rest of the evening and part of the night
will be on Terminaldrilling.
I listened to you - so there will be lots of trial and error work for me.
Your hints are exelent!

Last time using UNIX there was no VGA just Terminals, just loadely teletypers  with notched paper and of cause the thousends of punched card.

Just one punch wrong and you manualy sat there wondering what punchhole that was wrong. Tuff low level jobb. You could wait for hours to be permitted to use the
punched card reader. And that computercenter (IBM) was one of the modern ones in Europe.

But of cause... I cannot force you to help me, me being at that level.
[B]
I'm just very happy as long it lasts![/B]
**I admire your patience!**

Now to the manpages!

By the way:
Here is my Technical University where I was trained some 40 years ago:
[http://en.wikipedia.org/wiki/Lund_University]("http://http://en.wikipedia.org/wiki/Lund_University")

With respect and admiration
Gutta Perka

---

### Post by Gutta Perka on 2011-10-13
Hallo!

Its late - but still working.

I tried in the terminal your sugestions the one where I use Iomega booted to Ubuntu on USB2 and now connected USB stick to USB3. Here we go


[LEFT]> 
bo@david:~$ diff -B module1 module2|grep \>|sed -e "s/^> //"  <----Nothing come out here
bo@david:~$ lsmod                                                                    <----If above command gave nothing Do This and report.
Module                  Size  Used by
lib80211_crypt_ccmp    12789  2 
nls_utf8               12493  1 
isofs                  39549  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_idt      60049  1 
r852                   17901  0 
sm_common              16737  1 r852
snd_hda_intel          24262  2 
nand                   49707  2 r852,sm_common
snd_hda_codec          91754  2 snd_hda_codec_idt,snd_hda_intel
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
snd_hwdep              13276  1 snd_hda_codec
nand_ecc               13070  1 nand
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
mtd                    35852  2 sm_common,nand
snd_seq_midi           13132  0 
binfmt_misc            17292  1 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ipw2200               146148  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  505108  3 
libipw                 46701  1 ipw2200
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
cfg80211              172392  2 ipw2200,libipw
i2c_algo_bit           13199  1 i915
lib80211               14570  3 lib80211_crypt_ccmp,ipw2200,libipw
joydev                 17393  0 
dell_laptop            13519  0 
soundcore              12600  1 snd
dcdbas                 14098  1 dell_laptop
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
psmouse                73673  0 
serio_raw              12990  0 
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
b44                    31443  0 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
usb_storage            44173  4 
uas                    17699  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
ssb                    50682  1 b44
xhci_hcd               72915  0 What does this mean?


[/LEFT]
Usb stick now in USB3 port.
See your former instruktions to me.
That "xhci_hcd               72915  0" bothers me!

With all respect
Gutta Perka

---

### Post by kiyop on 2011-10-13
Thanks for your reporting the results of "lsmod".

I guess necessary modules may be (although I am not sure):
xhci_hcd
sdhci
sdhci_pci
usb_storage
hid
usbhid

But, they are for ubuntu because you got the above result by booting Ubuntu on USB 3.0 HDD (Iomega) connected to USB 2.0 port, did not you?
I do not use Ubuntu usually.
I do not have "usual" Ubuntu 11.04.
I have only Ubuntu modified a little by me.
So I decided to make kiyoshi's help on debian squeeze.
I guess necessary modules in debian are:
xhci
sdhci
sdhci_pci
usbhid
hid
usb_storage
So, I included the above modules and made kiyoshi's help (initramfs) and uploaded necessary files onto MegaUpload.
I suggest you to do the following.

1) Boot with Windows XP installed in your internal HDD.

2) Download the following 3 files.

[http://www.megaupload.com/?d=JHPC9ONW](http://www.megaupload.com/?d=JHPC9ONW)
debian squeeze kernel (vmlinuz-2.6.32-5-686)
SHA1SUM value: 64b470ab90e7587b8ad83889bf7f6b206ceeb3d5

[http://www.megaupload.com/?d=61MO56NU](http://www.megaupload.com/?d=61MO56NU)
kiyoshi's help initramfs file (initrd.img-kiyoCs111014)
SHA1SUM value: aee733ff458d765ddb110224f1f9f8178b0f2712

[http://www.megaupload.com/?d=JVD3J5L7](http://www.megaupload.com/?d=JVD3J5L7)
grub4dos 0.4.4 loader (grldr)
SHA1SUM value: 5b6b771be1b3fff8c12cb824516b717aa389d353

If some pages (advertisements) open, neglect them and just download 3 files. 
I suggest you to check if SHA1SUM values of the downloaded files match the above values.

3) Place the downloaded files on C:\.

4) Edit c:\boot.ini and add the following 1 line at the end.

C:\grldr="Grub4dos 0.4.4"

5) Make a text file named "menu.lst" on c:\ and edit it and add the following 3 lines. without empty lines between them.

title kiyoshi help thanks to debian kernel vmlinuz-2.6.32-5-686 and kexec-tools and dialog

kernel /vmlinuz-2.6.32-5-686

initrd /initrd.img-kiyoCs111014

6) Reboot and select boot menu for Windows XP and press F8 key just after selecting the boot menu for Windows XP.
Select "Grub4dos 0.4.4"
Select "kiyoshi help..."
Wait a moment until you think your USB 3.0 HDD is recognized (usually, 1 minute is enouch, I think), and then press "ENTER key".
Check if your ubuntu partition on USB 3.0 HDD (Iomega) is recognized or not and report me.

Caution!: Even if your ubuntu partition on USB 3.0 HDD (Iomega) is recognized by kiyoshi's help, maybe you cannot boot ubuntu because your initramfs in ubuntu /boot directory does not contain necessary modules. I will tell how to incorporate necessary modules into your ubuntu initramfs later.

---

### Post by Gutta Perka on 2011-10-14
OK! I'm in it.
Just now completing and learning this.
> 
                                                                                                       
                                                                                                                **Re: Trouble booting from USB 3.0 Device**             
                                                                Thanks for your giving me much information on your problem.

There are many possible ways to boot Ubuntu on Iomega via USB 3.0 expresscard.

I write one way without using debian below. If you prefer another way, tell me so.

Connect your Ubuntu USB3.0 media (Iomega?) to USB2.0 port without  connecting anything to USB 3.0 port (nec USB3 expresscard) and boot  Ubuntu form Iomega. Then execute in terminal
     Code:
     lsmod|sort| tee module1 
Then connect USB stick to nec USB3.0 expresscard and execute
     Code:
     lsmod |sort|tee module2 diff -B module1 module2|grep \>|sed -e "s/^> //" 
Confirm xhci or such module name(s) is/are shown.
If nothing shown, please post the result of
     Code:
     lsmod 
If something (modules for USB3.0 port) are shown, go ahead.     Code:
     gksu gedit /etc/modules 
and add the modules shown and save.
     Code:
     gksu gedit /etc/initramfs-tools/modules 
and add the modules shown and save.

Then
     Code:
     sudo update-initramfs -u sudo update-grub 
You should know the UUID of the Ubuntu / partition of your USB3.0HDD (Iomega)
     Code:
     sudo blkid $(mount|grep " / "|cut -d " " -f1) 
The UUID is shown after
UUID=
Neglect double quotation.

Mount the windows xp system partition and copy the current kernel and  its initrams files into the root directory of the windows xp system  partition.
The version of the current kernel is shown by
     Code:
     uname -r 
and the current kernel is like,
/boot/vmlinuz-...
The initramfs is like,
/boot/initrd.img-...

Download
[http://sourceforge.net/projects/grub...oad?_test=goal]("http://sourceforge.net/projects/grub4dos/files/GRUB4DOS/grub4dos%200.4.4/grub4dos-0.4.4.zip/download?_test=goal")
and decompress it by commands like
     Code:
     unzip [path]/grub4dos-0.4.4.zip 
Copy the following files in the decompressed directory.
grldr
grub.exe
menu.lst

Execute:
     Code:
     sudo sync 
And reboot and boot windows xp.

Add the following line to c:\boot.ini[FONT=monospace]
[/FONT]c:\grldr="grub4dos"

Add the following lines to c:\menu.lst
title ubuntu on Iomega
kernel /vmlinuz-... root=UUID=#### ro
initrd /initrd.img-...

The above "..." should be replaced with the version of the current kernel.
The above "####" should be replaced with the UUID of the ubuntu / partition.

Save c:\boot.ini and c:\menu.lst.

Shutdown and connect USB3.0HDD (Iomega) to nec USB3.0 card.

Boot and press F8 or Ctrl key to display the windows boot list menu.
Select
grub4dos

and then with arrow-down key, select
ubuntu on Iomega

God bless you!I just followed your steps - **and learned a lot**

BUT, almost ready and with great hope you aked me to do:

> Add the following line to c:\boot.ini[FONT=monospace]
[/FONT]c:\grldr="grub4dos"I was pusseld:

1/ windows "boot.ini" was not to be found on the old IDE drive.
2/ If that very windows file was to be found I have a feeling that you cannot just
    add "c:\grldr="grub4dos" to it on a new line. The contents of this file
    seems to have a strict linguistic order.

Note to 1/
--> I think the "Ubuntu - Boot Repair" (a cd from ubuntu to get a startup screeen where you select OS:s) I think that Ubuntu setup CD "grubed" the boot setup on windows. Certainly a bad thing to do. When I disconnected the Iomega I could not boot windows. "ntldr" was missing. So I did put in the "ntldr", taken from "the net" with a booted Ubuntu on USB2. Now it works - I can boot XP without the Iomega connected. If I connect the Iomega I get the "select screen" 

Note to 2/
--> I studied the the root of Debian and there was a "autorun.inf". It's liguistic more fits what I can imagine how such a file should look like. 
Did you refer to such a file?

Another way is to throw in "boot.ini" (they are to 99% the same) - but then I must first must study how it strictly is build to scweeze in the meaning of "grldr="gru4dos"" there.

I shall try to make this "autorun.inf" - (grub needs it???) and see what happens. I don't hurt!:p

I'm feeling and have great hope that we are soon there!

I have printed out your new thread/answer. I have printed it out for studies and later use. 

First I want to do and try the obove things and go to the botton with it.

I love it!
It's not a job to be done anylonger - Now it's sport!
It fits me fine!

Again - THANKS for caring. Your patience is admirable!

With respect
Gutta Perka

---

### Post by kiyop on 2011-10-14
I should have asked an important question. I forgot it! #-o
Could you mount (or access) some partition in USB 8GB flash connected to USB 3.0 port, when you booted Ubuntu in Iomega connected to USB 2.0 port?

> **Gutta Perka said:**
> 1/ windows "boot.ini" was not to be found on the old IDE drive.
Is Windows XP installed in the internal HDD? (A kind of joke);)
c:\boot.ini file is a hidden file, which is not seen by default while Windows XP is booting.

I could find the following URL by searching with Google within 10 seconds.
[http://vlaurie.com/computers2/Articles/bootini.htm](http://vlaurie.com/computers2/Articles/bootini.htm)

If you cannot find c:\boot.ini even after changing the configuration of "explorer(?)" in Windows XP so that the hidden system file is shown,
execute "boot info script" and post the contents of RESULTS.txt.
"boot info script" can be downloaded at:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

But I am a little confused because you posted the following:
> **Gutta Perka said:**
> Note to 1/
--> I think the "Ubuntu - Boot Repair" (a cd from ubuntu to get a startup screeen where you select OS:s) I think that Ubuntu setup CD "grubed" the boot setup on windows. Certainly a bad thing to do. When I disconnected the Iomega I could not boot windows. "ntldr" was missing. So I did put in the "ntldr", taken from "the net" with a booted Ubuntu on USB2. Now it works - I can boot XP without the Iomega connected. If I connect the Iomega I get the "select screen" 
So...I guess that you did wrong thing when you installed ubuntu.
Maybe I guess that you installed Grub code into the MBR of the internal HDD when you installed ubuntu into a partition in Iomega. In such case, similar problem happens. The solution is simple, but you solved the problem in a different way by yourself. So I do not write the solution for such case now.

The problem is that you downloaded unreliable ntldr file manually and placed it in c:\.

:confused:huh....

Where did you download "ntldr"? Please show the URL. Sometimes the downloadable file contains computer virus. Especially the system file in Windows....
(That is why I showed you the SHA1SUM value of my uploaded files.)

How to do....

First of all, please let me know the contents of RESULTS.txt given by boot info script.

---

### Post by Gutta Perka on 2011-10-14
First - here are thecomplete  results from boot_info_script:   (Hmmm ends with an error?)

Setup: Booted Ubuntu on USB2, Hirens Boot Usb on USB3 port.
  

>                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub4Dos is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /menu.lst /boot.ini /grub.exe /grldr.mbr /ntldr 
                       /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdb1 
                       and looks at sector 146243927 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sdb2 
                       and looks at sector 146030655 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for  on this drive. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /menu.lst /grldr /grldr

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 huvuden, 63 sektorer/spår, 9729 cylindrar, totalt 156301488 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   156,280,319   156,280,257   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 999.5 GB, 999460397056 bytes
255 huvuden, 63 sektorer/spår, 121510 cylindrar, totalt 1952071088 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   353,076,569   353,076,507  83 Linux
/dev/sdb2         361,478,568 1,952,058,149 1,590,579,582   7 NTFS / exFAT / HPFS
/dev/sdb3         353,076,631   361,478,564     8,401,934   5 Extended
/dev/sdb5         353,076,633   361,478,564     8,401,932  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2000 MB, 2000682496 byte
255 huvuden, 63 sektorer/spår, 243 cylindrar, totalt 3907583 sektorer
Enheter = sektorer av 1 · 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     3,907,582     3,907,520   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        EE0C69080C68CD61                       ntfs       
/dev/sdb1        9d0d61e1-cad3-a90c-7edc-4fc6f3f41ffb   ext3       Ubuntu
/dev/sdb2        562A797F2A795CC5                       ntfs       Iomega_HDD
/dev/sdb5        c86dde49-3ba9-4ba2-8b39-c960c80e5db2   swap       
/dev/sdc1        C4BC-BA75                              vfat       HIRENS141

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sdb2        /media/Iomega_HDD        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/HIRENS141         vfat       (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sr1         /media/Iomega_CD         iso9660    (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)


================================ sda1/menu.lst: ================================

--------------------------------------------------------------------------------
# This is a sample menu.lst file. You should make some changes to it.
# The old install method of booting via the stage-files has been removed.
# Please install GRLDR boot strap code to MBR with the bootlace.com
# utility under DOS/Win9x or Linux.

color blue/green yellow/red white/magenta white/magenta
timeout 30
default /default

title find and load NTLDR of Windows NT/2K/XP
fallback 1
find --set-root --ignore-floppies /ntldr
chainloader /ntldr
savedefault --wait=2

title find and load BOOTMGR of Windows VISTA
fallback 2
find --set-root --ignore-floppies /bootmgr
chainloader /bootmgr
savedefault --wait=2

title find and load CMLDR, the Recovery Console of Windows NT/2K/XP
fallback 3
find --set-root --ignore-floppies /cmldr
chainloader /cmldr
#####################################################################
# write string "cmdcons" to memory 0000:7C03 in 2 steps:
#####################################################################
# step 1. Write 4 chars "cmdc" at 0000:7C03
write 0x7C03 0x63646D63
# step 2. Write 3 chars "ons" and an ending null at 0000:7C07
write 0x7C07 0x00736E6F
savedefault --wait=2

title find and load IO.SYS of Windows 9x/Me
fallback 4
find --set-root /io.sys
chainloader /io.sys
savedefault --wait=2

title find and boot 0PE.ISO
fallback 5
find --set-root /0PE/0PE.ISO
map /0PE/0PE.ISO (0xff) || map --mem /0PE/0PE.ISO (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title find and boot MicroPE.ISO
fallback 6
find --set-root /boot/MicroPE.ISO
map /boot/MicroPE.ISO (0xff) || map --mem /boot/MicroPE.ISO (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title Parted Magic ISO
fallback 7
find --set-root /pmagic.iso
map /pmagic.iso (0xff) || map --mem /pmagic.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title Ultimate Boot CD ISO
fallback 8
find --set-root /ubcd.iso
map /ubcd.iso (0xff) || map --mem /ubcd.iso (0xff)
map --hook
chainloader (0xff)
savedefault --wait=2

title commandline
commandline

title floppy (fd0)
chainloader (fd0)+1
rootnoverify (fd0)

title back to dos
quit

title reboot
reboot

title halt
halt

title MAXDOS.IMG
find --set-root --ignore-floppies /boot/MAXDOS.IMG
map --mem /boot/MAXDOS.IMG (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)


--------------------------------------------------------------------------------

================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
D:\grldr="grub4dos"--------------------------------------------------------------------------------

========================= sda1/grub.exe embedded menu: =========================

--------------------------------------------------------------------------------
pxe detect
configfile
default 0
timeout 1
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             initrd.img-3.0.0-12-generic                    1
            ?? = ??             initrd.img-3.0.0-12-generic.zip               11
            ?? = ??             menu.lst                                       1
            ?? = ??             vmlinuz-3.0.0-12-generic.zip                   0
            ?? = ??             initrd.img-3.0.0-12-generic                    1

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set=root 9d0d61e1-cad3-a90c-7edc-4fc6f3f41ffb
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos1)'
  search --no-floppy --fs-uuid --set=root 9d0d61e1-cad3-a90c-7edc-4fc6f3f41ffb
  set locale_dir=($root)/boot/grub/locale
  set lang=sv_SE
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, med Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 9d0d61e1-cad3-a90c-7edc-4fc6f3f41ffb
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=9d0d61e1-cad3-a90c-7edc-4fc6f3f41ffb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, med Linux 3.0.0-12-generic (återställningsläge)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 9d0d61e1-cad3-a90c-7edc-4fc6f3f41ffb
    echo    'Läser in Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=9d0d61e1-cad3-a90c-7edc-4fc6f3f41ffb ro recovery nomodeset 
    echo    'Läser in initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, med Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 9d0d61e1-cad3-a90c-7edc-4fc6f3f41ffb
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9d0d61e1-cad3-a90c-7edc-4fc6f3f41ffb ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, med Linux 2.6.38-8-generic (återställningsläge)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 9d0d61e1-cad3-a90c-7edc-4fc6f3f41ffb
    echo    'Läser in Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=9d0d61e1-cad3-a90c-7edc-4fc6f3f41ffb ro recovery nomodeset 
    echo    'Läser in initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 9d0d61e1-cad3-a90c-7edc-4fc6f3f41ffb
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 9d0d61e1-cad3-a90c-7edc-4fc6f3f41ffb
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sdb1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=9d0d61e1-cad3-a90c-7edc-4fc6f3f41ffb /               ext3    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-8-generic               7
               =                boot/initrd.img-3.0.0-12-generic               8
               =                boot/vmlinuz-2.6.38-8-generic                  3
               =                boot/vmlinuz-3.0.0-12-generic                  3
               =                initrd.img                                     8
               =                initrd.img.old                                 7
               =                vmlinuz                                        3
               =                vmlinuz.old                                    3

================================ sdc1/menu.lst: ================================

--------------------------------------------------------------------------------
timeout 0 
default 0 
title Hiren's BootCD 
find --set-root /HBCD/menu.lst 
configfile /HBCD/menu.lst 
--------------------------------------------------------------------------------

========================== sdc1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
pxe detect
configfile
default 0
timeout 1
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             menu.lst                                       1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb3

00000000  fe f7 fc 07 d0 1b bd 87  3a 11 11 6f de cc 4e d6  |........:..o..N.|
00000010  9a f8 bd 71 be a3 b5 48  53 df 9d 48 aa be 84 48  |...q...HS..H...H|
00000020  35 91 98 0a 86 a9 10 b5  bc d3 8b 34 34 4c ba e9  |5..........44L..|
00000030  97 6b 91 87 87 65 38 4d  dc 17 dd a6 48 44 5f b4  |.k...e8M....HD_.|
00000040  4b 88 5a bf c0 ef ec bc  37 b1 a9 f6 17 13 63 f9  |K.Z.....7.....c.|
00000050  f0 77 35 44 8c 6c 24 60  c8 7e 34 32 5f 26 b2 37  |.w5D.l$`.~42_&.7|
00000060  05 06 66 67 c1 1f 9e 4e  b2 2e 82 20 11 16 96 32  |..fg...N... ...2|
00000070  7d 4a 87 c4 b9 04 16 6c  a9 7c 36 b8 62 67 36 95  |}J.....l.|6.bg6.|
00000080  a5 32 8c bf bd 65 dd ef  c1 27 7c cf f0 27 95 53  |.2...e...'|..'.S|
00000090  f6 85 fd d3 ff e7 86 f7  5f 0c 9c b6 3e 8c 3e ed  |........_...>.>.|
000000a0  db eb 07 c4 bb 13 56 4e  db 2b bc 4f e2 dd 8c c3  |......VN.+.O....|
000000b0  92 f6 9c 27 57 63 bc b3  55 49 1c 23 98 ac 7a 06  |...'Wc..UI.#..z.|
000000c0  b2 eb aa ad eb 2f c7 d2  0b cf e3 94 0b 1e fa 9a  |...../..........|
000000d0  71 f6 04 b9 dc ca f6 86  37 80 98 cf 66 6b 52 45  |q.......7...fkRE|
000000e0  4a 56 91 46 7c cb b9 dc  6b 69 8e e2 77 5e e4 e5  |JV.F|...ki..w^..|
000000f0  dc 69 e9 bc be ba e4 4b  7b d8 a6 c9 31 88 88 93  |.i.....K{...1...|
00000100  fb 76 db 94 62 86 91 b2  65 03 4d 4a 59 bf d3 c4  |.v..b...e.MJY...|
00000110  dc 96 65 32 11 ad b0 03  5a 59 67 86 ee cb 73 0c  |..e2....ZYg...s.|
00000120  a7 09 4f 05 33 e2 be 13  81 60 55 66 a2 19 45 33  |..O.3....`Uf..E3|
00000130  57 12 57 32 b8 33 99 1f  25 9d a6 94 6b 73 9b 65  |W.W2.3..%...ks.e|
00000140  38 4d ee 27 6e 53 a5 b9  e6 af 4d ca 59 bf e7 c8  |8M.'nS....M.Y...|
00000150  db 16 4c 9c 71 1e ce 59  4f ac 37 3d 38 4d 95 57  |..L.q..YO.7=8M.W|
00000160  93 cf a6 cf 59 20 46 c5  6e 76 74 56 67 25 cf 89  |....Y F.nvtVg%..|
00000170  7c 04 7d f0 df a4 e8 79  c2 16 34 61 bb e9 7d e0  ||.}....y..4a..}.|
00000180  d6 0a e6 e7 cf 48 a2 8b  4e 5b 6c 89 29 fa a3 df  |.....H..N[l.)...|
00000190  41 27 ce be 01 fa 82 74  21 96 3a 39 72 19 22 b4  |A'.....t!.:9r.".|
000001a0  04 d1 f4 91 68 44 72 b7  29 dd de 32 c0 ff be fd  |....hDr.)..2....|
000001b0  e5 9b a7 7f 19 f6 7e fa  8c 0c 48 5b c6 c0 00 01  |......~...H[....|
000001c0  c1 ff 82 fe ff ff 02 00  00 00 0c 34 80 00 00 00  |...........4....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
unlzma: Decoder error
]

> Re: Trouble booting from USB 3.0 Device 
I should have asked an important question. I forgot it! 
Could you mount (or access) some partition in USB 8GB flash connected to USB 3.0 port, when you booted Ubuntu in Iomega connected to USB 2.0 port?No problem there! I had a good view of Debian - from above!:D

I will continue this evening - now I have customurs wondering what I'm doing.....

Hey - I'm an outdoor man. Often going to the moutans climbing. I like that! I can now see the top - in distans. That is, the mist/clouds are diminishing . Soon there?

---

### Post by kiyop on 2011-10-14
Thanks for your reporting the contents of RESULTS.txt.

It is very nice to confirm you can recognize USB flash connected on USB  3.0 port while Ubuntu installed in /dev/sdb1 (Iomega) is booting.

Boot with Ubuntu on Iomega connected to USB 2.0  port and execute the following.

1) Confirm /etc/modules and /etc/initramfs-tools/modules contains the following lines by 
```
more /etc/modules
more /etc/initramfs-tools/modules
```xhci_hcd
sdhci
sdhci_pci
usb_storage
hid
usbhid

If not, as you know, add the above lines by
```
gksu gedit /etc/modules
gksu gedit /etc/initramfs-tools/modules
```2) execute
```
sudo update-initramfs -u
```3) Backup the MBR of the internal HDD:
First, confirm the internal HDD is recognized as /dev/sda by
```
sudo fdisk -l|grep 80.0
```If the internal HDD (80.0GB) is /dev/sda, go ahead.
If not, do not go ahead and let me know.
```
sudo dd if=/dev/sda bs=512 count=63 > sdambr63_111015
sudo mount -t ntfs-3g /dev/sda1 /mnt
sudo cp sdambr63_111015 /mnt/
sudo sync
```**2011/10/16 15:40 at JAPAN**
I have removed "-o rw" after "sudo mount -t ntfs-3g /dev/sda1 /mnt".

4) Install grub4dos boot code into the MBR of the internal HDD
```
wget -c http://downloads.sourceforge.net/project/grub4dos/GRUB4DOS/grub4dos%200.4.4/grub4dos-0.4.4.zip
unzip grub4dos-0.4.4.zip
cd grub4dos-0.4.4
sudo ./bootlace.com /dev/sda
```5) copy the current kernel and initramfs into /dev/sda1.
```
sudo cp /boot/vmlinuz-3.0.0-12-generic /boot/initrd.img-3.0.0-12-generic /mnt/
```**EDIT at 2011/10/16 15:40 at JAPAN**
I have removed "-a".

6) copy grub4dos loader into /dev/sda1.
```
sudo cp grldr /mnt/
```**EDIT at 2011/10/16 15:40 at JAPAN**
I have removed "-a".

7) Shutdown (finish using Ubuntu on Iomega) and remove any CD/DVD  (for example, Iomega_CD)
Remove Iomega USB HDD and USB flash.
Power on.

8 ) In grub4dos-0.4.4 menu, select " find and load NTLDR of Windows NT/2K/XP"

9) If Windows XP booted, add the following lines at the end of c:\menu.lst.

title ubuntu on Iomega 1st partition
kernel /vmlinuz-3.0.0-12-generic root=UUID=9d0d61e1-cad3-a90c-7edc-4fc6f3f41ffb ro vt.handoff=7
initrd /initrd.img-3.0.0-12-generic 

Save c:\menu.lst.

10) Restart Windows XP and wait until Grub4dos-0.4.4 screen with many menus shown.

11) Use arrow down key to select ubuntu on Iomega 1st partition (Do not push Enter key yet).

12) Connect Iomega USB HDD on USB **3.0** port and push ENTER key.

Good luck!

---

### Post by Gutta Perka on 2011-10-14
Hallo! time here 04.38 AM - woked up and went to see what's going on!

Thanks for your care!

Just a short note....

I was kicked out doing this command

> sudo mount -t ntfs-3g /dev/sda1 /mnt -o rw

I also tried a space between "ntfs and "-3g"
Manpages sais example: ....../mnt/*windows* -o...... or something like that. - perhaps the device or hda....

I dont dare to do that - something might explode in front of me:P

OK! I'll try to take a nap waiting for your suggestions!

Till then

Best Regards
Gutta

---

### Post by kiyop on 2011-10-15
> **Gutta Perka said:**
> I was kicked out doing this command
> 
                                                 sudo mount -t ntfs-3g /dev/sda1 /mnt -o rw                      > **Gutta Perka said:**
> sdb1: __________________________________________________  ________________________

    File system:       ext3
    
...

Operating System:  Ubuntu 11.10
Ooops! #-o I did not noticed well that your recent 11.10 ubuntu may have difference in mount command (options) from the older versions.

My knowledge on Ubuntu is based mainly on 10.10 and a little on 11.04.
I am too used to the Great world of Debian now. Anyway...

I found 
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
and
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
It says by default, ntfs-3g packages are available and you can mount NTFS partition in read/write mode by
```
sudo mount -t ntfs-3g /dev/DEVICE_FILE_NAME /MOUNT_POINT
```Maybe, we should remove the option "-o rw". Please remove "-o rw".

**Edit at 2011/10/15 19:48 in JAPAN**
I believe that you can write to a NTFS partition with Ubuntu 11.10.
I am not familiar with Ubuntu 11.10.

I suggest you to copy the generated sdambr63_111015 into another partition from Ubuntu / partition, which is not necessary.

Copying /boot/vmlinuz-3.0.0-12-generic and /boot/initrd.img-3.0.0-12-generic and grldr into a partition where BIOS can access is necessary.
Just mount the NTFS partition and copy the above 3 files into the NTFS partition.
To be simple, you need not even edit c:\menu.lst nor c:\boot.ini.

If only you installed grub4dos code into MBR of the intenal HDD, you can load c:\vmlinuz-3.0.0-12-generic and c:\initrd.img-3.0.0-12-generic manually at grub4dos command line.

You can install grub4dos code into MBR of the internal HDD by
4) in
[http://ubuntuforums.org/showthread.php?p=11345126#post11345126](http://ubuntuforums.org/showthread.php?p=11345126#post11345126)
That is, 
```
wget -c http://downloads.sourceforge.net/project/grub4dos/GRUB4DOS/grub4dos%200.4.4/grub4dos-0.4.4.zip[FONT=monospace]
[/FONT]unzip grub4dos-0.4.4.zip[FONT=monospace]
[/FONT]cd grub4dos-0.4.4[FONT=monospace]
[/FONT]sudo ./bootlace.com /dev/sda
```After disconnecting Iomega and USB 2GB flash, power on and at Grub4dos screen, press "c" key.
You will enter in Grub4dos command line.

Type the following 3 lines and hit "enter" key at the end of each line:

root (hd0,0)

kernel /vmlinuz-3.0.0-12-generic root=UUID=9d0d61e1-cad3-a90c-7edc-4fc6f3f41ffb ro vt.handoff=7

initrd /initrd.img-3.0.0-12-generic

And then, connect the Iomega to USB 3.0 port and type 

boot

and hit "Enter" key.

That is enough.

---

### Post by Gutta Perka on 2011-10-15
puh, kicked out again!

sudo cp -a /boot/vmlinuz-3.0.0-12-generic /boot/initrd.img-3.0.0-12-generic /mnt/
-->cp: kan inte skriva över katalog "/mnt/vmlinuz-3.0.0-12-generic" med icke-katalog


I'll try to translate that.

First - that should be swedish? Puh!
Translated by a Kenyan ubuntu fan?

I'll try to tell what he wants:
"cp: can't write over catalog  "/mnt/vmlinuz-3.0.0-12-generic" with a none- catalog"

Regarding your remarks ealier. 
I'll still open for what Linux to use. I only chosed Ubuntu because I thought that it had a large community.
That is, for instance there are interesting forums like this. Feel free to advice me in that matter  as well.

With respect and admiration

Gutta

---

### Post by kiyop on 2011-10-15
[B]EDIT at 2011/10/16 15:20 in JAPAN
My code "cp -a" is bad. There may be no problem on Gutta Perka's Ubuntu 11.10.[/B] 

> **Gutta Perka said:**
> puh, kicked out again!

sudo cp -a /boot/vmlinuz-3.0.0-12-generic /boot/initrd.img-3.0.0-12-generic /mnt/
-->cp: kan inte skriva över katalog "/mnt/vmlinuz-3.0.0-12-generic" med icke-katalog


I'll try to translate that.

First - that should be swedish? Puh!
Translated by a Kenyan ubuntu fan?

I'll try to tell what he wants:
"cp: can't write over catalog  "/mnt/vmlinuz-3.0.0-12-generic" with a none- catalog"
Something wrong happens.
I wonder if your Ubuntu 11.10 has problem.

Please post the result of 
```
file /boot/vmlinuz-3.0.0-12-generic
mount
ls -l /mnt/vm*
```> **Gutta Perka said:**
> Regarding your remarks ealier. 
I'll still open for what Linux to use. I only chosed Ubuntu because I thought that it had a large community.
That is, for instance there are interesting forums like this. Feel free to advice me in that matter  as well.
I remember ... The other guy said that Ubuntu is not stable because of its short term upgrade and that debian stable is so stable that its user is bored of using it and that debian sid (unstable) is interesting because of trouble.
I definitely confirmed that my decision to move to debian was right decision.
But, I think a person who hates learning by himself (herself) should not use Debian.
Of course, there is debian forum: [http://forums.debian.net/index.php ]("http://forums.debian.net/index.php"), but it is not a paradise for newbie.

**EDIT at 2011/10/15 23:53 at JAPAN:**
A possible work around is using FAT32 (vfat) partition on your USB flash.
Mount the FAT32 partition on the USB flash and copy the 3 files (vmlinuz-3.0.0-12-generic, initrd.img-3.0.0-12-generic, grldr) into it.

Then boot with XP and copy the files in USB flash to c:\.

---

### Post by Gutta Perka on 2011-10-15
I have decided to remove this, my own post.

It was not strictly Ubunto!

Regards

/Gutta

---

### Post by kiyop on 2011-10-15
[B]EDIT at 2011/10/16 15:55 in JAPAN:
My command "cp -a" is bad. There might have been no problem in Gutta Perka's Ubuntu 11.10.[/B]

> **Gutta Perka said:**
> 
1/ ubuntu will be bined.
Excuse me, but I do not know the meaning of "bined".

> **Gutta Perka said:**
> 
2/Debian will be installed in it's place
**Do not do that.**
You need not remove Ubuntu on Iomega.
You can use debian on USB 2.0GB flash, cannot you? But I think 2GB is too small for full install of GNOME.

> **Gutta Perka said:**
> 
 3/ As soon as Debian is installed I'll go through all the above
    instruktions myself again.
4/ As soon as I'm ready with that we will continue this thread as a clean Debian thread again here for
    those  who still might be interested in this thread (hallo out there - I will convert to Debian - no protests!)
I think that we should post about debian without mentioning Ubuntu in [other OS/ Distro talk]("http://ubuntuforums.org/forumdisplay.php?f=401") or [debian forum]("http://forums.debian.net/viewforum.php?f=30") because this is ubuntu forum.

> **Gutta Perka said:**
> Sir - I'll continue to read this thread and work with it however now in Debian.
I wrote comment to be executed on Ubuntu unless I clearly mentioned that you should execute in debian.
For example, "sudo" is written for Ubuntu.

> **Gutta Perka said:**
>  Because of this, feel free to take one to three days vacation. I suppose you need it.
I do not need such vacation. But, thanks for consideration for me:)

> **Gutta Perka said:**
> Just a question - What Debian do you recomend? 
Definitely "Stable" ("Squeeze", 6.0.3) especially for newbie.

> **Gutta Perka said:**
> (Are there special Debian versions).
Please read
[http://www.debian.org/releases/](http://www.debian.org/releases/)

For different architecture and different installer cd image,
[http://www.debian.org/releases/squeeze/debian-installer/](http://www.debian.org/releases/squeeze/debian-installer/)
Debian supports many architectures that Ubuntu does not supports.
I think "i386" for 32 bit and "amd64" for 64 bit are good one for you.

If the machine to be installed can access to internet via DHCP and if you know well how to install debian, I suggest to download the following 2 files (for i386)
[http://ftp.jaist.ac.jp/pub/Linux/Debian/dists/squeeze/main/installer-i386/current/images/netboot/debian-installer/i386/initrd.gz](http://ftp.jaist.ac.jp/pub/Linux/Debian/dists/squeeze/main/installer-i386/current/images/netboot/debian-installer/i386/initrd.gz)
[http://ftp.jaist.ac.jp/pub/Linux/Debian/dists/squeeze/main/installer-i386/current/images/netboot/debian-installer/i386/linux](http://ftp.jaist.ac.jp/pub/Linux/Debian/dists/squeeze/main/installer-i386/current/images/netboot/debian-installer/i386/linux)
and place at / directory of Ubuntu / partition and then execute the following
```
sudo gedit /etc/grub.d/40_custom
```and add the following lines at the end.
```
menuentry "debian installer" {
linux /linux
initrd /initrd.gz
}
```and save the file and execute
```
sudo update-grub
```and restart and press Shift key and select "debian installer" if you see "grub 1.9..." menu.
debian installer will start. I hope.

> **Gutta Perka said:**
> I'll try to keep up starting with #32 of this thread.
[#32]("http://ubuntuforums.org/showthread.php?p=11332900#post11332900") is for Ubuntu.

> **Gutta Perka said:**
> In real - this is just a minor stop and in real I didn't like Ubunto changing to version 11.10.
I have just dribbeld around with ubunto for some weeks and the ground did change for me.
You can prevent upgrade to 11.10, although I heard that Ubuntu (since 10.10->11.04) urges you to upgrade automatically. I am not sure if Ubuntu 11.04 also urges to upgrade to 11.10.

> **Gutta Perka said:**
> The worst thing that can happen now after this is that Debian is coming out with a major revision in a month or so.
Debian stable continues rather long, longer than Ubuntu releases.
Please refer
[http://en.wikipedia.org/wiki/Debian#Release_history](http://en.wikipedia.org/wiki/Debian#Release_history)

> **Gutta Perka said:**
> I'll do what you wanted me to do in the last post - but in Debian!
Do not do that.
[#50]("http://ubuntuforums.org/showthread.php?p=11347232#post11347232") is for Ubuntu.

I suggest you to follow
> **kiyop said:**
> 
**EDIT at 2011/10/15 23:53 at JAPAN:**
A possible work around is using FAT32 (vfat) partition on your USB flash.
Mount the FAT32 partition on the USB flash and copy the 3 files (vmlinuz-3.0.0-12-generic, initrd.img-3.0.0-12-generic, grldr) into it.

Then boot with XP and copy the files in USB flash to c:\.

---

### Post by kiyop on 2011-10-15
Maybe the problem with cp command is due to "-a" option.
If so, excuse me. [-o<

That is, for [#46]("http://ubuntuforums.org/showthread.php?p=11345126#post11345126") 5)
> **kiyop said:**
> 5) copy the current kernel and initramfs into /dev/sda1.
```
sudo cp -a /boot/vmlinuz-3.0.0-12-generic /boot/initrd.img-3.0.0-12-generic /mnt/
```
execute the following instead of the above.
```
sudo cp /boot/vmlinuz-3.0.0-12-generic /boot/initrd.img-3.0.0-12-generic /mnt/
```And for [#46]("http://ubuntuforums.org/showthread.php?p=11345126#post11345126") 6)
> **kiyop said:**
> 
6) copy grub4dos loader into /dev/sda1.
```
sudo cp -a grldr /mnt/
```
execute the following instead of the above.
```
cd grub4dos-0.4.4
sudo cp grldr /mnt/
```And then go ahead from [#46]("http://ubuntuforums.org/showthread.php?p=11345126#post11345126") 7)
> **kiyop said:**
> 7) Shutdown (finish using Ubuntu on Iomega) and remove any CD/DVD  (for example, Iomega_CD)
 Remove Iomega USB HDD and USB flash.
 Power on.

**EDIT at 2011/10/16 11:10 in JAPAN**
Of course, you should execute before 5) and 6),
```
sudo mount -t ntfs-3g /dev/sda1 /mnt
```

---

### Post by Gutta Perka on 2011-10-15
> I think that we should post about debian without mentioning Ubuntu in [other OS/ Distro talk]("http://ubuntuforums.org/forumdisplay.php?f=401") or [debian forum]("http://forums.debian.net/viewforum.php?f=30") because this is ubuntu forum.Results and suggestion because of that.
I cleaned up my post #51 and suggest that we both,  principally , continue where we was before that one - that is after post #50. I think I did wrong there forgetting that this is a Ubuntu forum only.  I suggest that you edit your following postings to mine from "you know what I mean" and keep the relevant Ubuntu talk in them.

I think and want to continue there - I think we are close to the end result - positive or negative.

"That other thing" - I'll deal with that another time and on another place.
Sad to say, in that eager, I destroyed my Ubuntu dealing with it. But here I'm back in Ubuntu again. Ver 11.04. (keeping that version!)

OK!

> Excuse me, but I do not know the meaning of "bined"I might use English wrong here!
In windows the "bin" is the  - wastepaper basket, litter bin,  waste paper basket, wastebasket, rubbish bin, litter-basket or something like that. So "bined" for my very own English "something that I wasted into the bin" - you know bending words...

I look forward to continue this thread. Tomorrow, Sunday and part of Monday, my wife and I are going to take the car for a rather long trip to two of our five children
.
That is, sad to say, neither Linuxing nor computing.
It's not often nowadays you see your children - so I look forward to that.

Anyhow, in the meanwhile, I'll give You and this thread some thoughts - eager to come back here.

 Until then and with great respect

/Gutta

---

### Post by kiyop on 2011-10-16
> **Gutta Perka said:**
> I cleaned up my post #51 and suggest that we both,  principally , continue where we was before that one - that is after post #50.

...

I suggest that you edit your following postings to mine from "you know what I mean" and keep the relevant Ubuntu talk in them.

...

Sad to say, in that eager, I destroyed my Ubuntu dealing with it. But here I'm back in Ubuntu again. Ver 11.04. (keeping that version!)
I see. Excuse my mistake.

> **Gutta Perka said:**
> So "bined" for my very own English "something that I wasted into the bin" 
I see. "binned". I guessed the misspelling of "bind" or so.

Let's proceed unhurriedly.
Please boot with Ubuntu in Iomega connected to USB 2.0 port and connect USB flash to USB 3.0 port and execute first, 
```
lsmod
```and post the result.
Execute "boot info script" again and post the contents of RESULTS.txt, because you reinstalled Ubuntu 11.04 and the version of kernel is different from that before (partly because of my bad command,  I am sorry).

---

### Post by MiniT on 2011-10-16
Hello all.
Glad to see that others are working on this issue.
See my fumbling on Linux Mint Forums:
[http://forums.linuxmint.com/viewtopic.php?f=49&t=83476](http://forums.linuxmint.com/viewtopic.php?f=49&t=83476)

I have found that there is a fix in initramfs-tools which did not call up the right module at the right time to boot from USB 3.0.
See here for the bug report and which iniramfs-tools is fixed:
[Bug #565047 in casper (Ubuntu): “Unable to install off USB 3.0 port (HP Envy 15 Laptop)”]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/565047") 
It applies to more than that hardware.  It is the initramfs-tools.

Also, near the bottom of that bug report board, there is reference Grub, with which you all are wresting.  Apparently GRUB2 which is used by Ubuntu Maverick and I think Natty does not boot from USB 3.0.

Two other links that might be useful:
[Debian User Forums • View topic - A possible solution to get USB 3.0 devices to work]("http://forums.debian.net/viewtopic.php?f=7&t=61600") 
[Boot problem on nec bootable usb 3 port]("http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/458792-boot-problem-nec-bootable-usb-3-port.html") 

I can confirm that it is not a Bios/Cmos problem only.  
Also have problem of boot from USB2.0, but same disk not on 3.0.
Tried with updated initramfs-tools, and when kicked out to initramfs prompt, checked loaded modules and saw the xhci-hcd or whatever it is called.
Problem still with Grub2 not finding the disk.

I am no programmer.
Spent all day yesterday messing and researching.
Succeeded in destroying all my stored movies and music on the USB3.0-HDD.  DOH!

I am going to try the Mint 10 64bit again.  It is based on Maverick, and Maverick-proposed has the updated initramfs-tools.  Then I will research how to replace teh Grub2 with another loader which works with USB3.0.  Hopefully in an easier way than hacking all the kernel and using Windows, etc. as I seem to see above.

Will report back, any help appreciated,** you all rock**. Keep going.

mini

---

### Post by kiyop on 2011-10-16
> **MiniT said:**
> I have found that there is a fix in initramfs-tools which did not call up the right module at the right time to boot from USB 3.0.
See here for the bug report and which iniramfs-tools is fixed:
[Bug #565047 in casper (Ubuntu): &#8220;Unable to install off USB 3.0 port (HP Envy 15 Laptop)&#8221;]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/565047") 
It applies to more than that hardware.  It is the initramfs-tools.

Also, near the bottom of that bug report board, there is reference Grub, with which you all are wresting.  Apparently GRUB2 which is used by Ubuntu Maverick and I think Natty does not boot from USB 3.0. .....
Thanks for your nice report.
It may depend on the hardware.
I could boot Ubuntu 10.10 and can boot 11.04 from USB 3.0 HDD connected to USB 3.0 port with [my tool](http://kiyoandkei.blog68.fc2.com/blog-entry-52.html) utilizing kexec.

---

### Post by Gutta Perka on 2011-10-17
[SIZE=4]**Restart!**[/SIZE]                   ----> [COLOR=Black]**Rev 2. Thanks to **[/COLOR] [kiyop]("http://ubuntuforums.org/member.php?u=1246530"),  <----


Too many posts? Hard to follow our struggle?

This discussion started with this in post #31.

I'll start with a copy here.

Then I hope that I, Gutta,  and [kiyop]("http://ubuntuforums.org/member.php?u=1246530") can change in this copy to keep it actual.

Can you mail me on this, [kiyop]("http://ubuntuforums.org/member.php?u=1246530")?? (I think you can reach me on this forum by using my e-mail given by me when I joined the the Ubuntu forum or there is a internal "mail" system. 

Hopyfully it will end with a succesfull booting from NEC usb3 port.

Here we go:

>                                   **Re: Trouble booting from USB 3.0 Device**             
                                                                Thanks for your giving me much information on your problem.

There are many possible ways to boot Ubuntu on Iomega via USB 3.0 expresscard.

I write one way without using debian below. If you prefer another way, tell me so.

Connect your Ubuntu USB3.0 media (Iomega?) to USB2.0 port without  connecting anything to USB 3.0 port (nec USB3 expresscard) and boot  Ubuntu form Iomega. Then execute in terminal
     
Code:
lsmod|sort| tee module1 

Then connect USB stick to nec USB3.0 expresscard and execute
     
Code:
     lsmod |sort|tee module2

diff -B module1 module2|grep \>|sed -e "s/^> //"  #<<<<----Rev 2


Confirm xhci or such module name(s) is/are shown.
If nothing shown, please post the result of
     Code:

     lsmod 

If something (modules for USB3.0 port) are shown, go ahead.     Code:

     gksu gedit /etc/modules 

and add the modules shown and save.
     
Code:
     
gksu gedit /etc/initramfs-tools/modules 

and add the modules shown and save.

Then
     
Code:
     sudo update-initramfs -u           #<<<<----Rev 1
sudo update-grub                     #<<<<----Rev 1

You should know the UUID of the Ubuntu / partition of your USB3.0HDD (Iomega)
     Code:

     sudo blkid $(mount|grep " / "|cut -d " " -f1) 

The UUID is shown after
UUID=
Neglect double quotation.

Mount the windows xp system partition and copy the current kernel and  its _initramfs_    (REV 1 ) files into the root directory of the windows xp system  partition.
The version of the current kernel is shown by

     Code:
     uname -r 
and the current kernel is like,
/boot/vmlinuz-...
The initramfs is like,
/boot/initrd.img-...

Download
[http://sourceforge.net/projects/grub...oad?_test=goal]("http://sourceforge.net/projects/grub4dos/files/GRUB4DOS/grub4dos%200.4.4/grub4dos-0.4.4.zip/download?_test=goal")
and decompress it by commands like
     Code:
     unzip [path]/grub4dos-0.4.4.zip 
Do not forget to change the above "[path]" to the real directory where "grub4dos-0.4.4.zip" exists.  <<<<----Rev 1



Copy the following files in the decompressed directory.
grldr
grub.exe
menu.lst

Execute:
     Code:
     sudo sync 
And reboot and boot windows xp.

Add the following line to c:\boot.ini[FONT=monospace]
[/FONT]c:\grldr="grub4dos"

Add the following lines to c:\menu.lst
title ubuntu on Iomega
kernel /vmlinuz-... root=UUID=#### ro
initrd /initrd.img-...

The above "..." should be replaced with the version of the current kernel.
The above "####" should be replaced with the UUID of the ubuntu / partition.

Save c:\boot.ini and c:\menu.lst.

Shutdown and connect USB3.0HDD (Iomega) to nec USB3.0 card.

Boot and press F8 or Ctrl key to display the windows boot list menu.
Select
grub4dos

and then with arrow-down key, select
ubuntu on Iomega

God bless you!
Testrig: Dell 2006 Inspiron laptop, new USB3 Iomega hard drive, ubuntu 11.04, an expresscard with Nec USB3 port - not bootable. I memory stic 8 Gig with LiveDebian - bootable. And  obvious a Windows XP on the 80 gig old built in IDE drive.

Goal, to be able to boot the Iomega HD drive from the the USB3 port in order to enjoy Ubuntu att full speed. 

Also feel free to start with some downloads.

> 
[http://www.megaupload.com/?d=JHPC9ONW](http://www.megaupload.com/?d=JHPC9ONW)
debian squeeze kernel (vmlinuz-2.6.32-5-686)
SHA1SUM value: 64b470ab90e7587b8ad83889bf7f6b206ceeb3d5

[http://www.megaupload.com/?d=61MO56NU](http://www.megaupload.com/?d=61MO56NU)
kiyoshi's help initramfs file (initrd.img-kiyoCs111014)
SHA1SUM value: aee733ff458d765ddb110224f1f9f8178b0f2712

[http://www.megaupload.com/?d=JVD3J5L7](http://www.megaupload.com/?d=JVD3J5L7)
grub4dos 0.4.4 loader (grldr)
SHA1SUM value: 5b6b771be1b3fff8c12cb824516b717aa389d353They might be handy!

I'm going myself to start again and follow the command given in the copy above.

In this way I hope that we together can reach our goal, without dribbeling around all the 50 posts.

OK - let's go!

Last but not least - that is if the Guro here,  [kiyop]("http://ubuntuforums.org/member.php?u=1246530"), agrees to this?

Others are of cause invited:) ...or just :popcorn:

/Gutta

---

### Post by kiyop on 2011-10-18
> **Gutta Perka said:**
> Hard to follow our struggle?
I do not struggle. I just try to help you.;)

> **Gutta Perka said:**
> Can you mail me on this, [kiyop]("http://ubuntuforums.org/member.php?u=1246530")??
I think I can, but why should I mail you?
Posting here is enough, I think.

> **Gutta Perka said:**
> Goal, to be able to boot the Iomega HD drive from the the USB3 port in order to enjoy Ubuntu att full speed. 
I am not sure if you can enjoy Ubuntu at full speed even after you boot Ubuntu on Iomega connected to USB 3.0 port successfully.

> **Gutta Perka said:**
> Last but not least - that is if the Guro here,  [kiyop]("http://ubuntuforums.org/member.php?u=1246530"), agrees to this?
huh??

First, please give me the result of 
```
lsmod
```or judge which module is necessary by yourself and Go ahead.:)

**EDIT at 2011/10/18 20:40 in JAPAN:**
> **Gutta Perka said:**
> lsmod |sort|tee module2 diff -B module1 module2|grep \>|sed -e "s/^> //" 
The above line should be separated to two lines, thus
```
lsmod |sort|tee module2
diff -B module1 module2|grep \>|sed -e "s/^> //"
```> **Gutta Perka said:**
> sudo update-initramfs -u sudo update-grub
The above line should be separated to two lines, thus
```
sudo update-initramfs -u 
sudo update-grub
```> **Gutta Perka said:**
> Mount the windows xp system partition and copy the current kernel and its initrams files into the root directory of the windows xp system partition.
It is due to [my misspelling]("http://ubuntuforums.org/showpost.php?p=11332900&postcount=32").
"initrams" -> "initramfs"
> **Gutta Perka said:**
> Code:
     unzip [path]/grub4dos-0.4.4.zip
Do not forget to change the above "[path]" to the real directory where "grub4dos-0.4.4.zip" exists.

Good luck! :)

---

### Post by Gutta Perka on 2011-10-18
First you asked for "lsmod" before I do anything.

> bo@bosses:~$ lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  2 
aes_generic            38023  1 aes_i586
lib80211_crypt_ccmp    12785  2 
nls_utf8               12493  1 
isofs                  39571  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
i915                  450944  3 
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
binfmt_misc            13213  1 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ipw2200               145664  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 i915
joydev                 17322  0 
libipw                 46641  1 ipw2200
cfg80211              156212  2 ipw2200,libipw
r852                   17878  0 
sm_common              16737  1 r852
snd_timer              28659  2 snd_pcm,snd_seq
nand                   49822  2 r852,sm_common
drm                   180037  4 i915,drm_kms_helper
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop            13515  0 
nand_ids                8547  1 nand
dcdbas                 14054  1 dell_laptop
nand_ecc               13070  1 nand
snd                     55295  13  snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
mtd                    26720  2 sm_common,nand
lib80211               14570  3 lib80211_crypt_ccmp,ipw2200,libipw
xhci_hcd               68062  0 
serio_raw              12990  0 
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
b44                    35301  0 
hid                    77084  1 usbhid
usb_storage            43946  4 
firewire_ohci          31504  0 
ssb                    45942  1 b44
sdhci_pci              13623  0 
uas                    17676  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci                  22720  1 sdhci_pci
bo@bosses:~$ 

> 
bo@bosses:~$ diff -B module1
diff: saknad operand efter "module1"   (missed operand after "module1")
diff: Försök med "diff --help" för mer information. (diff: try diff --help for more information)>Here ---->I connect USB stick to nec USB3.0 expresscard and execute

> 




bo@bosses:~$ module2|grep\>|sed -e "s/^>//"
Kommandot "grep>" hittades inte. Menade du: (Command "grep>" not found Did you mean...
 Kommandot "grep" från paketet "grep" (main) (...command "grep" from package "grep" (main") )
grep>: kommandot hittades inte (grep>: ( command not found (grep>:)
module2: kommandot hittades inte  (module2: command not found.

bo@bosses:~$ lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  2 
aes_generic            38023  1 aes_i586
lib80211_crypt_ccmp    12785  2 
nls_utf8               12493  1 
isofs                  39571  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
i915                  450944  3 
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
binfmt_misc            13213  1 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ipw2200               145664  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 i915
joydev                 17322  0 
libipw                 46641  1 ipw2200
cfg80211              156212  2 ipw2200,libipw
r852                   17878  0 
sm_common              16737  1 r852
snd_timer              28659  2 snd_pcm,snd_seq
nand                   49822  2 r852,sm_common
drm                   180037  4 i915,drm_kms_helper
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop            13515  0 
nand_ids                8547  1 nand
dcdbas                 14054  1 dell_laptop
nand_ecc               13070  1 nand
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
mtd                    26720  2 sm_common,nand
lib80211               14570  3 lib80211_crypt_ccmp,ipw2200,libipw
xhci_hcd               68062  0 
serio_raw              12990  0 
soundcore              12600  1 snd
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
b44                    35301  0 
hid                    77084  1 usbhid
usb_storage            43946  4 
firewire_ohci          31504  0 
ssb                    45942  1 b44
sdhci_pci              13623  0 
uas                    17676  0 
firewire_core          56138  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci                  22720  1 sdhci_pci
bo@bosses:~$ 

Suppose I must have forgotten to install or load something here..... or is it that the card on usb3 do not show up automaticly after I put it in?

I'll boot up Ubuntu with the USB-stick in and see if it is recognised!
If I recall correct - when doing this before I didn't get this result.

Regards
/Gutta

---

### Post by kiyop on 2011-10-18
Thanks for reporting.
You did not do what I asked, but I understand that USB 3.0 port is enabled and necessary modules are loaded before something is connected to USB 3.0 port.

**EDIT at 2011/10/19 12:50 in JAPAN:**
There are mis-copied lines in 
[http://ubuntuforums.org/showpost.php?p=11357916&postcount=58](http://ubuntuforums.org/showpost.php?p=11357916&postcount=58)
> diff -B module1                            <<<<<-----rev 1

module2|grep \>|sed -e "s/^> //"    <<<<---rev 1The correct line is:
```
diff -B module1 module2|grep \>|sed -e "s/^> //"
```That is, the 2 lines should be in a same line. 

Do not make a mistake in refering [my post]("http://ubuntuforums.org/showpost.php?p=11332900&postcount=32").

And "#" expresses that the words after it are comments and the words after it is not executed in terminal.
Thus, if you want to add comment in commands,
the following is better.
```
sudo update-initramfs -u # <<<<----Rev 1
sudo update-grub # <<<<----Rev 1
```I am not sure, but I guess necessary modules are:
xhci_hcd
usbhid
hid
usb_storage
firewire_ohci
sdhci_pci
firewire_core
crc_itu_t
sdhci

I want some guru who knows well about kernel modules help us.

**EDIT at 2011/10/19 22:40 in JAPAN:**
Do according to [#32]("http://ubuntuforums.org/showpost.php?p=11332900&postcount=32") with Ubuntu 11.04 on Iomega assuming that necesarry modules are the above-mentioned.

---

### Post by Gutta Perka on 2011-10-19
OK!

I just went by the computer - and noticed that kiyop also did that.;)

I'll change that in the evening! I'm just now occupied.

Also - I must boot the computer with expresscard and needed devices connected.
(That might be fixed later on by looking in other forums.)

Yesterday I also thought of, if I have the latest or/and best USB3 drivers for Ubuntu 11.04?
You know is the platform on wich I work - the best? Thinking of Debian, Ubuntu 11.10 and so on and to use their USB 3 drivers??

My Respect
/Gutta

---

### Post by Gutta Perka on 2011-10-19
What is happening around us?

We are working with NEC USB 3 [FONT=Arial][SIZE=1](version uPD720200 & uPD720200a)

[/SIZE][/FONT]If you look here - where fresh revisions on NEC USB 3 drivers/firmwares are downloadable.:
[http://www.station-drivers.com/page/renesas.htm](http://www.station-drivers.com/page/renesas.htm)



For me the interesting thing now is that the new chips [FONT=Arial][SIZE=1](uPD720201 & uPD720202)[/SIZE][/FONT]
has got a new driver not fitting the older  (read "now used") chipset.
(Hey - what was wrong with the old ones....;) )

As they are out and new I'll do some research on the net - What is new?

Also I found this - very alike what we are doing:
[http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/458792-boot-problem-nec-bootable-usb-3-port.html](http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/458792-boot-problem-nec-bootable-usb-3-port.html)

They seems to have solved (at least some of) the problems.
For me I must learn more Linux. However I recognized the lingual and the commands.

This was a bit outside this thread in a way - but interesting for me.

And .... yes, I did the changes, kiyop.

With all respect
/Gutta

---

### Post by goldentony111 on 2011-10-19
I have this problem too

---

### Post by kiyop on 2011-10-19
To goldentony> **goldentony111 said:**
> I have this problem too
**Please start a new thread (topic) just for your problem, and write the URL of your new thread in this thread.**
There have been too many replies (partly due to my bad comments) in this thread.
So if you post your matter in this thread, this thread will become more messy.

First, try booting any Ubuntu (Live CD, Live USB, on USB-HDD connected to USB 2.0 port, and so on) without connecting anything to USB 3.0 port (or boot Ubuntu without connecting cards including USB 3.0 port, if possible) and execute like [#32]("http://ubuntuforums.org/showpost.php?p=11332900&postcount=32"):
Open terminal and execute
```
lsmod|sort| tee module1
```Then connect USB media to USB 3.0 port (or shutdown Ubuntu and connect cards including USB 3.0 port and boot) and execute
```
lsmod |sort|tee module2
diff -B module1 module2|grep \>|sed -e "s/^> //"
```Confirm xhci or such module name(s) is/are shown.
If nothing shown, please post the result of
```
lsmod
```If something (modules for USB3.0 port) are shown, go ahead.

If you are running Ubuntu installed on a partition in USB 3.0 HDD (which you want to boot connecting to USB 3.0 port) with usual installation method,
```
gksu gedit /etc/modules
```and add the modules shown and save.
```
gksu gedit /etc/initramfs-tools/modules
```and add the modules shown and save.
Execute
```
sudo update-initramfs -u
sudo update-grub
```You should know the UUID of the Ubuntu / partition of your USB3.0HDD.
```
sudo blkid $(mount|grep " / "|cut -d " " -f1)
```The UUID is shown after
UUID=
Neglect double quotation.

Mount a partition in the internal HDD and copy the current kernel and its initrams files into the root directory of the partition.
The version of the current kernel is shown by
```
uname -r
```and the current kernel is like,
/boot/vmlinuz-...
The initramfs is like,
/boot/initrd.img-...

Download
[http://sourceforge.net/projects/grub4dos/files/GRUB4DOS/grub4dos%200.4.4/grub4dos-0.4.4.zip/download?_test=goal]("http://sourceforge.net/projects/grub4dos/files/GRUB4DOS/grub4dos%200.4.4/grub4dos-0.4.4.zip/download?_test=goal")
and decompress it by commands like
```
unzip [path]/grub4dos-0.4.4.zip
```(Do not forget to change the above "[path]" to the real directory where "grub4dos-0.4.4.zip" exists.)
Copy the following files in the decompressed directory into the partition in the internal HDD.

grldr
grub.exe
menu.lst

Execute:
```
sudo sync
```From here, you should configure boot loader to load grldr.
Please give me the information of the boot loader in the internal HDD.

If you do not know the boot loader, please run the [boot info script]("http://bootinfoscript.sourceforge.net/") and post the contents of the RESULTS.txt.

---

### Post by Gutta Perka on 2011-10-21
In the obove discription there is big risk that the PnP doesn´t work.
If the expresscard AND USB-device aren't connected at the very boottime OS will not find these devices later (windows xp does by "searh for new hardware)).

This might be a flaw in bios or in nec chipset.

I think it's the chipset AND badly written software that interacts with the nec-chipset.

There ARE those using the same chipset that boots and where PnP works.
I have seen in another thread that Laptops from Apple both can boot windows and  Apple OSes selectively with the same hardware as ours.

That is the chipset must be activated "late" in the bootprocess so it can "kick in".

It might be so simple that the chip has a timingissue and isn't "hot" at the start of  the bootingprocess, thereby missing the booting itself?

What we are trying to do might be prolonging the bootprocess so that we boot when the chip is "hot" and tell us "here I am".

That said, is there a way to write a programloop testing for "chipset ready" and kicks in the boot only "if ready."

Me rediculus? I agree!:)

---

### Post by kiyop on 2011-10-21
As for the possible long time required for recognizing device, I have already written in [#22]("http://ubuntuforums.org/showpost.php?p=10558607&postcount=22").
That is, adding "rootdelay=[COLOR=red]seconds[/COLOR]" in kernel option.

As for connecting at boot time, it is not so severe.
With my tool ([kiyoshi's help for debian]("http://kiyoandkei.blog68.fc2.com/blog-entry-52.html") or [for ubuntu (althogh I stopped maintainning)]("http://kiyoandkei.blog68.fc2.com/blog-entry-47.html")) you can wait until you confirm the USB 3.0 port is enabled.
My tool can boot Ubuntu on a partition of an USB-HDD connected at USB 3.0 port even if it is not connected at boot time.

But do not misunderstand what I mean in [#65]("http://ubuntuforums.org/showpost.php?p=11369716&postcount=65"). At first, to know which modules are necessary to recognize USB 3.0, the modules which may not relate to USB 3.0 port are listed in "module1" on purpose. Then the all modules are listed in "module2" when USB 3.0 is enabled. And then module1 and module2 are compared  (by "diff" command) to know the difference.

Furthermore, the error messages must be different if the root partition is not recognized: "(initramfs)".

Because your USB flash connected to USB 3.0 port can be recognized by booting Ubuntu installed in Iomega connected to USB 2.0 port, you need not worry about my method, I believe.

Have you finished doing according to [#32](http://ubuntuforums.org/showpost.php?p=11332900&postcount=32)? What is the result?

---

### Post by Gutta Perka on 2011-10-21
OK! That cleared up things going on in my head.

Now - it's friday evening here and I have the privilidge to work without any breaks for other than food! You will have the full report let's see....

I live in GMT +1, you live in GMT +9. That is for me my time is now 17.00 yours is 23.00 (PM)

When you wake upp, if you are a "normalsleeper" that is, you will have my results served at breakfeast. 
I'm sorry to have kept you waiting, indeed!
You helping me and all.
It's me to exuse!

Now I have several hours free (peasefully)  to concentrate on the task - especially now when I feel konfident in what I'm doing.  

NOW - this has became a sport (I kind of like that) - our time spent on  this boot issue, especially yours on me, can never justyfi the goal.
I hope, if we are lucky, it will benefit others! 

Again excause me for keeping you waiting.

With all my respect,

/Gutta

PS I must boot with the Expresscard in it's place when booting Ubunto on USB 2.  --->Then USB2 stick with LiveDebian on USB3 can "PnP"(recognized) with Ubuntu. If I start without the Expresscard - I never can use it. That is that the Expresscard (with or without USB2 stick mounted in the Expresscard) is/are like dead. DS

To be exact: I must have the expresscard out of the computer for BIOS to show USB-choice  #<<<<<<<<<<<<<<<<<<<<<
When Bios present the USB choice I press in the Expresscard and go USB-booting on USB2 port. # <<<<<<<<<<<<<<<<<
This might effect other things? #<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
I'm still working on with #32.   #<<<<<<<<<<<<<<<REVISION!

---

### Post by Gutta Perka on 2011-10-21
SAD! But here it is: REVISION 2.

> bo@bosses:~$ lsmod|sort| tee module1
aes_generic            38023  1 aes_i586
aes_i586               16956  2 
b44                    35301  0 
binfmt_misc            13213  1 
cfg80211              156212  2 ipw2200,libipw
crc_itu_t              12627  1 firewire_core
cryptd                 19801  0 
dcdbas                 14054  1 dell_laptop
dell_laptop            13515  0 
drm                   180037  4 i915,drm_kms_helper
drm_kms_helper         40745  1 i915
fat                    55505  1 vfat
firewire_core          56138  1 firewire_ohci
firewire_ohci          31504  0 
hid                    77084  1 usbhid
i2c_algo_bit           13184  1 i915
i915                  450944  3 
ipw2200               145664  0 
isofs                  39571  1 
joydev                 17322  0 
lib80211               14570  3 lib80211_crypt_ccmp,ipw2200,libipw
lib80211_crypt_ccmp    12785  2 
libipw                 46641  1 ipw2200
lp                     13349  0 
Module                  Size  Used by
mtd                    26720  2 sm_common,nand
nand                   49822  2 r852,sm_common
nand_ecc               13070  1 nand
nand_ids                8547  1 nand
nls_cp437              12751  1 
nls_iso8859_1          12617  1 
nls_utf8               12493  1 
parport                36746  3 parport_pc,ppdev,lp
parport_pc             32111  0 
ppdev                  12849  0 
psmouse                73312  0 
r852                   17878  0 
sdhci                  22720  1 sdhci_pci
sdhci_pci              13623  0 
serio_raw              12990  0 
sm_common              16737  1 r852
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hwdep              13274  1 snd_hda_codec
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_rawmidi            25269  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_timer              28659  2 snd_pcm,snd_seq
soundcore              12600  1 snd
ssb                    45942  1 b44
uas                    17676  0 
usbhid                 41704  0 
usb_storage            43946  5 
vfat                   17335  1 
video                  18951  1 i915
xhci_hcd               68062  0 
bo@bosses:~$ 
 




bo@bosses:~$ lsmod|sort| tee module2   ### <<<<<Remark: In #32 there is a space after "lsmod"!
aes_generic            38023  1 aes_i586
aes_i586               16956  2 
b44                    35301  0 
binfmt_misc            13213  1 
cfg80211              156212  2 ipw2200,libipw
crc_itu_t              12627  1 firewire_core
cryptd                 19801  0 
dcdbas                 14054  1 dell_laptop
dell_laptop            13515  0 
drm                   180037  4 i915,drm_kms_helper
drm_kms_helper         40745  1 i915
fat                    55505  1 vfat
firewire_core          56138  1 firewire_ohci
firewire_ohci          31504  0 
hid                    77084  1 usbhid
i2c_algo_bit           13184  1 i915
i915                  450944  3 
ipw2200               145664  0 
isofs                  39571  1 
joydev                 17322  0 
lib80211               14570  3 lib80211_crypt_ccmp,ipw2200,libipw
lib80211_crypt_ccmp    12785  2 
libipw                 46641  1 ipw2200
lp                     13349  0 
Module                  Size  Used by
mtd                    26720  2 sm_common,nand
nand                   49822  2 r852,sm_common
nand_ecc               13070  1 nand
nand_ids                8547  1 nand
nls_cp437              12751  1 
nls_iso8859_1          12617  1 
nls_utf8               12493  1 
parport                36746  3 parport_pc,ppdev,lp
parport_pc             32111  0 
ppdev                  12849  0 
psmouse                73312  0 
r852                   17878  0 
sdhci                  22720  1 sdhci_pci
sdhci_pci              13623  0 
serio_raw              12990  0 
sm_common              16737  1 r852
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hwdep              13274  1 snd_hda_codec
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_rawmidi            25269  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_timer              28659  2 snd_pcm,snd_seq
soundcore              12600  1 snd
ssb                    45942  1 b44
uas                    17676  0 
usbhid                 41704  0 
usb_storage            43946  5 
vfat                   17335  1 
video                  18951  1 i915
xhci_hcd               68062  0 
bo@bosses:~$



bo@bosses:~$ diff -B module1 module2|grep \>|sed -e "s/^> //"
bo@bosses:~$ 
(Nothing returned)

I confirm that both "lsmod-command" returns a "xhci" in module1 and in module2.
Nothing reported by the last command.

OK here we go:

bo@bosses:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17335  1 
fat                    55505  1 vfat
cryptd                 19801  0 
aes_i586               16956  2 
aes_generic            38023  1 aes_i586
lib80211_crypt_ccmp    12785  2 
nls_utf8               12493  1 
isofs                  39571  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
i915                  450944  3 
snd_rawmidi            25269  1 snd_seq_midi
ipw2200               145664  0 
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17322  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
libipw                 46641  1 ipw2200
binfmt_misc            13213  1 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         40745  1 i915
r852                   17878  0 
dell_laptop            13515  0 
sm_common              16737  1 r852
drm                   180037  4 i915,drm_kms_helper
cfg80211              156212  2 ipw2200,libipw
psmouse                73312  0 
nand                   49822  2 r852,sm_common
dcdbas                 14054  1 dell_laptop
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mtd                    26720  2 sm_common,nand
serio_raw              12990  0 
xhci_hcd               68062  0 
i2c_algo_bit           13184  1 i915
lib80211               14570  3 lib80211_crypt_ccmp,ipw2200,libipw
soundcore              12600  1 snd
video                  18951  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
b44                    35301  0 
firewire_ohci          31504  0 
usb_storage            43946  5 
ssb                    45942  1 b44
firewire_core          56138  1 firewire_ohci
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
uas                    17676  0 
crc_itu_t              12627  1 firewire_core
bo@bosses:~$ 

USB3 referer could it be some of these:
xhci_hcd               68062  0 
usbhid                 41704  0 
hid                    77084  1 usbhid
b44                    35301  0 
usb_storage            43946  5 
ssb                    45942  1 b44
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
uas                    17676  0 

More see complete listing obove.
????
usb-livedebian is still connected to USB 3 port!

I added these - only "lp" was shown in "modules (/etc)":
so now "modules (/etc)" contain the following:

xhci_hcd               68062  0 
usbhid                 41704  0 
hid                    77084  1 usbhid
b44                    35301  0 
usb_storage            43946  5 
ssb                    45942  1 b44
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
uas                    17676  0

I have a strong feeling that these are to many.
Perhaps xhci_hcd is the only one needed since I have seen this so many times???

OK ! I save and go on. Here I had to stop and restart the terminal.
Afterwards to my understanding it was due to that I didn't close the "gedit session" in "gedit".

Here I was kicked out:

bo@bosses:~$ gksu gedit /etc/initramfs-tools/modules

(gedit:2331): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Filen eller katalogen finns inte

(gedit:2331): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Misslyckades med att skapa filen "/root/.local/share/recently-used.xbel.VPD33V": Filen eller katalogen finns inte

(gedit:2331): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Filen eller katalogen finns inte

(gedit:2331): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Misslyckades med att skapa filen "/root/.local/share/recently-used.xbel.5DON3V": Filen eller katalogen finns inte

(gedit:2331): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Filen eller katalogen finns inte
bo@bosses:~$ 

=============================ADDED - REVISION===========================================
Sitting looking at what I did send to you I noticed errors done by me.
I just copied the listing with all postfixes (that is what is after the module, size etc) into the modules.
I opened of cause the module files and took away that in both module files.
Saved - and yes - another error log:

bo@bosses:~$ gksu gedit /etc/modules

#While saving I got these:

(gedit:3683): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Filen eller katalogen finns inte

(gedit:3683): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Misslyckades med att skapa filen "/root/.local/share/recently-used.xbel.G8653V": Filen eller katalogen finns inte

(gedit:3683): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Filen eller katalogen finns inte

(gedit:3683): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Misslyckades med att skapa filen "/root/.local/share/recently-used.xbel.0KJZ3V": Filen eller katalogen finns inte

(gedit:3683): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Filen eller katalogen finns inte
bo@bosses:~$ gksu gedit /etc/initramfs-tools/modules

(gedit:3706): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Misslyckades med att skapa filen "/root/.local/share/recently-used.xbel.RXHP3V": Filen eller katalogen finns inte

(gedit:3706): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Filen eller katalogen finns inte

(gedit:3706): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Misslyckades med att skapa filen "/root/.local/share/recently-used.xbel.YWQ33V": Filen eller katalogen finns inte

(gedit:3706): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Filen eller katalogen finns inte
bo@bosses:~$ gksu gedit /etc/modules

(gedit:3719): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Misslyckades med att skapa filen "/root/.local/share/recently-used.xbel.D9UN3V": Filen eller katalogen finns inte

(gedit:3719): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Filen eller katalogen finns inte

(gedit:3719): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Misslyckades med att skapa filen "/root/.local/share/recently-used.xbel.2F4Q3V": Filen eller katalogen finns inte

(gedit:3719): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Filen eller katalogen finns inte
bo@bosses:~$ gksu gedit /etc/initramfs-tools/modules

(gedit:3731): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Misslyckades med att skapa filen "/root/.local/share/recently-used.xbel.X81S3V": Filen eller katalogen finns inte

(gedit:3731): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Filen eller katalogen finns inte

(gedit:3731): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Misslyckades med att skapa filen "/root/.local/share/recently-used.xbel.Y0IX3V": Filen eller katalogen finns inte

(gedit:3731): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Filen eller katalogen finns inte

(gedit:3731): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Misslyckades med att skapa filen "/root/.local/share/recently-used.xbel.87953V": Filen eller katalogen finns inte

(gedit:3731): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Filen eller katalogen finns inte
bo@bosses:~$ ^C
----
Translating: "Filen eller katalogen finns inte" is in English like this "The file or catalog does not exist"
Translating: "Misslyckades med att skapa filen" is in English like this "Failure in creating the file" 
----
Sad to say - another set of errors that denied me permissions.

I'll go on reading "Setting permissions in Ubuntu.
But first:
-->"Managing users in Ubuntu"
-->"A short, practical guide to user management in Ubuntu and GNU/Linux"


===================================END REVISION====================================



I suppose you have the numbers of "gedit" warnings.
It tells me that the filecatalog does not exists or failed to creat it.
All over my understanding - I opened it and there was comments in it how to edit that file but nothing else.

OK! I'll start digging in those cataloges as "admin" to see if I find something.
Saving this gedit-session now and come back to tell you if I find someting in the area mensioned by the errorlog above!
..
..
Will be back soon
..
..
Please wai!
..
..
Hey a dot in front of the name means: "unseen"!
Manual to be picked. Something like "ls - show all"????
Help only wants to help me with this "gedit" session.
Time to point on therminal and look there?
Sakura therminal has no help!!! Tryng Sakura-therminal options
to mount "help"....right click ... negative no options for help in Sakura.
...
I'll download another therminal with "help" in it!
...Rember from that old true Unix days - logout and then "log in as /root"
I will give it a try!
...
...will soon be back.
...FAILED!
...Must go out to the internet!
...Sorry!
Thinking...
Thinking...
...
...
Now I see I have to study how to create a "root-user" or someting like "superuser".
I'm not allowed myself to touch anything over my own head!

Sad ... I really had it in my bones to continue this.

I have started reading:
-->"Managing users in Ubuntu"
-->"A short, practical guide to user management in Ubuntu and GNU/Linux"

It will be late when I put out the light!
I must have other settings in "old Ubuntu" install because I don't   remember these errors - or I didn't notice them - after a command   results rush by in a hi speed. 

So - I'll be back mid-Sunday! Tomorrow my wife directs me! (smile!)

Sad it is my lack of knowledge that hinder(stops?) the progress!  
I really intended to finish #32. 


With all my respect
/Gutta

---

### Post by kiyop on 2011-10-21
> **Gutta Perka said:**
> PS I must boot with the Expresscard in it's place when booting Ubunto on USB 2.  --->Then USB2 stick with LiveDebian on USB3 can "PnP"(recognized) with Ubuntu. If I start without the Expresscard - I never can use it.
What is the last "it"? If the last "it" means USB 3.0 Expresscard, first boot with ubuntu on Iomega connected to USB 2.0 port **without connecting the USB 3.0 Expresscard** and execute "lsmod|sort|tee module1" and shutdown and connect USB 3.0 Expresscard and boot with the ubuntu again and go ahead from "lsmod|sort|tee module2".

> **Gutta Perka said:**
> To be exact: I must have the expresscard out of the computer for BIOS to show USB-choice  #<<<<<<<<<<<<<<<<<<<<<
When Bios present the USB choice I press in the Expresscard and go USB-booting on USB2 port. 
I am confused.
You cannot select "USB 2 port" at BIOS if you connected the expresscard, can you?
Do you connect the expresscard after you reach BIOS (boot selection menu)?

---

### Post by kiyop on 2011-10-21
> **Gutta Perka said:**
> > bo@bosses:~$ lsmod|sort| tee module1
aes_generic            38023  1 aes_i586
...
lp                     13349  0 
Module                  Size  Used by
mtd                    26720  2 sm_common,nand
...
xhci_hcd               68062  0 
bo@bosses:~$ 
Did you make a mistake on copy and pasting the above?
The line " Module                  Size  Used by" should be shown at first.

> **Gutta Perka said:**
> > bo@bosses:~$ lsmod|sort| tee module2   ### <<<<<Remark: In #32 there is a space after "lsmod"! 
Whether there is a space after "lsmod" or not does not matter.
Relax. :)

> **Gutta Perka said:**
> > so now "modules (/etc)" contain the following:

xhci_hcd               68062  0 
usbhid                 41704  0 
hid                    77084  1 usbhid
b44                    35301  0 
usb_storage            43946  5 
ssb                    45942  1 b44
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
uas                    17676  0
> **Gutta Perka said:**
> > =============================ADDED - REVISION==========================================  =
Sitting looking at what I did send to you I noticed errors done by me.
I just copied the listing with all postfixes (that is what is after the module, size etc) into the modules.
I opened of cause the module files and took away that in both module files.

As you understood, each of only the name of modules (without ".ko" without "Size" without information on "used by") must be written on each line in /etc/modules and /etc/initramfs-tools/modules.

> **Gutta Perka said:**
> > Here I had to stop and restart the terminal.
Afterwards to my understanding it was due to that I didn't close the "gedit session" in "gedit".
You are right. Close gedit window after editing and saving the files.

> **Gutta Perka said:**
> > bo@bosses:~$ gksu gedit /etc/modules

#While saving I got these:

(gedit:3683): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: Filen eller katalogen finns inte
.......

I think you need not worry about the above errors.
The error means that it was failed to set the permissions of /root/.local/share/recently-used.xbel.
 The aim is to add the names of modules into /etc/modules and /etc/initramfs-tools/modules.
To make sure, 
```
more /etc/modules
more /etc/initramfs-tools/modules
```to check if the module names are added.

If they are correctly added like
```
xhci_hcd 
usbhid 
hid
b44 
usb_storage 
ssb
sdhci_pci 
sdhci
uas
```then go ahead. :)

---

### Post by Gutta Perka on 2011-10-21
Time now 01.43 AM, reading the manual in bed. Before I put out the lamp I thought I should look for you here. So I hope this will answer your questions.

> I am confused.
You cannot select "USB 2 port" at BIOS if you connected the expresscard, can you?
Do you connect the expresscard after you reach BIOS (boot selection menu)?I understand that you are confused.

If the expresscard device is connected when starting up the computer - then bios don't show the USB option. It's not in the list of presented booting devices.
(remark: computer from 2005)

There is also a funktion to be set in BIOS: from my remembering like this "Do you want the BIOS to poll for USB-devices during BOOT - up?" My answer is set to "Yes".
I think this is to "help" OS to recognize the USB-ports in those early USB-days. That also might be a "savior" for me! In todays computers I think that question is set aside
and BIOS is allways "helping" OS:es in finding USB:s. 

The procedure:

a/ Yes - I start without the expresscard
b/ Press f12 to reach bios settings - NOW presenting the choice of an USB-boot.
c/ Before choosing USB boot I press in the expresscard.
d/ Now choosing USB-boot and press C/R
e/ Now Ubunto boots on USB2.
f/ Everything works - Ubuntu finds the Expresscard and later automaticly "PnP-finds" the LiveDebian USB stick in USB3 when I put it into the expresscard. (And yes - no booting on USB3 allowed - just don't work for booting)

More to this issue.
If I put in the expresscard AFTER I have booted Ubuntu it never connects to OS.
It's like dead! No PnP finding there. Just a restart/rebooting using the procedure mensioned above helps! In windows XP I might find it using "Find and install new hardware" that is - not the PnP-way.

Now I must rest! I hope you are having a nice morning.

By the way - I should more often use the "sudo-command" according to the manual, when doing things near the /root.

Thanks for You caring, kiyop!

With all my respect
/Gutta

---

### Post by kiyop on 2011-10-21
Thanks for your nice report :D
Please take a rest. :)

Tomorrow or later, please read the following.

Now I understand how difficult your situation is.
I am very happy to **struggle** to enable booting from USB 3.0 Expresscard you have. :D

> **Gutta Perka said:**
> If the expresscard device is connected when starting up the computer - then bios don't show the USB option. It's not in the list of presented booting devices.
(remark: computer from 2005)

There is also a funktion to be set in BIOS: from my remembering like this "Do you want the BIOS to poll for USB-devices during BOOT - up?" My answer is set to "Yes".
I think this is to "help" OS to recognize the USB-ports in those early USB-days. That also might be a "savior" for me! In todays computers I think that question is set aside
and BIOS is allways "helping" OS:es in finding USB:s. 

The procedure:

a/ Yes - I start without the expresscard
b/ Press f12 to reach bios settings - NOW presenting the choice of an USB-boot.
c/ Before choosing USB boot I press in the expresscard.
d/ Now choosing USB-boot and press C/R
e/ Now Ubunto boots on USB2.
f/ Everything works - Ubuntu finds the Expresscard and later automaticly "PnP-finds" the LiveDebian USB stick in USB3 when I put it into the expresscard. (And yes - no booting on USB3 allowed - just don't work for booting)

More to this issue.
If I put in the expresscard AFTER I have booted Ubuntu it never connects to OS.
It's like dead! No PnP finding there. Just a restart/rebooting using the procedure mensioned above helps! In windows XP I might find it using "Find and install new hardware" that is - not the PnP-way.
<A> If you put in the expresscard after you have booted Ubuntu, can you continue using Ubuntu installed in Iomega?
<B> If you does not put in the expresscard, can you boot ubuntu installed in Iomega?

If you can continue using Ubuntu (<A>) or can boot Ubuntu (<B>), execute
```
sudo rm module1 module2 # to delete module1 and module2 with root privilege

lsmod|sort|tee module1
```and restart and go through the above a) to f), and then
```
lsmod|sort|tee module2[FONT=monospace]

[/FONT]diff -B module1 module2
```and post the result.

---

### Post by Gutta Perka on 2011-10-22
Wife went to town - that is for me going on with the #32 mission.:)

You wrote:

> <A> If you put in the expresscard after you have booted Ubuntu, can you continue using Ubuntu installed in Iomega?
<B> If you does not put in the expresscard, can you boot ubuntu installed in Iomega?

If you can continue using Ubuntu (<A>) or can boot Ubuntu (<B>), execute
     Code:
     sudo rm module1 module2 # to delete module1 and module2 with root privilege  lsmod|sort|tee module1 
and restart and go through the above a) to f), and then
     Code:
     lsmod|sort|tee module2diff -B module1 module2 
and post the result.With all respect kiyop....
Can you remind me later on this matter.

Now I want to start finishing #32 as on a straight line.
So let's finish that one first.
I checked with gedit that the module1 and module2 contains what it should. I don't feel to remove those for other tests and then rebuild them.

OK! Here we go/continue:

Session in UBUNTO -report before going to boot windows:
> bo@bosses:~$ sudo update-initramfs -u
[sudo] password for bo: 
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
bo@bosses:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows NT/2000/XP (loader) on /dev/sda1
done
bo@bosses:~$ 
bo@bosses:~$ 
bo@bosses:~$ 
bo@bosses:~$ sudo blkid $(mount|grep " / "|cut -d " " -f1)
/dev/sdb1: UUID="1f66e765-7888-49d5-aa82-bdb82263ab63" TYPE="ext3" 
bo@bosses:~$ 
bo@bosses:~$ 
bo@bosses:~$ uname -r
2.6.38-8-generic
bo@bosses:~$ 
bo@bosses:~$ 
bo@bosses:~$ 


And copying to windows root:
/boot/vmlinuz-...
The initramfs is like,
/boot/initrd.img-...

kiyop - you are aware that /boot/initrd.img-2.6.38-8-generic is a "gz" file???
Perhaps that coming later. In that compressed file I find no other initrd.img-2.6.38-8-generic file. So I do as told to.
Also I copy the grub-files you asked me to do into windows root by just draging them around with the mousepointer.

Please let me know.

At last before logging out and boot windows i:
bo@bosses:~$ sudo sync
[sudo] password for bo: 
bo@bosses:~$ 

That's it for now in UBUNTU.
I send this as a report to you.

Later there will be another report/discription from me.
Remark:
When I started this with a new Ubunto 11.04, #32 etc  I also med fixed the Windows MBR and bootfiles to be clean windows ones. 

/Gutta


---

### Post by Gutta Perka on 2011-10-22
Report from Gutta in windows:

> Now in windows:
"boot.ini" 

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
/fastdetect


This gives in a stright boot one line "one-only-option" to boot Win XP.

now I add c:\grldr="grub4dos"

To be remembered Win XP boots on D:, UBUNTU on C:

 
Now I save boot ini as:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
/fastdetect
c:\grldr="grub4dos"


Here I'm not sure about the "/fastdetect" - might hinder a wider space of devices to boot.
Look here --- link:

[http://www.maxi-pedia.com/fastdetect+boot.ini+option+parameter](http://www.maxi-pedia.com/fastdetect+boot.ini+option+parameter)


OK! Now for "menu.lst":

It now ends with:

title ubuntu on Iomega
kernel /vmlinuz-2.6.38-8-generic root=UUID=1f66e765-7888-49d5-aa82-bdb82263ab63 ro
initrd /initrd.img-2.6.38-8-generic

God bless me - as you said - now is the first time to try booting Ubuntu on USB3...
I'm still worried of the "gz" file we transported to windows root.
Also worried about the place where "/fastdetect" should be.
(I myself would like to delete that command in boot.ini.)

I'll send this to you just now as a report.

I'll be booting around!

/Gutta

OK! kiyop here we go - let's test the prototype!:D

---

### Post by Gutta Perka on 2011-10-22
From outer space!!
=====================================
Calling -kiyop, kiyop -Japan spacecenter
......
Gutta from Eagle...
Gutta from Eagle... come..

Confirm Eagle has landed!!!
Gutta has landed!!!!!!

Gutta on Eagle will now see if Eagle satellite Windows XP also will land.
Gutta on Eagle suggest to destroy Windows XP satelite and only Use Ubuntu Eagle.


======================================

Ok I'm very happy!
Windows is now a minor "issue".

1/ I did not even took out the expresscard when booting.
2/ I did not to press any "F8" at start up.
3/ Did not chose USB in BIOS.

Then I had the choices "grub4dos" and "windows."
My choice fell on "grub4dos".
 Now "grub" presented A LOT of selections. At the very bottom was "Ubunto on Iomega".
I selected that ...:) and went on!
The screen rolled on with a lot of text and at last Ubuntu continued booting.

Can "grub4dos" screen be "automated" choosing "Ubuntu on Iomega"?

THANKS!
You knew this!:D

All of a sudden I hear my wife parking the car!

That is .- timing!

Now I want to hear some of your satisfaction expressed here, kiyop!!

Are you going to mark this thread as "SOLVED" or do you want to do some polishing first.
(Like automating the process.... ;))

With my greatest respect AND THANK YOU for your Patience with me!!!!
I'm eager to hear from You soon!

**Revision**: Tested and of cause windows booted as well!!
**Revision:** See my next inlay. A little bit polishing needed
/Gutta 


[SIZE=4][/SIZE][SIZE=4][/SIZE]

---

### Post by Gutta Perka on 2011-10-22
OK! I just come home again being out with my wife on a party.

When i went this afternoon I just shut down the computer.

When starting the computer from "cold" I got these errors:
First some choices to be made.

Windows : Choice "grub4dos"
Grub4dos: Choice "Iomega on USB3"

Lots of screens went by that ended like this:
> 
Gave up waiting for root device. Common problems.
-Boot args (cat /proc/cmdline)
-Check rootdelays = (did the system wait long enough?)
-Check root= = (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)

Alert! /dev/disk/by-uuid/1f66e765-7888-49d5-aa82-bdb82263ab63 does not exist

Dropping to shell
Busybox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) build-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

## Here the boot stopped.

I sat looking at this log.
Two of them indicated "finding wrong device" Those are::

> -Check root= = (did the system wait for the right device?)
Alert! /dev/disk/by-uuid/1f66e765-7888-49d5-aa82-bdb82263ab63 does not exist


A logical answer could be that the wrong USB3 port was "polled".

I changed the Iomega to the other USB 3 port (there are two of them)

AND - Ubuntu directly booted on this USB3 port.

The process need a little polishing I think!
I'm sure you can give me a hint.

With all my respect.
/Gutta

---

### Post by kiyop on 2011-10-22
I am really happy to hear that you can boot Ubuntu on Iomega connected to USB 3.0 port. :D

And I think I need not answer the question in [#74]("http://ubuntuforums.org/showpost.php?p=11379192&postcount=74") and [#75]("http://ubuntuforums.org/showpost.php?p=11379359&postcount=75").
If you want me to answer them, please let me know.

> **Gutta Perka said:**
> When starting the computer from "cold" I got these errors:
First some choices to be made.

Windows : Choice "grub4dos"
Grub4dos: Choice "Iomega on USB3"

Lots of screens went by that ended like this:
> Gave up waiting for root device. Common problems.
-Boot args (cat /proc/cmdline)
-Check rootdelays = (did the system wait long enough?)
-Check root= = (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)

Alert! /dev/disk/by-uuid/1f66e765-7888-49d5-aa82-bdb82263ab63 does not exist

Dropping to shell
Busybox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) build-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)

## Here the boot stopped.                      I sat looking at this log.
Two of them indicated "finding wrong device" Those are::
[quote]-Check root= = (did the system wait for the right device?)
Alert! /dev/disk/by-uuid/1f66e765-7888-49d5-aa82-bdb82263ab63 does not exist                      A logical answer could be that the wrong USB3 port was "polled".

I changed the Iomega to the other USB 3 port (there are two of them)

AND - Ubuntu directly booted on this USB3 port.
[/QUOTE]
Your solution (pullout Iomega from USB3 port and reconnect it to USB3 port) is very good one.
You know, the kernel (/vmlinuz-2.6.38-8-generic) and the initramfs (/initrd.img-2.6.38-8-generic) in windows XP c drive were correctly loaded and the loaded kernel and initramfs started booting Ubuntu but could not find Ubuntu / partition with UUID=1f66e765-7888-49d5-aa82-bdb82263ab63 and gave the above error message.
As you wrote, the problem may be due to long time required for recognition of USB3 port and Iomega. But by **the kernel**.
Reconnecting to the same port may be effective, I guess.
To make the kernel wait for more long time, you should add "rootdelay=" option as I wrote in [#22]("http://ubuntuforums.org/showpost.php?p=10558607&postcount=22").
Another possibility is that reconnection urged the kernel to re-recognizing the connected devices. I had also similar situation when a partition in USB-HDD connected to USB3 port has filesystem error. At that time, I solved the problem by executing file system check "e2fsck -f -y".

> **Gutta Perka said:**
> 
 Now "grub" presented A LOT of selections. At the very bottom was "Ubunto on Iomega".
I selected that ...:smile: and went on!
The screen rolled on with a lot of text and at last Ubuntu continued booting.

Can "grub4dos" screen be "automated" choosing "Ubuntu on Iomega"?

Boot Windows XP and edit c:\menu.lst  as
```
timeout 5
default 0

title ubuntu on Iomega
kernel /vmlinuz-2.6.38-8-generic root=UUID=1f66e765-7888-49d5-aa82-bdb82263ab63 ro quiet splash rootdelay=10
initrd /initrd.img-2.6.38-8-generic

title windows XP PBR of partition with /ntldr
find --set-root --ignore-floppies /ntldr
chainloader +1

title windows XP ntldr
find --set-root --ignore-floppies /ntldr
chainloader /ntldr

```Grub4dos will count 5 seconds and automatically start booting Ubuntu (because of "timeout 5" and "default 0").
Long text message will not be shown (because of "quiet splash").
10 seconds will be waited by kernel before trying to find Ubuntu / partition (because of "rootdelay=10").

> **Gutta Perka said:**
> 
  Are you going to mark this thread as "SOLVED" or do you want to do some polishing first.

I am not the opening poster [numb7rs]("http://ubuntuforums.org/member.php?u=1192843") of this topic (thread), so I cannot edit the title of this thread.
This thead is not originally for your problem.
It is a kind of "Thread (topic) Hijacking". :D

There are another problems in your situation.
One big problem is that you cannot use a newer kernel even after the newer kernel is installed in future.
You should manually generate the initramfs for the newer kernel and copy the newer kernel and the initramfs into Windows XP c drive and edit c:\menu.lst, if you want to use the newer kernel.
There is one way to automatically use the newer kernel; my tool, [kiyoshi's help]("http://kiyoandkei.blog68.fc2.com/blog-entry-52.html"). It can even boot another linux using one of the following kernel loader; Grub2, Grub legacy, grub4dos, lilo, syslinux, extlinux, isolinux.
But, I do not recommend you to use kiyoshi's help. It needs much knowledge to utilize it.

I guess that now your computer is booting like the following (although I partly forgot what you have done in this long thread):
Step 1) 
MBR in internal HDD -> PBR of /dev/sda1 (internal HDD first partition = Windows XP c drivce) -> ntldr - \boot.ini
Step 2-A)
Choice "Windows" -> NTDETECT.COM and so on (I am not sure) -> Windows XP.
Step 2-B)
Choice "grub4dos" -> \grldr -> searching /menu.lst -> c:\menu.lst
-> Choice "Iomega on USB3" -> /vmlinuz-2.6.38-8-generic in c:\ (/dev/sda1) and /initrd.img-2.6.38-8-generic in c:\ -> kernel tries to find partition with UUID=1f66e765-7888-49d5-aa82-bdb82263ab63

With kiyoshi's help, the above (from Step 2-B) can be changed to:
Step 2-B)
Choice "grub4dos" -> \grldr -> searching /menu.lst -> c:\menu.lst 
-> Choice "kiyoshi's help" -> /vmlinuz-2.6.38-8-generic in c:\ (/dev/sda1) and /initrd.img-kiyoCs (with kiyoshi's help) in c:\ 
-> kiyoshi's help wait for your pressing "ENTER" key 
-> your pressing "ENTER" key 
-> kiyoshi's help searches for all the partitions recognized and list the partitions. 
-> your selecting a partition
-> kiyoshi's help tries to mount the selected partition and ask you which you want; find "configuration files" or "manually boot"
Step 3-A)
-> Select "find configuration files"
-> kiyoshi's help find the configuration files such as /boot/grub/grub.cfg for Grub2 and so on, and list the menu entries found
-> Select one of the found menu entries
-> kiyoshi's help ask if you want to change the contents of boot configuration
-> you can edit or boot
->** Thanks to Great Tool "kexec"**, kiyoshi's help overwrite the kernel to be booted onto the kernel (in RAM) in use with the initramfs specified
-> If success, linux kernel and initramfs to be loaded is loaded and started.
Step 3-B)
-> Select "manual"
-> You can use shell like sh and can use kexec.

---

### Post by Gutta Perka on 2011-10-22
OK!

I'll read your guide carefully later.

The problem with the two USB 3 ports is solved.

With the expresscard there is a "dummy" USB cable to get extra power from another USB port.
This one must be defect, because when I removed it I can easily boot from any of the two USB3 ports.
That is I think both USB3 ports are "polled". 

No problems for me - the Iomega has an Y-Usb cable where one of them is a "dummy" one for that extra power. 

I changed the "menu.lst" - now it's perfect. (Those 10 extra seconds aren't needed)

Now for some testing.

In programs-system there there is a program "Disktools"

Testing readingspeed(writeprotected) on Iomega botted on USB2:
Highest 35.8 MB/s
Average 33.8

Testing readingspeed(writeprotected) on Iomega botted on USB3:
Highest 112 MB/s
Average 80

Testing readingspeed(writeprotected) on internal old HD:
Highest 38 MB/s
Average 30:

One should be careful doing tests but it indicates that the Iomega is at least twice as fast.
There are certainly better test tools out the. Doing tests with other programs in Windows XP shows much better results.

That is - Iomega/USB3 running Ubunto schould run conciderly faster than running Windows XP on the old IDE HD.

Now I can enjoy Linux!!

More to this later.

THANKS!

With all my respect
/Gutta
-

---

### Post by Gutta Perka on 2011-10-23
**Nota Bene!** (Lat!)

For others out there not to be confused:

kiyop wrote:> MBR in internal HDD -> PBR of /dev/sda1 (internal HDD first partition = Windows XP c drivce) -> ntldr - \boot.iniI have on many places tried to say directly and indirectly that Windows is on D: drive and  Ubuntu on C:drive.

I, in many places I ignored that, and went on "doing it my way".

I understood what kiyop ment and I have fully understanding for that.

Me? Yes - not many have a windows on his/laptop on the only internal hard drive named D:
I think it was me trying to reformat the Dell laptop. When doing so I found a hidden partition
made at factory that contained lots of interesting things. It contained things to control
MMC and those extra buttons for sound etc. It also contained a complete compressed Windows Home "Especially Simple".

That is if I crashed the Dell hard drive Dell support could help you by asking you to do a certain key sequence  (CTRL-Alt - F11 at a certain place when booting up) and by that making the DELL "factory fresh")
Knowing that, when partitioning and not being able to "destroy" that secret partition my choice was easy. I named user windows partition to "D:"

So fellows - now you know why that very Swede has an internal drive named "D:"

I was lucky there - I have later learned that a big part of Dell BIOS is .... yes on the hard drive.

That is why many don't succeed putting in a new bigger hard drive in DELL. They must exactly mirror, sector by sector, the old hard drive part to the new hard drive. 
That said - however big hard drive you bought - DELL laptop has a hardware limit - biggest usable partition is around 133 GB on an old IDE IDE buss.

That's why I bought the Iomega USB 3 HDD with one TB and at greater speed.
The processor speed is OK - 1.9 Ghz. 

For that other money,spent on a new laptop, my wife and I can dress up and go to a concert in Copenhagen (just about 110 km away) with my renovated perlwhite Mercedes Benz 250 SE coupé 1967 
with blood red leather and wood panels handmade of palicander. Not to forget all that chrome!! 

Don't forget that life is what you do with it!
But don't follow that device to far - then life is boring. 

kyiop and all the others out there - take care - with exactly that very qualities kyiop has shown here!!!

With all my respect

"FIAT LUX!" ©
/Gutta

---

### Post by kiyop on 2011-10-23
To everybody who cannot boot Ubuntu installed in an external media connected to USB 3.0 port,

Please read [#16]("http://ubuntuforums.org/showthread.php?p=10472525#post10472525") - [#28]("http://ubuntuforums.org/showthread.php?p=11100306#post11100306") in this thread.
[#32]("http://ubuntuforums.org/showthread.php?p=11332900#post11332900") may also be helpful, in the case Windows XP is installed in the internal HDD.

To Gutta Perka

> **Gutta Perka said:**
> With the expresscard there is a "dummy" USB cable to get extra power from another USB port.
This one must be defect, because when I removed it I can easily boot from any of the two USB3 ports.
That is I think both USB3 ports are "polled". 

No problems for me - the Iomega has an Y-Usb cable where one of them is a "dummy" one for that extra power. 
I see. Thanks for your reporting.

> **Gutta Perka said:**
> I have on many places tried to say directly and indirectly that Windows is on D: drive and  Ubuntu on C:drive.

I, in many places I ignored that, and went on "doing it my way".
Do you know "C:" or "D:" drive expressed in Windows means a partition rather than a hard disk (device, media)?
Furthermore, in Windows, ext2, ext3, ext4 partitions are usually not recognized and so the name of "C:" or so is usually not attributed to ext2, ext3, ext4 partitions.

As for "D:" of windows XP system drive (partition) in your internal HDD, I have noticed.
But I continued to use "C:" for Windows system partition in your internal HDD, on purpose (to check your understanding and your ability to apply your knowledge to your problem) because I thought "C:" for Ubuntu / partition (not to the external HDD) is wrong.
But you understood correctly and succeeded. Congratulations! :p

> **Gutta Perka said:**
> 
I think it was me trying to reformat the Dell laptop. When doing so I found a hidden partition
made at factory that contained lots of interesting things. It contained things to control
MMC and those extra buttons for sound etc. It also contained a complete compressed Windows Home "Especially Simple".

That is if I crashed the Dell hard drive Dell support could help you by asking you to do a certain key sequence (CTRL-Alt - F11 at a certain place when booting up) and by that making the DELL "factory fresh")
Knowing that, when partitioning and not being able to "destroy" that secret partition my choice was easy. I named user windows partition to "D:"
Thanks for your nice explanation on the superiority of using Grub4dos without changing (installing Grub4dos code to) MBR and the following sectors in the internal HDD, without changing partitions in the internal HDD.

---

### Post by Gutta Perka on 2011-10-24
OT!

> Thanks for your nice explanation on the superiority of using Grub4dos  without changing (installing Grub4dos code to) MBR and the following  sectors in the internal HDD, without changing partitions in the internal  HDDI wasn't superior there it was me being plain scared.
This was a struggle behind the scene.

Behind the scene I was studying people having trouble changing HDD on certain DELL's on the Internet. I did learn a lot there but none fully understand what DELL have done. I believe BIOS is split first in hardware between the the BIOS-chip and certain parts hard cored to HDD - BUT with some sectors (parts of MBR etc) writable. (DELL might have saved an PROM there)

None really understands it - I know parts of how it is acting from people on the net trying to crack the secret.

NOTA BENE!
DELL "makes it easy"  for customers to chose a new a new HDD for their products AS LONG as you buy a spares from DELL. That is - that new drive is prepared for that very model AND country.
The pricetag compared to  "the around your corner cheep computer shop -HDD) is huge.
 
That's money talking!!!:D  (DELL might also think You need a new DELL laptop? That's even more money talking!)

I pulled their legs - I bought the Iomega/USB3 port.
First I thought I was fooled when I couldn't boot from BIOS choice USB.
However - You made it work.
Bi product - I have learnt a lot - brutally forced into the inner space of Linux kernel and all that stuff.

And a new love here  - "grub4dos" that is!

With all my respect!

FIAT LUX! ©
Gutta Perka

---

### Post by Gutta Perka on 2011-10-24
Tell me the luck that lasts?

Now sitting here with Ubuntu on USB 2. Here everything is fine!

Had to because the WLAN doesn't work with Ubuntu on USB 3.
Connected by cable works - but that's not the way I work.
Trying to fix it - gives me an out of sync screen giving me the only choice -  to unplug the DELL.
Could it be that those files in the modules was too wild chosen???

Nothing changed by me!!

????????????????:(

BTW - how do you, on your command, empty buffered writing/reading before removing an USB-device?

FIAT LUX! ©
/Gutta

---

### Post by kiyop on 2011-10-24
> **Gutta Perka said:**
> Had to because the WLAN doesn't work with Ubuntu on USB 3.
Connected by cable works - but that's not the way I work.
Trying to fix it - gives me an out of sync screen giving me the only choice -  to unplug the DELL.
Could it be that those files in the modules was too wild chosen???
I do not know whether some modules listed in /etc/initramfs-tools/modules prevent WLAN or not.
But you can remove some module names in /etc/initramfs-tools/modules and generate a new initramfs by
```
sudo update-initramfs -u
```and replace the old /vmlinuz-... in Windows System partition (D: ?) with the generated /boot/vmlinuz-...

You can test which modules are not necessary.

Indeed, I had the following experience.
I added all the modules used in debian sid into /etc/initramfs-tools/modules by
```
lsmod|grep -v Module|cut -d " " -f1 >> /etc/initramfs-tools/modules
```and generated kiyoshi's help. With the kiyoshi's help, I could not boot my USB-HDD connected to USB 3.0 port in one of my computers.
Definitely, some modules prevent from booting Linux correctly.

> **Gutta Perka said:**
> how do you, on your command, empty buffered writing/reading before removing an USB-device?
Maybe
```
sudo sync
sudo umount -l /MOUNT_PATH
```

---

### Post by Gutta Perka on 2011-10-25
Didn't tell you but I have done lots of things trying to make Ubuntu more appealing for my taste.
I want multiple drop-lists, simple gray background and a more clean look. I hate 18x18 mm big colourfull bottoms - that said I've trying to squeeze Ubunto to my taste - but done many errors doing so.

I also might have been careless with the read/write-buffers disconnecting th Iomega.

Now with better knowledge I reinstalled Ubuntu and re fixed the grub4dos things. That is about 1 1/2 hour only compared to undo things in Ubuntu.

And - I am still uncertain if Ubuntu Linux is the Linux for me. I liked CGI and Perl many years ago and would like an installation fitting that purpose and photo work. I'm renting a virtual server on an Apache. I have much to relearn and freshen up. My job twisted me from what I liked and job for me became more  telling others to do jobs (ok better paid:P ). I wonder if there is an Apach/Linux version that can be used also by my wife. We are soon pensioners.

A  clean sort of Ubuntu without the tingle-tangle and super-bottoms, that is. 

It works fine, booting and all now!
The distance to a another Linux is just a CD away!

With all my respect


FIAT LUX!©

Gutta

---

### Post by Gutta Perka on 2011-10-26
REV: OT! But some may think it's usable! <===REV while "In Topic"! 

IN TOPIC!

Eureka!

I think I have found the error!

I have just installed a new environment (shell?) for Ubuntu.
Same problems as before.....

My conclusion is that - automaticly installing a new starting splash-screen for Ubuntu is destroying settings in grub4dos or any other things in booting procedure like changing UUID.....?

If that's the case - it must be an issue made by programmers building certain shells? (environments).

When this issue is cleared I will build another environment for local-hosts, Perl and studying Linux.
A spartan one. The goal is to be able to chose between these environments.

The one I now working with is for fun, every day use and for my wife - this one:
[ http://www.howtogeek.com/55985/how-to-make-ubuntu-linux-look-like-windows-7/   ]("http://www.howtogeek.com/55985/how-to-make-ubuntu-linux-look-like-windows-7/"):D:D


Look at the wallpaper - win7 wallpaper , Ubuntu crushing it.
(Perhaps an eye-raiser for children and friends, using win7 and XP only...)
However there are some thoughts about it - a primitive "windower" will be able to use Ubuntu!:lolflag:

I think the professional way for dual Ubuntu environment is to make a new partition and let grub4dos etc.
make me/my wife chose the appropriate one? In that way I don't have to bother destroying anything in the "other" environment.... 

Now back to fix the destroyed booting procedure. Interesting - I use the same  boot-procedure on USB2 - and there it works....

With all my respect

FIAT LUX! (c)

Gutta


#EDIT!==============

While nothing (I think) could modify "module" that brute I just did:

sudo update-initramfs -u
sudo update-grub


UUID etc was the the same as before - copied over the VMLINUZ...and initrmfs...to XP root.
No changes to boot.ini and menu.lst necessary!
Then prfectly OK booting on USB3.

That is - I think something is happening in "initramfs" on Ubunto on Iomega!
Does grub4dos use initrmfs in Iomega/Ubuntu?

#END EDIT=========================

---

### Post by kiyop on 2011-10-26
I cannot understand what you did caused the problem, but the problem may be related to:
> **kiyop said:**
> There are another problems in your situation.
One big problem is that you cannot use a newer kernel even after the newer kernel is installed in future.
You should manually generate the initramfs for the newer kernel and copy the newer kernel and the initramfs into Windows XP c drive and edit c:\menu.lst, if you want to use the newer kernel.
There is one way to automatically use the newer kernel; my tool, [kiyoshi's help]("http://kiyoandkei.blog68.fc2.com/blog-entry-52.html"). It can even boot another linux using one of the following kernel loader; Grub2, Grub legacy, grub4dos, lilo, syslinux, extlinux, isolinux.
But, I do not recommend you to use kiyoshi's help. It needs much knowledge to utilize it.

I guess that now your computer is booting like the following (although I partly forgot what you have done in this long thread):
Step 1) 
MBR in internal HDD -> PBR of /dev/sda1 (internal HDD first partition = Windows XP c drivce) -> ntldr - \boot.ini
Step 2-A)
Choice "Windows" -> NTDETECT.COM and so on (I am not sure) -> Windows XP.
Step 2-B)
Choice "grub4dos" -> \grldr -> searching /menu.lst -> c:\menu.lst
-> Choice "Iomega on USB3" -> /vmlinuz-2.6.38-8-generic in c:\ (/dev/sda1) and /initrd.img-2.6.38-8-generic in c:\ -> kernel tries to find partition with UUID=1f66e765-7888-49d5-aa82-bdb82263ab63

With kiyoshi's help, the above (from Step 2-B) can be changed to:
Step 2-B)
Choice "grub4dos" -> \grldr -> searching /menu.lst -> c:\menu.lst 
-> Choice "kiyoshi's help" -> /vmlinuz-2.6.38-8-generic in c:\ (/dev/sda1) and /initrd.img-kiyoCs (with kiyoshi's help) in c:\ 
-> kiyoshi's help wait for your pressing "ENTER" key 
-> your pressing "ENTER" key 
-> kiyoshi's help searches for all the partitions recognized and list the partitions. 
-> your selecting a partition
-> kiyoshi's help tries to mount the selected partition and ask you which you want; find "configuration files" or "manually boot"
Step 3-A)
-> Select "find configuration files"
-> kiyoshi's help find the configuration files such as /boot/grub/grub.cfg for Grub2 and so on, and list the menu entries found
-> Select one of the found menu entries
-> kiyoshi's help ask if you want to change the contents of boot configuration
-> you can edit or boot
->** Thanks to Great Tool "kexec"**, kiyoshi's help overwrite the kernel to be booted onto the kernel (in RAM) in use with the initramfs specified
-> If success, linux kernel and initramfs to be loaded is loaded and started.
Step 3-B)
-> Select "manual"
-> You can use shell like sh and can use kexec.
Your grldr in Windows XP system drive uses menu.lst in Windows XP system drive. The menu.lst uses vmlinuz-... and initrd.img-... in Windows XP system drive, not the original ones in Ubuntu / partition in Iomega.
Not only kernel (vmlinuz-...) but also initramfs (initrd.img-...) should be copied into Windows XP system partition from the Ubuntu / partition when they are changed.

With kiyoshi's help utilizing kexec, you need not copy them.

If you want to understand more, please search "kexec" with Google and analyze my init script: 
[http://blog-imgs-47.fc2.com/k/i/y/kiyoandkei/init110904.txt](http://blog-imgs-47.fc2.com/k/i/y/kiyoandkei/init110904.txt)

---

### Post by Gutta Perka on 2011-10-27
OT!


> 
If you want to understand more, please search "kexec" with Google and analyze my init script: 
[http://blog-imgs-47.fc2.com/k/i/y/ki...init110904.txt]("http://blog-imgs-47.fc2.com/k/i/y/kiyoandkei/init110904.txt")
YES - I want to understand more. I left Perling, under three years my job during beginning of 1990. The old Camel you know! Must say though - Internet was not mature, as nowadays. Writing progs those days was often in a team. One person was specialist on the OS and sh-scripts, one or two writing main program and one "art-designer" telling how it should look like and the customer of cause telling us what he/her wanted. (Sometimes we managed!:)) 
I sat in the middle as Perler, main programmer that is. Together we worked - everyone specialists in his/hers "area". 
Nowadays I think that the two first functions mentioned are one and the same. Information that is required is found on Linux/Perl forums.

By the way - Perl might be outdated and set aside by Java Scripts and even pure Java??
Whatever - they can't have the beauty to express all you wanted in one rather short line like in Perl!
(As it's for fun and recreation I'll will not abandon Perl)  In the "Camel-pages" I see that they even discuss new releases...   

As said - Now it's fore pure fun and recreation. Now I must relearn AND learn. To be honest just learn is the most appropriate word. 

When I read your shell shell-script starting with (shebang ??) "#!/bin/sh" my hart went soft.
My old now outdated programs always started with "#!/usr/bin/perl" - also  scripts.
Looked almost the same!
Yes I studied your script and think if you gave me a total one week free we could have discussed that script into particles.

This I loved (shows who you are!)
> 
.
.
export panic= . /conf/initramfs.conf
.
.
:P


I'm just now sitting on Iomega USB2!

With Linuxmint! ## For the moment that is!

I love it, It's what I wanted but it has a very tiny community.

There is also an Debianmint - but I don't like the thought. Squeezing another shell on Debian feels as me going church dressed with another mans clothes.  Might be wrong there?
Kiyop - what's you meaning there?

LinuxMint has , so far and for me, the nicest bidirectional interface man to OS.
Soft and not pushing. Clean and spartan. Still with the V12-motor there under the hood - if you understand what I mean?

Anyhow - this might be the choice as it was like love at first glance!

Kiyop - feel free to, if you want, to direct/warn me here.

(For me now Ub...u is like a Mic...soft Linux!):P Hmmm...Sorry there!!!:biggrin:

Anyhow - Linux is Linux, as tee comes in different tastes.
(As I understand now, ranting around in different tastes!)

When I have chosen what Linux - I'll try your USB3-solution in that very Linux.
Alone at first of cause. Now I know a bit better!


With all my respect Kiyop

FIAT LUX!(c)
/Gutta

Rev: Sorry for spelling your very name wrong. That' bad respect. Again sorry. Here I changed to the right one!!

Added:

You wrote:

> Your grldr in Windows XP system drive uses menu.lst in Windows XP system  drive. The menu.lst uses vmlinuz-... and initrd.img-... in Windows XP  system drive, not the original ones in Ubuntu / partition in Iomega.
Not only kernel (vmlinuz-...) but also initramfs (initrd.img-...) should  be copied into Windows XP system partition from the Ubuntu / partition  when they are changed.

Yes! Thats why Linuxmint directly could boot on USB3.

/Gutta

---

### Post by Gutta Perka on 2011-11-03
Hallo kiyop.

Now after trying Ubuntu, Linux mint and Debian (Live Debian on Usb) I decided for the last one, Debian.

That is I wiped Ubuntu away from Iomega hdd and did an netinstall of Debian on clean Ubuntu partitions
.
The last thing I was asked in that installation was if I wanted to have a "grub" install on the main hdd. I answered no - I thought I had a working one, "the #32 one"  that you directed me to and was working.

It didn't work!:oops:

Booting through computer BIOS on USB2 does neither work.

Grub on Windows seems OK but end with (initramfs) promt not finding Debian.
BIOS boot end with error: 
> file not found.
grub>


That is - I cannot boot Debian at all - Debian seems to have _no_ "normal" boot-sector at all.

Resque tools of mine:
Debian Live USB and Windows XP 

I think repairing the Debian boot sector is one solution - and then using the "old USB3 boot" from Windows.

How to?

With all my respect

/Gutta

---

### Post by kiyop on 2011-11-03
> **Gutta Perka said:**
> The last thing I was asked in that installation was if I wanted to have a "grub" install on the main hdd. I answered no - I thought I had a working one, "the #32 one"  that you directed me to and was working.

It didn't work!:oops:

Booting through computer BIOS on USB2 does neither work.

Grub on Windows seems OK but end with (initramfs) promt not finding Debian.
BIOS boot end with error: 

That is - I cannot boot Debian at all - Debian seems to have _no_ "normal" boot-sector at all.
If you started debian installer and do not install Grub2 nor LILO on MBR or PBR, it is very natural that you cannot boot debian before you configure boot loader correctly.

There are many ways to boot debian installed on Iomega.
I have written in this thread many hints.
You may be able to find the solution  by yourself.

I think that #32 is for enabling boot of Ubuntu from USB 3.0 port (by using Ubuntu and/or Debian), although I forget the detail of #32.
Do not misunderstand.

And if you want to ask about debian, please post at debian forum:
[http://forums.debian.net/](http://forums.debian.net/)
I also answer at debian forum.
[http://forums.debian.net/memberlist.php?mode=viewprofile&u=39793](http://forums.debian.net/memberlist.php?mode=viewprofile&u=39793)

Please be noticed that I will not answer to the question just about debian (which does not relate to Ubuntu) in this forum (Ubuntu forum) from now in this thread.

---

### Post by Gutta Perka on 2011-11-03
Sorry!

Thanks for answering me here.

I am already registered at the Debian forum - however I can't log in there.
I e-mailed the administrator for looking into that issue - no answer so far..

Perhaps it's because my name is a two-parted?
I'll try to just use one nick.

To You out there, sorry, this is just a a little transferdetail. 

Best regards
/Gutta

---

### Post by kiyop on 2011-11-05
To everybody who cannot boot Ubuntu installed in an external media connected to USB 3.0 port,

Please read [#16]("http://ubuntuforums.org/showthread.php?p=10472525#post10472525") - [#28]("http://ubuntuforums.org/showthread.php?p=11100306#post11100306") in this thread.
[#32]("http://ubuntuforums.org/showthread.php?p=11332900#post11332900") may also be helpful, in the case Windows XP is installed in the internal HDD.

---

### Post by Tone303 on 2012-01-23
This 10 page thread with loads of code and commands has a two-sentence answer:

***USB 3.0 Cards which add USB3 to your computer are not bootable devices. The makers simply did not think to make them communicate with motherboard bios to be bootable.*** 

Which makes them worthless , not worth the money, who would want to buy a 30 dollar USB 3 card only to transfer files and not be able to boot systems at near-slow-SSD speed? Youd want BOTH !! Bootable too !!

very stupid manufacturers, very stupid. If they were smart they would make it bootable, then advertise that their cards / chipsets are bootable. that would be smart advertising to get more sales. just....dumb.

A USB card must be firmware programmed to declare itself to the motherboard as bootable, 10 pages of code wont fix this.

---

### Post by xyzzyman on 2012-01-23
> **Tone303 said:**
> This 10 page thread with loads of code and commands has a two-sentence answer:

***USB 3.0 Cards which add USB3 to your computer are not bootable devices. The makers simply did not think to make them communicate with motherboard bios to be bootable.*** 

Which makes them worthless , not worth the money, who would want to buy a 30 dollar USB 3 card only to transfer files and not be able to boot systems at near-slow-SSD speed? Youd want BOTH !! Bootable too !!

very stupid manufacturers, very stupid. If they were smart they would make it bootable, then advertise that their cards / chipsets are bootable. that would be smart advertising to get more sales. just....dumb.

A USB card must be firmware programmed to declare itself to the motherboard as bootable, 10 pages of code wont fix this.

It's actually a BIOS issue w/ExpressCard slots. Most systems can't boot with ExpressCard CompactFlash adapters even. There are some chipsets that won't work as bootable with any BIOS, but even with eSATA ExpressCard adapters w/ Jmicron 36x chips in them if the BIOS doesn't recognize it as bootable it won't work.

---

### Post by Gutta Perka on 2012-01-23
> **Tone303 said:**
> This 10 page thread with loads of code and commands has a two-sentence answer:

***USB 3.0 Cards which add USB3 to your computer are not bootable devices. The makers simply did not think to make them communicate with motherboard bios to be bootable.*** 

Which makes them worthless , not worth the money, who would want to buy a 30 dollar USB 3 card only to transfer files and not be able to boot systems at near-slow-SSD speed? Youd want BOTH !! Bootable too !!

very stupid manufacturers, very stupid. If they were smart they would make it bootable, then advertise that their cards / chipsets are bootable. that would be smart advertising to get more sales. just....dumb.

A USB card must be firmware programmed to declare itself to the motherboard as bootable, 10 pages of code wont fix this.

Hey there!

**This thread is THE workaround of that issue!**

I'm sitting here with Ubuntu booted from a USB3 expresscard.

HD-Speed is about three times 3-4 times faster than the internal IDE-HD.

You can boot from USB3-expresscard but you have to read this thread first.
When that's done it is as natural as any other booting.:D

---

### Post by kiyop on 2012-01-23
Thanks Gutta Perka, for your nice comments. :smile:

To Tone303 [s]and xyzzyman[/s];
(LINE-THROUGH at 2012/1/23 22:40 at JAPAN)

> **Tone303 said:**
> This 10 page thread with loads of code and commands has a two-sentence answer:

***USB 3.0 Cards which add USB3 to your computer are not bootable devices. The makers simply did not think to make them communicate with motherboard bios to be bootable.*** 

Which makes them worthless , not worth the money, who would want to buy a 30 dollar USB 3 card only to transfer files and not be able to boot systems at near-slow-SSD speed? Youd want BOTH !! Bootable too !!

very stupid manufacturers, very stupid. If they were smart they would make it bootable, then advertise that their cards / chipsets are bootable. that would be smart advertising to get more sales. just....dumb.

A USB card must be firmware programmed to declare itself to the motherboard as bootable, 10 pages of code wont fix this.
[s]> **xyzzyman said:**
> It's actually a BIOS issue w/ExpressCard slots. Most systems can't boot with ExpressCard CompactFlash adapters even. There are some chipsets that won't work as bootable with any BIOS, but even with eSATA ExpressCard adapters w/ Jmicron 36x chips in them if the BIOS doesn't recognize it as bootable it won't work.[/s]
First, boot any kind of Ubuntu (Live CD, Live USB or the one installed in inetrnal hdd or so) on the computer which the USB 3.0 card is connected to, and connect your USB3.0 HDD (or some media)  to the port of the USB3.0 card and check if you can mount the partition in the USB3.0 HDD or not.
If it can be mounted, there is possibility that you can boot the ubuntu installed in the USB3.0 HDD connected to the USB 3.0 card.

I have been booting debian and ubuntu installed in partitions in a USB3.0 HDD connected to USB 3.0 port since last February (for about one year). On the configuration (set-up) menu of BIOS of the connected PC, USB 3.0 card and the USB 3.0 HDD connected to the USB 3.0 card are not shown. Of course, the bios cannot boot from the USB3.0 HDD connected to the USB 3.0 card. But I can boot the debian and ubuntu installed in the USB3.0 HDD connected to the USB 3.0 card by using the kernel and initramfs on an internal HDD which can be booted from bios via a kernel-loader.

If you cannot understand how to boot by yourselves, please write concretely the problematic situations of yours.
I am willing to support you.

And again,
> **kiyop said:**
> To everybody who cannot boot Ubuntu installed in an external media connected to USB 3.0 port,

Please read [#16]("http://ubuntuforums.org/showthread.php?p=10472525#post10472525") - [#28]("http://ubuntuforums.org/showthread.php?p=11100306#post11100306") in this thread.
[#32]("http://ubuntuforums.org/showthread.php?p=11332900#post11332900") may also be helpful, in the case Windows XP is installed in the internal HDD.

---

### Post by xyzzyman on 2012-01-23
I understand that. I was just commenting to Tone33 (his rant was at the card makers) that it's not a problem with the ExpressCard USB 3.0 adapters insomuch of themselves as it's the BIOS itself not recognizing it, hence why you can't boot from them and have to chainload it from another drive that's been booted... Some BIOS have been updated but most haven't and probably won't. So I don't know why you directed that comment at me...

---

### Post by kiyop on 2012-01-23
> **xyzzyman said:**
> I understand that. I was just commenting to Tone33 that it's not a problem with the ExpressCard USB 3.0 adapters insomuch of themselves as it's the BIOS itself not recognizing it, hence why you can't boot from them and have to chainload it from another drive that's been booted... Some BIOS have been updated but most haven't and probably won't. So I don't know why you directed that comment at me...
I see. Excuse me! :oops:

---

### Post by Gutta Perka on 2013-03-01
Now on UBUNTU 12.04 LTS - AND HAVE HAD MANY PROBLEMS IN UBUNTU in installing and configuring, updating etc.

Now after a year of problems I found an error depending in the booting of the IOMEGA. ( I'm happy now - just trying to find a solution!)

MENU.LST on the old hdd says:


> color blue/green yellow/red white/magenta white/magenta
timeout 30
default /default

title find and load NTLDR of Windows NT/2K/XP
fallback 1
find --set-root --ignore-floppies /ntldr
chainloader /ntldr
savedefault --wait=2

title Ubuntu on Iomega
kernel /vmlinuz-3.0.0-15-generic root=UUID=383ddb4e-bcf1-4b7e-a09f-cab28dc12ce4 ro quiet splash rootdelay=8
initrd /initrd.img-3.0.0-15-generic

See that "xxxx-3.0.0-15-generic"!

It made grub to direct vmlinuz and initrd.img to follow up any new version of UBUNTU and telling UBUNTU what headers etc to use.

I tried to use virtualbox to handle my windowsprinters, -scanners etc within UBUNTU - but no way!

A bad solution is:

In UBUNTU do:
ls -l /boot

Just now after taking a ghost of ubuntu i'll try:
Picking up the last version of vmlinuz-xxxx and then put those xxxx into menu.lst on orginal old hd for booting up the IOMEGA.

EDIT: Did not work! /Gutta

-----
EDIT #2: Post 87 say: "
Not only kernel (vmlinuz-...) but also initramfs (initrd.img-...) should  be copied into Windows XP system partition from the Ubuntu / partition  when they are changed."

- That helped but makes updating UBUNTU rather a big process! (Never update UBUNTU is a solution - that is!)

-----------
EDIT #3:
Yes I know - its time to buy a new computer and not sneaking around....[IMG]http://ubuntuforums.org/images/smilies/icon_razz.gif[/IMG]
However then I'll miss the sport....
-----------

/Gutta P

---

### Post by kiyop on 2013-04-06
> **Gutta Perka said:**
> 
EDIT #2: Post 87 say: "
Not only kernel (vmlinuz-...) but also initramfs (initrd.img-...) should  be copied into Windows XP system partition from the Ubuntu / partition  when they are changed."

- That helped but makes updating UBUNTU rather a big process! (Never update UBUNTU is a solution - that is!)
You should manually copy the new kernel (vmlinuz-***) and initramfs (initrd.img-***) in /boot directory to the partition where BIOS can recognize and deal the files in and you should manually configure boot loader configuration file such as /menu.lst.

If you can use my tool (kiyoshi's help), you need not do the above thing.
How to make my tool is written at [http://kiyoandkei.blog68.fc2.com/blog-entry-52.html](http://kiyoandkei.blog68.fc2.com/blog-entry-52.html)

> **Gutta Perka said:**
> 
EDIT #3:
Yes I know - its time to buy a new computer and not sneaking around....:razz:
However then I'll miss the sport....


And I got the following message of yours:
[QUOTE=Gutta Perka]Best kiyop...
...how are You, well I hope.

Remember Gutta Perka?

I'm waiting for my new laptop to arrive.
Can this voodoo be done with grub-ESI (?) on a GPT/UESI -Win8/Win7 system.

:P !!!! Your splendid solution has now served me for almost two years! WOW! Eloge!!!

That's all! (He He He...)

Stiil with all my respect for You
Gutta Perka
Sweden[/QUOTE]
I am not sure what you mean by the above message, but I guess you want to ask if this method can work well with grub-e[color=red]f[/color]i on a GPT/UE[color=red]F[/color]I -Win8/Win7 system or not.
Unfortunately, I have no PC with UEFI. So, I cannot try this method on PC with UEFI.

---

### Post by Gutta Perka on 2013-04-07
Nice seeing You are fine!

Reading this:
[http://www.rodsbooks.com/efi-bootloaders/grub2.html](http://www.rodsbooks.com/efi-bootloaders/grub2.html)
-it seems as it is possible and I can try that myself.

Reading on the Internet - it seems as the problem is that UEFI-standard is not holy - that is today, many PC:s have their own way of implementing UEFI.

I'l give it a try when my laptop arrives.

Regards
Gutta Perka

---

### Post by kiyop on 2013-04-13
I am interested in grub2 on UEFI system. I am looking forward to your report. :)

---

