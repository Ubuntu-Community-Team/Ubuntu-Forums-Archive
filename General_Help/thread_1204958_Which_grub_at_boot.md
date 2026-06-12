---
title: "Which grub at boot?"
date: 2009-07-05
forum: General Help
---

### Post by oblivion62 on 2009-07-05
In my continuing attempts to experiment with things, I installed Mandriva on a second hard disk in my ubuntu box.

Its grub has taken over. Despite me removing the boot flag from the second hd and reinstalling grub on hd0,0 following the pages in help I found when searching for grub and finding a "fix boot problems" page, I still get the Mandriva-flavour grub complete with its version of menu.lst. I wouldn't mind, but Mandriva stopped working and I want the drive back, but I don't dare until I've got boot back under the ubuntu version of grub! Oh, Hardy, sorry.

I'm clearly missing something obvious. Can anyone suggest what, please?

--tim

---

### Post by blueridgedog on 2009-07-05
If you boot off of a LiveCD, do you still have your original /boot/grub/menu.lst on the hard drive or has the other install altered it?

While on the LiveCD, can you post the output of:

```
fdisk -l 
```

and 

```
mount
```

If your Ubuntu disk still has a correct menu.lst, we should be able to reinstall grub, this time pointing it at your prior hard drive as the root.

---

### Post by oblivion62 on 2009-07-05
> **blueridgedog said:**
> If you boot off of a LiveCD, do you still have your original /boot/grub/menu.lst on the hard drive or has the other install altered it?

Thanks for this. I fear I may not have explained things either clearly or completely.

I have a /boot/grub/menu.lst on both hard drives. They're different. The one on the ubuntu drive (hd0) looks exactly as it should, I think, with no sign of Mandriva. The one on hd1 contains Mandriva stuff AND a line for ubuntu 8.10 (which was the version I was running when I installed Mandriva). I made that line the default. If I execute the Mandriva lines, the system fails and reboots. The ubuntu line works but loads the current version.

> **blueridgedog said:**
> While on the LiveCD, can you post the output of:

```
fdisk -l 
```

and 

```
mount
```



I don't have a LiveCD handy, but I can probably make one in the not-too-distant. However, using the current version of ubuntu, loaded from the ubuntu 8.10 line (that nevertheless loads 9.04 -- sorry, I said Hardy earlier and didn't mean it!) in the active grub, I get no output from the fdisk -l command and the following from mount:

```
mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-13-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/tim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tim)

```

> **blueridgedog said:**
> 
If your Ubuntu disk still has a correct menu.lst, we should be able to reinstall grub, this time pointing it at your prior hard drive as the root.

I thought I'd done that earlier: I used

```

grub> setup (hd0,0)

```

as the inline help suggested, but I'm still getting the wrong menu.lst being read and the graphical Mandriva thing.

Logically, that suggests to me that I'm wrong in thinking it's (hd0,0) but the executed menu.lst looks like this:

```
timeout 10
color black/cyan yellow/cyan
gfxmenu (hd1,0)/boot/gfxmenu
default 3

title linux
kernel (hd1,0)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=bb793bff-3e8a-445b-bffc-d2e5cc611b5e resume=UUID=6b56e405-0046-4dad-909a-d5cfe63c1859 splash=silent vga=788
initrd (hd1,0)/boot/initrd.img

title linux-nonfb
kernel (hd1,0)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=bb793bff-3e8a-445b-bffc-d2e5cc611b5e resume=UUID=6b56e405-0046-4dad-909a-d5cfe63c1859
initrd (hd1,0)/boot/initrd.img

title failsafe
kernel (hd1,0)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=bb793bff-3e8a-445b-bffc-d2e5cc611b5e failsafe
initrd (hd1,0)/boot/initrd.img

title Ubuntu 8.10
root (hd0,0)
configfile /boot/grub/menu.lst

title 2.6.27-desktop586rc8-2mnb
kernel (hd1,0)/boot/vmlinuz-2.6.27-desktop586-0.rc8.2mnb BOOT_IMAGE=2.6.27-desktop586rc8-2mnb root=UUID=bb793bff-3e8a-445b-bffc-d2e5cc611b5e resume=UUID=6b56e405-0046-4dad-909a-d5cfe63c1859 splash=silent vga=788
initrd (hd1,0)/boot/initrd-2.6.27-desktop586-0.rc8.2mnb.img

title desktop586 2.6.27.14-1mnb
kernel (hd1,0)/boot/vmlinuz-2.6.27.14-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.14-1mnb root=UUID=bb793bff-3e8a-445b-bffc-d2e5cc611b5e resume=UUID=6b56e405-0046-4dad-909a-d5cfe63c1859 splash=silent vga=788
initrd (hd1,0)/boot/initrd-2.6.27.14-desktop586-1mnb.img

title desktop586 2.6.27.19-1mnb
kernel (hd1,0)/boot/vmlinuz-2.6.27.19-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.19-1mnb root=UUID=bb793bff-3e8a-445b-bffc-d2e5cc611b5e resume=UUID=6b56e405-0046-4dad-909a-d5cfe63c1859 splash=silent vga=788
initrd (hd1,0)/boot/initrd-2.6.27.19-desktop586-1mnb.img

```

And all its non-ubuntu references are to hd1,0...

Which is weird. Or it seems like it to me. But I don't speak fluent linux, as you can probably tell. ;)

--tim

---

### Post by blueridgedog on 2009-07-05
Can you post the output of 

```
sudo fdisk -l
``` 

We need to see which really is hd0 and which is hd1.  Also, you will need to use the root command with the grub setup, but again we need to nail down which is which drive.

Just from what you posted, it appears that Ubuntu is on hd1, and the root partition is hd1,0 (in grub speak).  

So, going on that alone, I would try:

```
sudo grub
root hd1,0
setup hd0
quit
```

That will put the grub boot loader into the mbr of the fist hard drive, telling it to boot off of the second.  

If you think your bios is set to boot off of the second (new bios's can boot off of any drive) then you can setup the second hard drive.

---

### Post by oblivion62 on 2009-07-06
> **blueridgedog said:**
> Can you post the output of 

```
sudo fdisk -l
``` 


First and foremost: thanks for all this!

Aha. I should've realised.

And I didn't sudo grub last time either.

Output is:

```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcdf0cdf0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9349    75095811   83  Linux
/dev/sda2            9350        9726     3028252+   5  Extended
/dev/sda5            9350        9726     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 30.0 GB, 30060527616 bytes
255 heads, 63 sectors/track, 3654 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01d201d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3654    29350723+  83  Linux


```
> **blueridgedog said:**
> We need to see which really is hd0 and which is hd1.  


I'd first installed ubuntu to the 80Gb drive and, rather later, given Mandriva the 30Gb. This led me to assume that grub and ubuntu were initially sharing a drive, and a new grub on the 30Gb drive had moved in and taken precedence somehow. Is that borne out by the above?

--tim

---

### Post by blueridgedog on 2009-07-06
It seems clear that Ubuntu was/is on sda1/hd0,0 and assuming the /boot/grub on sda1 is still intact, you can try:

sudo grub
root hd0,0
setup hd0
quit

---

### Post by oblivion62 on 2009-07-06
> **blueridgedog said:**
> It seems clear that Ubuntu was/is on sda1/hd0,0 and assuming the /boot/grub on sda1 is still intact, you can try:

sudo grub
root (hd0,0)
setup (hd0)
quit

You star. :-)

Sorted. So now I can find a new use for a 30Gb drive with a broken Mandriva on it. Like, maybe, something a bit less likely to cause chaos and confusion. All my mp3s, perhaps. :-)

Thanks again!

---

### Post by blueridgedog on 2009-07-06
If all your mp3's fit on a 30 gig disk, then you need to buy more music!  I am glad your system is working.

---

### Post by hibliss on 2009-07-06
> **blueridgedog said:**
> If all your mp3's fit on a 30 gig disk, then you need to buy more music!  I am glad your system is working.

If you bought 30gb worth of MP3s at $1/song, with the average MP3 coming in at or below 5mb, you are looking at around $6000 worth of music on that hard drive.

At the OP, why don't you try installing Mandriva, or OpenSuse, or another distro that you want to test in VirtualBox inside your current Ubuntu install to test?

---

### Post by blueridgedog on 2009-07-06
> **hibliss said:**
> If you bought 30gb worth of MP3s at $1/song, with the average MP3 coming in at or below 5mb, you are looking at around $6000 worth of music on that hard drive.


Ouch.  I ripped my CD collection years ago, and haven't looked back.  The only think I have bought "audio" wise in the last decade have been a pile of audio books.

You could use that drive as a dedicated /home partition...

---

