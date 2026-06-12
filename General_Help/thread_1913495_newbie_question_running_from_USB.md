---
title: "newbie question running from USB"
date: 2012-01-22
forum: General Help
---

### Post by slo_hand2 on 2012-01-22
[B]My hard drive in my dell inspiron 1200 is not seen, I know the hard drive is good, but this laptop does not see it, so I am guessing I have some motherboard problems, it also does not see my DVD-Rom/cdrw, so I am using Ubuntu off of a USB drive.
With this in mind what diagnostics can be run that can tell me if/what motherboard problems I am having?
I know you will most likely say not worth the trouble, but I am just playing around with this laptop to see if I can get it operation once again, not as my primary device.
[/B]

---

### Post by Old_Grey_Wolf on 2012-01-22
Does Ubuntu see it? Enter this command in the terminal ```
sudo fdisk -l
```

Just for future reference, what version of Ubuntu do you have on the USB?

---

### Post by slo_hand2 on 2012-01-29
I am running it off a program called UNetboot in, and it is Ubuntu v.10.04. 3lts

when I type in your suggestion I see the following:

Disk /dev/sda:2055mb,2055019008 bytes
255 heads, 63 sectors/track, 249 cylinders
Units = cylinders of 106065 * 512 = 8225280 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device boot     start     end    Blocks           id   system
/dev/sdal             1       250   2006784        b     W95 fat32

Partition 1 has different physical/logical endings:
 phys+(248, 254, 63) logical=(249, 214, 29

It does not give any indication of drive C so I am assuming the above info is from the USB stick.

---

### Post by grahammechanical on 2012-01-29
Linux does not use terms like "drive C." That Microsoft talk.

sda = sata drive a = first (and in your case only) sata drive on the machine. A second drive would be sdb

sda1 - the first partition on sda. A second partition would be called sda2.

I am guessing, but this might mean something.

> Partition 1 has different physical/logical endings:
phys+(248, 254, 63) logical=(249, 214, 29

When you say

>  I know the hard drive is good, but this laptop does not see it,

do you mean that it is not recognised in the BIOS? And the same is true of the DVD/CD drive? Does the OS load?

Does Ubuntu see the DVD drive? Can it (on the USB stick) access the DVD drive? For example can you use Ubuntu to play an audio CD in that drive?

I am wondering if the fault is with the operating system and not with the physical components.

Do you need this OS? Is there data on it that you need? Think about installing Ubuntu. That will require a disk format that might solve this issue. I suggest this as something to keep in mind.

Regards.

---

### Post by slo_hand2 on 2012-01-29
The hard drive is not seen in the bios, neither is the dvd/cd player and no the O/S does not load, the hard drive has winxp on it.
SO your saying that the sda is referring to the harddrive and not the usb? that would be great!
sda = sata drive a = first (and in your case only) sata drive on the machine. A second drive would be sdb

sda1 - the first partition on sda. A second partition would be called sda2.

do you have any idea how to repair this?

Partition 1 has different physical/logical endings:
 phys+(248, 254, 63) logical=(249, 214, 29

when I go to install I get as far as the prepare partition screen , but it shows NOTHING in the box, when I click forward I get the following." No root file system defined" "Please correct this from the partition menu" where do I find the partition menu?
BTW thank you for spending your time helping a complete newbie to Linux, it is appreciated

---

### Post by slo_hand2 on 2012-01-29
**Ok** I found the partition under GParted it only shows the USB drive

here:

Partition   file system    mount point        size          used           unused       flags
/dev/sda1     fat32           /cdrom       1.91 GiB      709.07 Mib      1.22 Gib      Boot
with a key  


the hard drive is a 60GB hard drive

---

### Post by Old_Grey_Wolf on 2012-01-29
Since the hard drive is not showing up using the "sudo fdisk -l" command and not in the BIOS, you aren't going to be able to load an OS on it. 

Check the hard drive and CD/DVD connectors. 

It could be a failed controller chip on the motherboard since that laptop is 5 to 7 years old, and it was an inexpensive laptop to begin with.

---

### Post by slo_hand2 on 2012-01-29
True an inexpensive laptop, and maybe not worth the time or money to fix it, but it's fun to try anyway, as you say it is most likely the motherboard, which would not make it work fixing, ( Yes I have replaced motherboards before, but would not be worth it for such and obsolete laptop. I thought perhaps linux Ubuntu could or would have a diagnostic tool to seek out the problem.
 Thanks for the help guys you were Great!

One last question about ubuntu, can I run this from the usb stick and have complete control like if it was installed on the hard drive? if so can you tell me how to get my Belkin wireless adapter to install?

---

### Post by Old_Grey_Wolf on 2012-01-29
> **slo_hand2 said:**
> ...I thought perhaps linux Ubuntu could or would have a diagnostic tool to seek out the problem...

Usually the manufacturer of the computer or hardware device provides the diagnostic tools for troubleshooting their hardware. Many of them don't provide any tools.

> One last question about ubuntu, can I run this from the usb stick and have complete control like if it was installed on the hard drive? if so can you tell me how to get my Belkin wireless adapter to install?

If you have a larger USB, I use a 16GB, you can do a full install of Ubuntu on it just like a hard drive. 

You would need your 2GB USB drive you already have and a second larger USB drive. Then install Ubuntu to the second USB dirve just like you would to a hard drive. Then Google for the Belkin wireless adapter driver install instructions as you would with a normal hard disk install. Installing a wireless driver is usually just having a wired Ethernet connection and loading the driver by going to Hardware Drivers in the Administration menu.

---

### Post by slo_hand2 on 2012-01-29
**Thank You again **you guys have been a big help and it is appreciated! I will I'm sure have other questions in the future, I would like to learn more about Linux!:popcorn::popcorn:

---

### Post by slo_hand2 on 2012-02-02
> **Old_Gray_Wolf said:**
> Usually the manufacturer of the computer or hardware device provides the diagnostic tools for troubleshooting their hardware. Many of them don't provide any tools.



If you have a larger USB, I use a 16GB, you can do a full install of Ubuntu on it just like a hard drive. 

You would need your 2GB USB drive you already have and a second larger USB drive. Then install Ubuntu to the second USB dirve just like you would to a hard drive. Then Google for the Belkin wireless adapter driver install instructions as you would with a normal hard disk install. Installing a wireless driver is usually just having a wired Ethernet connection and loading the drive by going to Hardware Drivers in the Administration menu.

I don't seem to be able to install the O/S onto a 8GB usb drive form the install, does the 8GB need to be prepped like in windows in order to make it bootable? If so how is this done in linux?

---

### Post by Old_Grey_Wolf on 2012-02-02
> **slo_hand2 said:**
> I don't seem to be able to install the O/S onto a 8GB usb drive form the install, does the 8GB need to be prepped like in windows in order to make it bootable? If so how is this done in linux?

I installed Ubuntu 10.04 LTS directly to an 8GB USB. 

I had a working hard disk in my laptop; therefore, I removed it so I wouldn't harm it, just in case I did something wrong.

Then I booted from the 2GB Live USB (sda) to get to the installer. 

I chose the 16GB USB (sdb) as the target device for the installation.

It was a new 16GB USB so it was probably formatted as FAT32.

Hope this helps.

---

### Post by slo_hand2 on 2012-02-03
**Hmm did just as you did and the *8GB is formatted to Fat32 so i am at a loss, unless it's the laptop causing the problem?**

---

### Post by Old_Grey_Wolf on 2012-02-03
You could install on the 8GB USB using another computer. If you need to, you could use a boot-able CD to do the installation. Then booting the laptop from the 8GB USB.

Be careful not to install GRUB or Ubuntu on the hard disk of the other computer. That is why I removed the hard disk from my laptop when I made my USB-portable-OS.

The only reason I suggest this is to answer to your question > **slo_hand2 said:**
> One last question about ubuntu, can I run this from the usb stick and have complete control like if it was installed on the hard drive?  Personally, I wouldn't want to run a computer in this configuration permanently if I had other choices.

---

### Post by slo_hand2 on 2012-02-03
> **Old_Gray_Wolf said:**
> You could install on the 8GB USB using another computer. If you need to, you could use a boot-able CD to do the installation. Then booting the laptop from the 8GB USB.

Be careful not to install GRUB or Ubuntu on the hard disk of the other computer. That is why I removed the hard disk from my laptop when I made my USB-portable-OS.

The only reason I suggest this is to answer to your question  Personally, I wouldn't want to run a computer in this configuration permanently if I had other choices.

I understand, but since the laptop is a piece of junk anyway I thought just for fun, and experimental purposes I would try.
Thank you for all your help, I like learning new things, and Linux is something I would like to learn more about.

---

