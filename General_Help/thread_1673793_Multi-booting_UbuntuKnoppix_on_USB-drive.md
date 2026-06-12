---
title: "Multi-booting Ubuntu/Knoppix on USB-drive"
date: 2011-01-22
forum: General Help
---

### Post by chah on 2011-01-22
I'm trying to create an 8GB USB drive that has Knoppix on /dev/sdb1 and Ubuntu10.10 on /dev/sdb2, dual booting with Grub 0.97 (I don't know Grub 2 that well, but if someone can give me a push here, I'd like to give it a try).

I partitioned the device into 6GB for /dev/sdb1, and the leftover for /dev/sdb2 as I have the DVD version for Knoppix. I download/install Ubuntu using Unetbootin, and now have an image of 10.10 on my HDD. My intention is to boot both OS's in Live CD mode, possibly with a tiny bit of persistent storage squeezed in there.

I setup /dev/sdb1 first by copying the contents of /KNOPPIX and /boot into /dev/sdb1, then installing grub with the grub-install command. I created menu.lst by copying kernel options from the isolinux.cfg file. The Knoppix grub stanza looks like this:

```

title Knoppix
kernel /boot/isolinux/linux ramdisk_size=100000 lang=en vt.default_utf8=0 apm=power-off video=vga16fb:off initrd=minirt.gz nomce quiet loglevel=0 tz=localtime no3d noprompt
initrd /boot/isolinux/minirt.gz
boot

```

This works, and I can boot to Knoppix.

I understand Ubuntu less well than Knoppix. There seem to be several .cfg files in the CD for different boot options and I don't know which one to use. There are some booting parameters in /casper, I tried taking a few of those but couldn't get a successful boot following a parallel path for copying Ubuntu onto /dev/sdb2. 

So I tried using Unetbootin to create a bootable USB key. This worked for me in the past when I live installed to /dev/sda1 on a USB drive. However this time when I chose /dev/sdb2 (on a USB drive) as the partition, and let it overwrite GRUB to the MBR, I didn't end up with a bootable USB drive which was strange. The boot process hung at the initial GRUB prompt. Another strangeness I encountered was I couldn't overwrite the MBR with grub-install from Knoppix as I was able to before. (GRUB 0.97 under Knoppix). However I zero'd out bytes 0-446 of sector 0 on the USB, then I went to grub prompt (instead of using grub-install), and was able to reset the MBR using the grub command setup(hd2). 

On a different machine, I was successful in getting Knoppix/Ubuntu dual booting, both in Live-CD mode from the hard drive by copying the boot options that Unetbootin gave me. The Ubuntu stanza there looks like this:
```

title Ubuntu_10.4
root (hd0,1)
kernel /ubnkern initrd=/ubninit file=/vdrom/preseed/ubuntu.seed boot=casper quiet splash persistent --
initrd /ubninit
boot

```
When I try to copy this method over to the USB drive, I run into the problem that I'm not certain which device the BIOS is going to assign to my USB drive, while I am always certain what is going to be assigned to an internal static HDD. On one machine, the USB drive might be (hd1) while on another machine it might be (hd2). This hits the limits of my Grub understanding and I haven't been able to find out how to get around this.

Can any resident Ubuntu/Grub expert advise on what I might try next, or how to set the root to partition 1 of "this device".

Thanks in advance

---

### Post by bryanl on 2011-01-23
What might be a bit easier is to boot the ISO. See [multiple boot from ISO on USB pen drive](http://tcl.leipper.org/2010/12/multiple-boot-from-iso-on-usb-pen-drive/) for an overview and links to Pendrivelinux and GeekDeck for details.

The idea is to use GRUB2 to mount the ISO as a loop and then feed it the necessary boot parameters.

This gets rather wild when you consider you've got a compressed read only file system inside an ISO that is a file on a USB stick - but it does seem to work. I've got several Ubuntu ISO's for both 64 and 32 bit versions booting well and Pendrive has the parameters for several utility ISO's. I can zsync the latest builds of Natty and then reboot to see what they do, for example. I can't see where Knoppix would be that much different (but then maybe I don't see so good ...! ;0 )

---

### Post by chah on 2011-01-23
Thanks for the link, that sounds great!

In fact I originally wanted to boot from the iso image directly but ended up thinking it would be too hard to figure out how to do.

Anyway now that I have instructions I'll give it a whirl.

Thanks again.

---

### Post by C.S.Cameron on 2011-01-23
There is a script to do  that:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

