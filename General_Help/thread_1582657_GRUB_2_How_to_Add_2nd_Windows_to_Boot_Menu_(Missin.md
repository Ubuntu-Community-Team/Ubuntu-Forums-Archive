---
title: "GRUB 2: How to Add 2nd Windows to Boot Menu (Missing but should have been detected)"
date: 2010-09-26
forum: General Help
---

### Post by OzzyFrank on 2010-09-26
OK, now apparently there are great advantages to the huge mess of config files in **Grub 2**, as opposed to simply editing *menu.lst*, but they elude me. All I want to do is **add another Windows entry** to the boot menu, and while this was in legacy Grub a really easy affair, I've just spent a couple of hours sifting through Google results and still don't have an answer.

The situation is that I decided to do a fresh install when I got larger drives, imaged over my old Windows XP fine, and decided to create another partition for Windows 7 (just to have a look - it sucks). Anyway, I was pleased to see Grub 2 added 7 to the menu, but only later realised XP had been left off. Now, XP is actually on sda1 (first partition of the first drive, which has always been the case), but is ommitted, while 7 - which is on sda2 - is listed.

I thought Grub 2 was supposed to be great at probing for other OSes and automagically adding them to the menu, but obviously it has failed in this case (I would have expected it to find XP on sda1 rather than 7 on sda2).

Now, after a bit of reading I am still confused as to what to do about adding an entry, as I've mostly seen how to edit (or remove) existing entries. Do I add it to **/etc/grub.d/30_os-prober**, and if so, how and where in the files? Or do I create a copy of that file, with a name like ***[I]32_os-prober*[/I]**, and replace the 7 info with what's right for XP (once again, help on what to put in would be appreciated)? Or do I add it to **/etc/grub.d/40_custom**, and if so, what is the syntax?

Also, if you have info on using **UUIDs** with Grub 2, it would help. In legacy Grub I got around boot issues resulting from weird device names changes (*sda1* would become *hda1* and back again, which made the system unbootable till I manually edited *menu.lst*) by specifying the UUIDs instead of names like *sda1*.

Thanks in advance for helping sort this out.

---

### Post by OzzyFrank on 2010-09-26
PS: Here is the output from **update-grub**:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
**[COLOR="Red"]Found Windows 7 (loader) on /dev/sda1[/COLOR]**
done

... while** sudo blkid -c /dev/null** displays:
**[COLOR="RoyalBlue"]/dev/sda1: LABEL="Windows XP" UUID="1D3688CD689CA81D" TYPE="ntfs" [/COLOR]**
**[COLOR="Red"]/dev/sda2: LABEL="Windows 7" UUID="7FABF7DA4717AB8F" TYPE="ntfs"[/COLOR]** 
/dev/sda3: UUID="7bdf888f-7125-4910-bbbd-04de7ad34717" TYPE="ext4" 
/dev/sda5: LABEL="Swap" UUID="3481abb9-52c1-41b6-8f52-265586d130e8" TYPE="swap"

Windows XP is indeed on sda1, so you're probably thinking W7 overwrote the MBR with its own loader, which might be the case, yet I have to add I can boot to XP without issue using 3rd party tools (did so with the Super Grub 2 Disk, and my installed Acronis OS Selector has absolutely no problems booting either Windows version).

---

