---
title: "GRUB question: Adding XP Pro and Windows 7 separately instead of one &quot;Vista (loader)&quot;"
date: 2009-07-18
forum: General Help
---

### Post by _glook on 2009-07-18
Hello. I recently installed Win7RC and am trying to get separate items for XP and 7 into grub. Here is the series of events that took place.

- Started off with dual boot Ubuntu Jaunty Jackalope 32-bit and Windows XP Professional on one hard drive.
- Connected a new hard drive.
- Installed Windows 7 RC on second hard drive.
- Deleted all Ubuntu 32-bit partitions.
- Created Ext4 partitions for 64-bit Jaunty Jackalope.
- Installed Jaunty Jackalope 64-bit.
- Since BIOS booted from second hard drive, switched boot order so that Grub runs, instead of "Vista (loader)".

So at this point, both my new ubuntu loads and the "Vista (loader)" works. However, I don't like the vista loader because it takes me to another loader where I pick either Windows 7 or XP. I'd like to do everything from GRUB, including being able to pick both Windows 7 and XP.

What I did was I previously saved my old menu.lst from my 32 bit Ubuntu and copied the item for XP it over to my new 64-bit Ubuntu. When I select it from GRUB, it gives me "BOOTMGR is missing, please press CTRL+ALT+DEL". I figured it might be on one of my other partitions instead so I changed it from "root (hd0, 0)" to (hd1, 0) and (hd0, 1) etc. When I changed it to those, it says there's nothing there, which leads me to believe XP was on (hd0, 0). So I figured maybe the XP's files are on Windows 7 but I looked in the Windows folder in XP and boot.ini is still there. Also, I don't know how to get Windows 7 to load instead of the Dual Booting "Vista (loader)", since I don't want to go through two booters just to get to Windows 7 (the whole reason for this to begin with). Adding an item in grub for Windows 7 ends up looking exactly like the "Vista (loader)" item.

Anyway, does anyone have suggestions? I'm all ears at this point.

---

### Post by SuperSonic4 on 2009-07-18
Can you post either a screenshot of gparted or the output of ```
sudo fdisk -l
``` (that's a lower case l) and which partitions correspond to XP and Win 7

---

### Post by _glook on 2009-07-18
Oh right, I probably should have done that first.

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c823f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2549    20474811    7  HPFS/NTFS  ## This is WINDOWS 7 RC
/dev/sda2            2550      121601   956285190    f  W95 Ext'd (LBA)
/dev/sda5            2550       12747    81915403+   7  HPFS/NTFS
/dev/sda6           12748       31869   153597433+   7  HPFS/NTFS
/dev/sda7           31870      121601   720772258+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0c3d0c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8938    71794453+   7  HPFS/NTFS  ## THIS IS XP
/dev/sdb2            8939       19457    84493867+   f  W95 Ext'd (LBA)
/dev/sdb5           18764       19457     5574523+  82  Linux swap / Solaris
/dev/sdb6            8939       15017    48829504+  83  Linux
/dev/sdb7           15018       18763    30089713+  83  Linux

Partition table entries are not in disk order

```/dev/sda1 is Windows 7 RC
/dev/sdb1 is Windows XP Pro


This is what the boot section looks like in /boot/grub/menu.lst:
```
# Main Ubuntu
title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        ca0dc036-5f3a-4d98-9c76-54e843acafec
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=ca0dc036-5f3a-4d98-9c76-54e843acafec ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Secondary Boots and Tools:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows Vista (loader)
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        ca0dc036-5f3a-4d98-9c76-54e843acafec
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=ca0dc036-5f3a-4d98-9c76-54e843acafec ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        ca0dc036-5f3a-4d98-9c76-54e843acafec
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ca0dc036-5f3a-4d98-9c76-54e843acafec ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        ca0dc036-5f3a-4d98-9c76-54e843acafec
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=ca0dc036-5f3a-4d98-9c76-54e843acafec ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        ca0dc036-5f3a-4d98-9c76-54e843acafec
kernel        /boot/memtest86+.bin
quiet
```The Windows XP one was added from my old grub (from the 32-bit installation of Ubuntu).

---

### Post by _glook on 2009-07-18
Sorry, is it required to bump topics to the front page to get answers or should I just let this sleep?

---

### Post by master_kernel on 2009-07-18
title        Microsoft Windows 7
root        (hd0,0)
savedefault
makeactive
chainloader    +1

title        Microsoft Windows XP Professional
root        (hd1,0)
savedefault
makeactive
chainloader    +1

---

### Post by _glook on 2009-07-18
Thanks for the code. I made the changes, but unfortunately, Windows 7 gives me "Missing BOOTMGR, Press CTRL+ALT+DEL to restart" problem and Windows XP gives me the "Windows Boot Manager" that gives me the options Windows 7 and Older Operating System. Ideally, I'd like to go directly to boot to either of the Windows Operating systems without going through the "Windows Boot Manager".

---

### Post by master_kernel on 2009-07-20
I have the same issue, just never bothered correcting it. I'm bookmarking this to see when someone finds a solution.

---

### Post by _glook on 2009-07-21
Okay, so I was messing around and I got something to work. But first:
While I was searching for this thread, I came upon this one that looks similar:
[http://ubuntuforums.org/showthread.php?t=1050353](http://ubuntuforums.org/showthread.php?t=1050353)
I have no idea why my google searches before failed to find this thread. Of course, I haven't really looked at it in depth, so I don't know how applicable it is.

Anyway, since the Windows 7 option was giving me "BOOTMGR missing", I copied these files from the root of Windows XP partition to the root of Windows 7 partition: boot.ini, ntldr, and ntdetect. You will need to set your folder options to be able to view both hidden files and you may need to disable the option to hide system and other files. Once I did that, it gave me some wierd error of not finding a file that was clearly there. Then I remembered the 
map        (hd0) (hd1)
map        (hd1) (hd0)
options from the "Vista loader", likely because when grub loads, it loads from the second hard drive but it internally counts it as the first, thusly, needing to switch the hard drives when loading the windows boot manager.
So, I added those two lines to the ends of both of the loaders. So now the "XP Professional" entry looks exactly like my vista loader entry. When I select "Windows 7", it loads up Windows XP. So now I know how to load up Windows XP (I have to change the title from Windows 7 to Windows XP, but that's no big deal). But now Windows 7 brings up the vista loader instead of just loading. I'm probably going to have to actually change the windows boot loader files in either XP or Windows 7. It's probably Windows XP boot loader that I have to change just from guessing, which is easiest to fix anyway.

So, status is:
I've gotten XP to load, but not 7.

---

### Post by _glook on 2009-07-22
Okay, it ended up being pretty easy to get Windows 7 to load up right away. I went into Windows 7, started up cmd.exe as administrator, then I rand bcdedit.exe and changed the timeout time to 0. This makes the loader only load for a split second and then Windows 7 starts to load. It's sort of a hacky solution but hey, the OS comes out this Fall and the free version only lasts ("really") until March of next year. So, I'm done thinking about this.

---

