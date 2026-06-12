---
title: "eject/unmount and external HD indicator lights"
date: 2011-05-26
forum: General Help
---

### Post by floydian_slip on 2011-05-26
Hi,

I just recently switched from Ubuntu to Xubuntu, and so far I'm quite happy, except there are a few differences with regard to unmounting a volume, e.g. external HD or USB.

(1) In Ubuntu, when right-clicking, I had the option to either "safely remove" (which I think just means "unmount") or to "eject" a volume.

(2) After safely removing it, the volume icon would disappear from my desktop and from my file manager (Nautilus).

(3) The indicator lights on my external HD and USB drive would turn off, indicating that it's safe to remove.

In Xubuntu, however, I have only the "eject" option, and after ejecting, the drive still shows up in my file manager (Thunar), and the indicator light never turns off. In fact, even when I do the following command:

```
sudo umount /media/xxxxx
```

the drive still shows up in Thunar, and the indicator light is still on, so it's not a difference between eject vs. unmount. Also, the drive is successfully unmounted because when I run

```
ls -a /media
```

I don't see the mount point anymore.

But what I'd really like is for my drive to disappear from the file manager/desktop, and for the indicator light to go off, that way I know for sure it's okay to unplug it. Is there any way I can have it do that??

Thanks!

---

### Post by gnawingonfoot on 2011-06-09
I'm bumping this thread because I also have questions regarding this matter, and I've had to reformat USB flash drives and my external hard drive several times because I keep screwing *something* up (FAT32 formatting on all), and then data gets lost.

When I unmount (or 'Eject') an external drive in **Xubuntu 11.04** (upgraded from 10.10), I only get the slightest flash of a notification (if any) from the notifier, even though I have the settings set to let all notifications sit for six seconds before disappearing.  Notifications for when I plug a drive in and it mounts automatically are just fine, though.

I've started using **Disk Utility 2.32.1** to actually make sure things get unmounted and that I'm not just getting error messages (which seems to happen a lot, even though I don't have programs/files/windows from the drive actually open).  I'm using a **Samsung G2 Portable** 320 gigabyte external hard drive.  After I click the "Unmount" in Disk Utility, I notice that the drive's light remains on and the inside parts are still spinning.  

From here, it appears unmounted in every way I look at it, and I can mount it up again just fine, but as I've had a lot of data loss lately, I'm a bit paranoid still about the spinning part (and the light being on).  Pressing the "Safe Removal" button in Disk Utility appears to work, but then Thunar automatically powers up (and mounts) the drive again.

For my flash drive, I'm using a **4G PNY Attache**, which I thought to be a pretty reliable product line, but it has been giving me the most problems.  It is also is formatted FAT32, and I pretty much only run **PortableAbiWord** from it when I'm on Windows 7 computers, and at home, I edit copies of the files that are on my computer's internal hard drive (so there are back-ups).  For the record, Windows often refuses to let my drive free after I've closed PortableAbiWord and states that the drive is busy.  This may be part of the problem, but I realize this isn't the place for help on that, but could this mean that the drive itself is flawed--is this even likely?  (The first university tech support lackey first thought to push the computer's power button to turn it off so I could remove the drive, so I have no faith in them.)  Using Disk Utility's "Safe Removal" button has the same effect of as it does on the portable hard drive.

Anyhow, I really just want the data loss to stop so I don't have to reformat any disk or flash drives anymore or lose any more of my typing progress.  I use FAT32 so I can work on my essays on campus (using PortableAbiWord run from the drive, as the university has an exclusive deal with Microsoft to allow only MSOffice on school computers, and going back-and-forth between MSWord and LibreOffice/AbiWord inevitably leads to file and formatting corruption--and GoogleDocs hasn't been consistent enough for me with longer essays).  I'm really at a loss here, and I'm not sure what exactly has been causing problems, but any help would be much appreciated!

---

### Post by moonport on 2011-07-26
> **floydian_slip said:**
> Hi,

I just recently switched from Ubuntu to Xubuntu, and so far I'm quite happy, except there are a few differences with regard to unmounting a volume, e.g. external HD or USB.

(1) In Ubuntu, when right-clicking, I had the option to either "safely remove" (which I think just means "unmount") or to "eject" a volume.

(2) After safely removing it, the volume icon would disappear from my desktop and from my file manager (Nautilus).

(3) The indicator lights on my external HD and USB drive would turn off, indicating that it's safe to remove.

In Xubuntu, however, I have only the "eject" option, and after ejecting, the drive still shows up in my file manager (Thunar), and the indicator light never turns off. In fact, even when I do the following command:

```
sudo umount /media/xxxxx
```

the drive still shows up in Thunar, and the indicator light is still on, so it's not a difference between eject vs. unmount. Also, the drive is successfully unmounted because when I run

```
ls -a /media
```

I don't see the mount point anymore.

But what I'd really like is for my drive to disappear from the file manager/desktop, and for the indicator light to go off, that way I know for sure it's okay to unplug it. Is there any way I can have it do that??

Thanks!

I've the same issue with my usb pendrive since I upgraded to Lucid Lynx.

---

### Post by Jack Brown on 2011-11-24
bump.

also for flash drive / mobile phone / card reader.

i tried SAFE REMOVAL using Disk Utility 3.0.2 from repos on xubuntu 11.10.

It does safely remove the drive and icons disappear from desktop, but then it gets automatically mounted after 3-5 seconds and icons reappear... (even if it was unmounted but visible before)

xubuntu's really nice.  and being able to use gtk programs is great!

thanks.

---

### Post by jthechemist on 2011-12-29
Bump again.

I'm using a fresh install of Xubuntu 11.10 (Oneiric), and I'm experiencing similar issues. When I click the 'eject' icon in Thunar next to a mounted USB HDD (or select 'eject' from the right-click options) I get a message informing me the drive cannot be unmounted, as there is data that is being/needs to be written to the disk (which there shouldn't be!). A quick peek in /media shows my drive has apparently been unmounted, though the drive still hums away. I haven't experienced any data loss, but if this keeps up, I am worried that might change.

Has anyone heard of any bugs being filed?

---

