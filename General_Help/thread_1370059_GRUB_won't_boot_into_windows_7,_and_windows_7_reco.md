---
title: "GRUB won't boot into windows 7, and windows 7 recovery erases ubuntu..."
date: 2010-01-01
forum: General Help
---

### Post by amiejay on 2010-01-01
Whenever I select Windows 7 under GRUB, it just hangs at a flashing underscore :(
windows 7 is installed under my first primary partition, what should the GRUB section look like for it?
I can't check what mine looked like because this happened:

[LIST=1]
[*] I started up the windows 7 recover (another option under GRUB, on hd(0,3). 7 is on hd(0,1)) and it worked.
[*] I decided that i wanted to try something else before i restore my windows 7 partition to its factory state, so i exit the recovery thing.
[*]Next thing I know, my Ubuntu partition is completely gone, along with my grub.cfg files -.-
[/LIST]
 
Partitions are like this in this order:
sda1: Windows 7 (can't boot into)
sda8: ubuntu (gets erased)
sda5: partition i'm going to use soon for another distro
sda6: Fat 32 partition for media files, etc.
sda7: swap partition
sda3: Windows Recovery 
sda4: really small fat32 partition that i think ASUS uses for quick boot

Asus Eee PC btw.

oh, and by default, there was like 20 MB of free space in front of my windows partition (idk why asus did that) and when i shrunk my first partition (the windows one) it moved it all to the left -.- do you think something when wrong while doing that?

---

### Post by Brandon Williams on 2010-01-03
The section for my Windows 7 boot looks like this:

```
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 40244da5244d9f32
	chainloader +1
}
```

You would have to figure out what the UUID of the partition is so that you can replace the value on the 'search' line.

If you boot into Ubuntu using the grub command prompt, you should be able to regenerate your grub.cfg with 'sudo update-grub', provided that you have os-prober installed.

---

### Post by Leppie on 2010-01-03
is there a cd/dvd drive in your eee pc?
otherwise, do you still have the install/livecd media you used to install ubuntu on this machine available?

if the linux partition has only been deleted, it may be that you can recover it. if it was also formatted, that will be difficult.

---

### Post by amiejay on 2010-01-03
That's what my GRUB looked like, yep, windows 7 was the first OS, hd(0,1) in GRUB 2. 
No DVD drive in the eee pc :(
I restored the linux partition, it's the windows one i was worried about....turns out the 20 MB blank space in front of windows 7 was needed for it to boot for some reason. Have to reinstall windows completely :(

---

### Post by k64 on 2010-01-03
> **amiejay said:**
> That's what my GRUB looked like, yep, windows 7 was the first OS, hd(0,1) in GRUB 2. 
No DVD drive in the eee pc :(
I restored the linux partition, it's the windows one i was worried about....turns out the 20 MB blank space in front of windows 7 was needed for it to boot for some reason. Have to reinstall windows completely :(

I had this problem when my Windows Vista partition was to the right of Ubuntu. For some reason, GRUB 2 fails to recognize Windows drives to the right of itself. However, it does recognize them when they're on the left. Why? It's the biggest mystery I've ever seen.

---

### Post by amiejay on 2010-01-03
Yeah, I'm really not liking windows after this experience. Especially since I don't have a windows Starter edition CD, so i can't reinstall. I'll just have to get a Professional x86 one from MSDN AA. Any good programs for trimming down a windows 7 professional install for a netbook? vlite isn't working for me :(

---

### Post by k64 on 2010-01-04
> **amiejay said:**
> Yeah, I'm really not liking windows after this experience. Especially since I don't have a windows Starter edition CD, so i can't reinstall. I'll just have to get a Professional x86 one from MSDN AA. Any good programs for trimming down a windows 7 professional install for a netbook? vlite isn't working for me :(

Windows 7 generally performs about the same as XP no matter what hardware it's on. In WorldBench 6, PC World's scores of Win7 Starter and Win7 Home Premium/Pro were only two points different - Home Premium and Pro scoring the same - and 2 points behind Starter. Translation: You won't notice much of a difference.

---

### Post by amiejay on 2010-01-04
Sweet! So just turn off aero and it's basically the same thing? Only i'd actually be able to change the desktop background :P

---

### Post by k64 on 2010-01-04
> **amiejay said:**
> Sweet! So just turn off aero and it's basically the same thing? Only i'd actually be able to change the desktop background :P

Heck, those WorldBench 6 scores were with Aero enabled! I'm sure disabling Aero will probably tie it with Starter.

---

### Post by rileinc on 2010-01-04
I've had that problem too when I bought a new Acer laptop a month ago. It's preinstalled with W7 home premium along with a bootable recovery partition (that's normally invisible). After installing Ubuntu 9.10, grub identifies the recovery partition as Vista for some reason. 
  Out of curiosity, I tried booting into the said entry on grub menu and guess what? 
The recovery tool erased /boot. What was originally /boot became an unformatted partition. I don't know how or why that happened because I didn't run the recovery tool. The same happens when I boot a W7 ultimate retail DVD.

---

### Post by amiejay on 2010-01-04
sweet! Can i disable my desktop's windows 7 pro x86 key and use it on my netbook?
I want to put windows 7 pro x64 on my desktop soon anyways.

---

### Post by k64 on 2010-01-04
> **amiejay said:**
> sweet! Can i disable my desktop's windows 7 pro x86 key and use it on my netbook?
I want to put windows 7 pro x64 on my desktop soon anyways.

Now hold up there. Once you activate Windows on one computer, you have to purchase a new license to put it on another one. I see this as (kind of) a nuisance - but Microsoft is only trying to keep their (proprietary) rights to the software. Linux, on the other hand, doesn't have to be activated - and so can be installed on any computer. (Ubuntu is a kind of Linux.)

Here's the comparison between the two licenses:

[http://en.wikipedia.org/wiki/Software_License_Agreement](http://en.wikipedia.org/wiki/Software_License_Agreement)
[U]
[/U][http://en.wikipedia.org/wiki/GNU_GPL](http://en.wikipedia.org/wiki/GNU_GPL)

---

### Post by amiejay on 2010-01-04
Eh. I'll just have to waste another one of my MSDN AA keys. oh well...

---

### Post by garvinrick4 on 2010-01-04
In Windows 7 the D: drive the original factory OS is seen as Vista by Linux. It just is until
Microsoft fixes. I have used it as experiment to reinstall Window 7 OS and it did not bother
my extended or logical partitions. Just installed  7 back to original condition and left mbr in sda1 alone also. As usual just did "sudo update-grub" and all was OK. 
 I think all the so called VISTA partition in 7 is like sda3 or sda4 but shows up on end of partition table but of course has to be one of the 4  primarys.
Here is fdisk -l and it sda4 shows up at end of partition table in gparted. And shows up
as Vista in grub2 menu.

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe7e8e0a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       26132   209696248    7  HPFS/NTFS
/dev/sda3           26133       37330    89947935    5  Extended
/dev/sda4           37331       38914    12709888    7  HPFS/NTFS
/dev/sda5           32107       37111    40202631   83  Linux
/dev/sda6           37112       37330     1759086   82  Linux swap / Solaris
/dev/sda7           26133       31856    45977967   83  Linux
/dev/sda8           31857       32106     2008093+  82  Linux swap / Solaris

---

### Post by amiejay on 2010-01-04
Yeah, on my home computer, "vista" (the recovery thing) never touched anything else, but i guess on netbooks it does...

---

