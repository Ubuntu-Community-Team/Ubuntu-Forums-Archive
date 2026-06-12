---
title: "GRUB problem"
date: 2010-04-27
forum: General Help
---

### Post by takisan on 2010-04-27
Hello World,

I currently have a Tri-boot set up. 2GB Primary FAT16 w/ MS-DOS 6.22, 16GB NTFS with XP, and 16GB EXT4 with Karmic. When I boot and load up GRUB, I only get Ubuntu and Windows, but after selecting Windows, it lets me choose between Windows or DOS. I'd rather have DOS as an option at the GRUB menu, but have no idea how to do that.

Thanks in advance.

---

### Post by ubunterooster on 2010-04-27
apt-get update grub?

---

### Post by towheedm on 2010-04-27
> **takisan said:**
> Hello World,

I currently have a Tri-boot set up. 2GB Primary FAT16 w/ MS-DOS 6.22, 16GB NTFS with XP, and 16GB EXT4 with Karmic. When I boot and load up GRUB, I only get Ubuntu and Windows, but after selecting Windows, it lets me choose between Windows or DOS. I'd rather have DOS as an option at the GRUB menu, but have no idea how to do that.

Thanks in advance.

I'll assume you installed MSDOS on FAT16, then XP on NTFS and lastly Karmic on EXT4.  If this is correct then what's happening here is that after you installed XP it removed the MSDOS bootloader, installed the NTFS bootloader  and set itself to dual-boot with MSDOS.  Now when Karmic was installed, Grub now only sees the NTFS bootloader, not MSDOS and so does not detect MSDOS as a bootable partition.

It's been so long since I've dual booted anything with NTFS.  I remember back in the days, I had my machine set to boot 6 OS's: MSDOS, WinXPPro, NT2000Pro, NTServer, OpenCaldera and RedHat.  I believe the bootloader then was LILO and I had to manually set it up to show all OS's and allow me to select.

Unfortunately, both the MSDOS and NTFS bootloader uses the same named files: MSDOS.SYS and IO.SYS.  I remember vaguely needing the versions for both MSDOS which I named MSDOS.DOS and IO.DOS and the version for NTFS which I named MSDOS and IO something, can't recall now.  During the selection process I had to copy the appropriate files to MSDOS.SYS and IO.SYS to get it to work.

I know it can be done, because I did it once very very long ago, but can't recall much more than the above.  Sorry bout that.  I'll see if I can find my notes though.

Hope this is some help.

---

### Post by ubunterooster on 2010-04-27
This does sound like LILO is needed if the update grub does not work. LILO is much more flexible

---

### Post by oldfred on 2010-04-28
This site has lots of info on windows and the issue also applies to all versions and your DOS install. If you do not want all the details at least review the pictures to get some understanding of what windows is doing:

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

You may be able to repair each and then get grub to boot each separately.

---

