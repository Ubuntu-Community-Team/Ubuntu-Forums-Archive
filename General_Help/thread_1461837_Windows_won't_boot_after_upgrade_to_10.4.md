---
title: "Windows won't boot after upgrade to 10.4"
date: 2010-04-24
forum: General Help
---

### Post by rshel on 2010-04-24
Hi,

I upgraded my ubuntu to 10.4 the other night. Everything went well and 10.4 worked great.  However, I tried to boot up Windows this morning and found that after selecting XP from the grub menu, all I got was a black screen.  I can access the drive from linux and can save the music and photos I store on the HD with windows, but I hope someone can give me an easier, or at least faster fix.  I'm afraid I was not paying enough attention during the upgrade (late night!) when I got to the point where I was asked about installing grub on various drives and I may have installed it over the mbr/pbr??? on the windows hd.  Does anyone have an guess what I might have done?  Here is the output from fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         464       19310   151388527+   7  HPFS/NTFS
/dev/sda4           19311       19457     1180777+   5  Extended

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001a5a7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6079    48829536   83  Linux
/dev/sdb2            6080       60801   439554465    5  Extended
/dev/sdb5           59858       60801     7582648+  82  Linux swap / Solaris
/dev/sdb6            6080       59857   431971722   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 40.0 GB, 40007761920 bytes
64 heads, 32 sectors/track, 38154 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000


As always, I appreciate any help.

---

### Post by Kljuka on 2010-04-24
I would guess, you had problems with grub. Check how it's configured.
It's located in /boot/grub/menu.lst

Did you install additional hard drives? Or did you create any new partitions? In that case, the entry about your windows partition in menu.lst might not be correct (root          (hd0,0)).
Check also if the Windows entry within menu.lst has "makeactive".

Hope this helps

---

### Post by rshel on 2010-04-24
Thanks for the quick response.  

After looking in /boot/grub/ I see that there is NO file called menu.lst.  A search finds no file in my file system.  How can I have deleted this and how can I be booting at all without this file?
And should I try to reinstall grub?

<bump>

OK.  I must have grub2 since I do have a grub.cfg file.  I ran update-grub and it adds Windows XP to the boot menu.  Windows XP appears in the boot menu, but when I select it, I get a black screen with a blinking cursor.  As if windows cannot find an init file or something?

Any help would be appreciated.

---

### Post by Premium Jersey Milk on 2010-04-30
> **rshel said:**
> Thanks for the quick response.  

After looking in /boot/grub/ I see that there is NO file called menu.lst.  A search finds no file in my file system.  How can I have deleted this and how can I be booting at all without this file?
And should I try to reinstall grub?

<bump>

OK.  I must have grub2 since I do have a grub.cfg file.  I ran update-grub and it adds Windows XP to the boot menu.  Windows XP appears in the boot menu, but when I select it, I get a black screen with a blinking cursor.  As if windows cannot find an init file or something?

Any help would be appreciated.

I have the same problem as you, black screen with a blinking cursor. But, I'm trying to boot with a windows seven loader.

I really need a fix/more info. I need to get on seven and use lightroom/photoshop for some photos I just shot for someone.

---

### Post by wilee-nilee on 2010-05-01
> **Premium Jersey Milk said:**
> I have the same problem as you, black screen with a blinking cursor. But, I'm trying to boot with a windows seven loader.

I really need a fix/more info. I need to get on seven and use lightroom/photoshop for some photos I just shot for someone.

Start your own thread and post this boot script.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Same for the thread starter post the script in code tags

---

### Post by Copernicus1234 on 2010-05-01
May be this bug: 

> We had a late discovery of GRUB bootloader bug affecting dual-boot users of Ubuntu. When installing in a dual-boot environment, the other operating system will not appear at first in the GRUB menu. Installing the available updates and rebooting will fix this issue. However, it was determined the day of the release that this is not an optimal solution for new users or those not connected to the Internet. 

[https://wiki.ubuntu.com/IncidentReports/2010-04-29-Late-respin-for-bug-570765]("https://wiki.ubuntu.com/IncidentReports/2010-04-29-Late-respin-for-bug-570765")

---

### Post by Kolbis on 2010-05-24
I solved this problem by using the xp install (bootable) disk. Early in the install process you can load the recovery console (press R for repair). Simply type bootfix...it will restore the MBR. After that I had to uptate-grub before it worked.

Another thing: My computer shut down when I tried to start xp from grub...just cut the power.

K.

---

