---
title: "dual booting with Windows 7"
date: 2011-09-07
forum: General Help
---

### Post by rmcellig on 2011-09-07
I have Ubuntu installed on my PC. I would like to install Windows 7 side by side. How do I do this? Do I have to create a new partition and then install Windows 7 to it? If so, what format should the partition be or does it really matter seeing that Windows 7 should be formatting the partition NTFS when it installs. I just need some clarification before I proceed. 

Thanks!

---

### Post by nipunshakya on 2011-09-07
^^^ Dear sir, whenever we try to install windows after linux is already inside the machine, the MBR gets overwritten. So, we can bootoff a LIVECD and repair the MBR. So basically what we need to do is you Create an NTFS partition for windows (using fdisk, GPartEd or whatever tool you are familiar with) using the LIVECD ofcourse.


Regards, WinuxUser[]("https://help.ubuntu.com/community/Grub2/#Reinstalling%20GRUB2")

---

### Post by rmcellig on 2011-09-07
I booted from the Ubuntu Live CD and created an NTFS partition with a size of 44GB. Then when I boot up from the Windows installer CD I just install to this partition? Will my windows partition show up in the Grub bootloader?

Thanks!!

---

### Post by YesWeCan on 2011-09-07
It's even simpler (assuming your disk is MBR format and you use BIOS booting and not UEFI).
 
All you need is an empty primary partition slot and, say, 20GB of unallocated disk space. Windows will install itself in this space and format it appropriately.

Ubuntu doesn't use the standard MBR boot code and replaces it with Grub boot code. When you install Windows it will restore the standard code. So afterwards, as WinuxUser said, you'll need to boot live CD and reinstall Grub to the MBR. You'll have to repeat this in the event that Windows repairs the MBR for any reason in the future.

---

### Post by nipunshakya on 2011-09-07
> **rmcellig said:**
> I booted from the Ubuntu Live CD and created an NTFS partition with a size of 44GB. Then when I boot up from the Windows installer CD I just install to this partition? Will my windows partition show up in the Grub bootloader?

Thanks!!

I haven't personally tried to install windows after ubuntu's rule over the machine but yes the space you created as NTFS will be detected by the windows and then you can install it inside the partition.....
If you are good at some terminal thing, i suggest you look at the following before proceeding....else if you aren't sure of what the thing below even means, YesWeCan has the right answer stored for you above.....take a look..:) i found it in ubuntu documentation

**Recovering GRUB after reinstalling Windows**

 Please use this guide : 

[LIST]
[*][https://help.ubuntu.com/community/Grub2/#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2/#Reinstalling%20GRUB2")
[/LIST]
 
**Master Boot Record backup and re-replacement**

 Back-up the existing MBR, install Windows, replace your backup overwriting the Windows boot code: 

[LIST=1]
[*]Create an NTFS partition for windows (using fdisk, GPartEd or whatever tool you are familiar with)
[*]Backup the MBR e.g. dd if=/dev/sda of=/mbr.bin bs=446 count=1
[*]Install windows
[*]Boot into a [LiveCD]("https://help.ubuntu.com/community/LiveCD")
[*]Mount your root partition in the LiveCD
[*]Restore the MBR e.g. dd if=/media/sda/mbr.bin of=/dev/sda bs=446 count=1
[*]Restart and Ubuntu will boot
[*]Setup grub to boot windows
[/LIST]

Its not necessary you do as it says, but still if you know a bit of terminal, you can obviously try the above....goodluck

Regards, WinuxUser

---

### Post by rmcellig on 2011-09-07
I now have Windows running in the allocated partition. I haven't restarted yet though. I hope GRUB loads so I can see the other linux OS's I have and I can start up from them. I will post back any problems. Fingers crossed :)

---

### Post by YesWeCan on 2011-09-07
Yes, that will work (referring to post #5).
Actually, there are many ways to skin a cat in linux and there is an easier one which doesn't involve dd - a ruthless command even in the hands of experienced geeks. :)

To keep it simple, just install Windows. Make sure it boots ok.
Then boot live CD (asme version as installed)
[COLOR="DarkSlateBlue"]sudo mount /dev/sdax /mnt[/COLOR]
choose x as the number of your Ubuntu root (or boot) partition.
[COLOR="DarkSlateBlue"]sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]

That's it.

---

### Post by YesWeCan on 2011-09-07
> **rmcellig said:**
> I now have Windows running in the allocated partition. I haven't restarted yet though. I hope GRUB loads so I can see the other linux OS's I have and I can start up from them. I will post back any problems. Fingers crossed :)
It will boot back into Windows until you do the Grub reinstall.

Once you are booted in Ubuntu, run
[COLOR="DarkSlateBlue"]sudo update-grub[/COLOR]
to add Windows to the Grub menu.

I'm assuming you are using Grub2.

---

### Post by rmcellig on 2011-09-07
YesWeCan.

You are right. When I restart my machine, I boot right back into Windows 7. How exactly do I reinstall GRUB like you suggest and add Window to the GRUB menu? Do I have to reboot from the Ubuntu Live CD? This is fun! :)

---

### Post by YesWeCan on 2011-09-07
> **rmcellig said:**
> YesWeCan.

You are right. When I restart my machine, I boot right back into Windows 7. How exactly do I reinstall GRUB like you suggest and add Window to the GRUB menu? Do I have to reboot from the Ubuntu Live CD? This is fun! :)
I'm glad you think this is fun. :P

Yes, just boot the live Ubuntu CD. Make sure it is the same Ubuntu version as on your hard drive.

Then you need to find out the name of your Ubuntu partition. It will be something like sda1 or sda5 or another. The friendly way is to run Disk Utility. The quicker, geek way is to open a terminal and run
[COLOR="DarkSlateBlue"]sudo fdisk -lu[/COLOR]

Then in a terminal reinstall Grub. You have to mount the Ubuntu root partition so the Grub installer can find its files there.

[COLOR="DarkSlateBlue"]sudo mount /dev/sdax /mnt[/COLOR]   (choose x as I described above)
[COLOR="DarkSlateBlue"]sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]

I'm assuming your disk is sda and not sdb or something else.


Then reboot your hard drive.
This time it will boot into Ubuntu.
Open a terminal again and run
[COLOR="DarkSlateBlue"]sudo update-grub[/COLOR]
and this will detect Windows and add it to the menu and the next time you boot you'll see the menu and get to choose between Ubuntu and Windows.

---

### Post by rmcellig on 2011-09-07
OK. I followed your instructions while booted in the Live CD. Everything went fine. When I removed the CD and then restarted, a prompt appears: 

error:File Not found
GRUB rescue>

What do I do now?

---

### Post by YesWeCan on 2011-09-07
Ok. no problem. Let's take a closer look.
Would you boot the live CD again and post the output of
sudo fdisk -lu

---

### Post by nipunshakya on 2011-09-07
Sorry for interrupt and going off topic but when i was offering some assistance to OP, i had some confusions to myself too....thanks YesWeCan for your help and support...i have learnt alot today from this thread and the googling things mentioned by OP....

Regards,WinuxUser

---

### Post by YesWeCan on 2011-09-07
> **WinuxUser said:**
> Sorry for interrupt and going off topic but when i was offering some assistance to OP, i had some confusions to myself too....thanks YesWeCan for your help and support...i have learnt alot today from this thread and the googling things mentioned by OP....

Regards,WinuxUser
No worries. This is a confusing system. I get confused regularly and I think I understand it. :P So if you think there is a good way to do something then just pitch right in there with the rest of us. Usually the final solutions end up being bits of everybody's suggestions.

---

### Post by rmcellig on 2011-09-07
here you go:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eb98f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   212955135   106476544   83  Linux
/dev/sda2   *   212955136   304812031    45928448    7  HPFS/NTFS
/dev/sda3       304814078   488396799    91791361    5  Extended
/dev/sda5       482242560   488396799     3077120   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by YesWeCan on 2011-09-07
That looks good.
What version of Ubuntu are you using?

The commands you should have used (and probably did, just sayin' ;) ) are:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

If you did something different then do these now and reboot.

Otherwise there is something more interesting going on.

The grub rescue> prompt is actually a positive sign. It means the Grub boot program at the start of the disk is running fine but it cannot locate the files it needs in Ubuntu's /boot directory. This may be because it is looking in the wrong partition.

---

### Post by rmcellig on 2011-09-07
What I did before was this:

sudo mount /dev/sda2 /mnt

Maybe that's why it didn't work. I saw the GRUB menu on startup and am now booting into Pinguy 11.04. The other OS's including Windows do not show up in the GRUB menu on startup. Just the Pinguy one. What do I do now so all of my partitions show up in the GRUB menu. I have Mint, Ubuntu, Pinguy and another one that starts with a Z and looks like Windows 7 on startup.

---

### Post by YesWeCan on 2011-09-07
Good. You've got Pinguy booting. Is Pinguy good - it's a variation of Ubuntu right?

So having booted Pinguy you should run
[COLOR="DarkSlateBlue"]sudo update-grub[/COLOR]
and it should list the OS's it has detected (also memtest) and Windows 7 should be near the bottom of the list. These shouls all show up on the menu next time you boot.

---

### Post by YesWeCan on 2011-09-07
> **rmcellig said:**
> What I did before was this:

sudo mount /dev/sda2 /mnt

Maybe that's why it didn't work. 
Exactly.
Your fdisk -lu output shows 4 partitions, 3 primary and 1 logical:
```

Device    Boot     Start        End     Blocks   Id   System
/dev/sda1           2048  212955135  106476544   83   Linux
/dev/sda2  *   212955136  304812031   45928448    7   HPFS/NTFS
/dev/sda3      304814078  488396799   91791361    5   Extended
/dev/sda5      482242560  488396799    3077120   82   Linux swap / Solaris

```
Your Pinguy OS is located in sda1 and has a linux file system.
Windows 7 OS is located in sda2 and has NTFS file system.
Your linux swap is in sda5
the extended partition sda3 is a special one that is a sort of trick to allow the use of more than 4 partitions. Partitions numbered 1 to 4 are always called "primary" partitions and those numbered greater than 4 are always called "logical" partitions.

---

### Post by rmcellig on 2011-09-07
When I started up Pinguy, a window appears for user/password. I did this but it keeps returning to the same window along with a Power manager configuration not being set up properly error.

---

### Post by rmcellig on 2011-09-07
should i restart from the live cd again?

---

### Post by YesWeCan on 2011-09-07
Does Windows appear on your boot menu and does it boot ok?

---

### Post by rmcellig on 2011-09-07
no. i am stuck at the window i mentioned in my previous post. there is a bottom panel that allows me to suspend, restart or shutdown.

---

### Post by YesWeCan on 2011-09-07
Choose restart. This will reboot your PC.
If Grub is working ok you should first see the normal BIOS stuff and then you should see a Grub menu with Windows as a selection. Select it and check it boots ok.
You can shut down Windows and reboot and select Pinguy again.

I just want to check the Grub is working ok before looking into the Pinguy power mgmt issue.

---

### Post by rmcellig on 2011-09-07
when i restart, the grub menu with pinguy and memtest appears booting back into the same window mentioned above.

---

### Post by YesWeCan on 2011-09-07
Ok. Let's see what's really going on in some detail. You'll need to boot the live CD again and download and run bootinfoscript:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Follow the instructions on the web page. It will output a file called RESULTS.txt.

Copy & paste the contents of RESULTS.txt into a post and then highlight the text and click the # above. This puts "code" tags around it and makes it easier to read.

---

### Post by rmcellig on 2011-09-07
will do.

---

### Post by rmcellig on 2011-09-07
Where is the # symbol I am supposed to select?

---

### Post by rmcellig on 2011-09-07
<code>           Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   212,955,135   212,953,088  83 Linux
/dev/sda2    *    212,955,136   304,812,031    91,856,896   7 NTFS / exFAT / HPFS
/dev/sda3         304,814,078   488,396,799   183,582,722   5 Extended
/dev/sda5         482,242,560   488,396,799     6,154,240  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        da3fc62a-7caa-4e9c-9b85-c4ae1ffdb655   ext4       
/dev/sda2        38D6CFEE6A804FF3                       ntfs       Windows
/dev/sda5        b4381dd8-e81d-4315-9775-84ceadbf1259   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root da3fc62a-7caa-4e9c-9b85-c4ae1ffdb655
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root da3fc62a-7caa-4e9c-9b85-c4ae1ffdb655
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
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
menuentry 'Pinguy OS, with Linux 2.6.38-10-generic' --class pinguy --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root da3fc62a-7caa-4e9c-9b85-c4ae1ffdb655
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=da3fc62a-7caa-4e9c-9b85-c4ae1ffdb655 ro  quiet  quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-10-generic
}
menuentry 'Pinguy OS, with Linux 2.6.38-10-generic (recovery mode)' --class pinguy --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root da3fc62a-7caa-4e9c-9b85-c4ae1ffdb655
	echo	'Loading Linux 2.6.38-10-generic ...'
	linux	/boot/vmlinuz-2.6.38-10-generic root=UUID=da3fc62a-7caa-4e9c-9b85-c4ae1ffdb655 ro single  quiet
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-10-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root da3fc62a-7caa-4e9c-9b85-c4ae1ffdb655
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root da3fc62a-7caa-4e9c-9b85-c4ae1ffdb655
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=da3fc62a-7caa-4e9c-9b85-c4ae1ffdb655 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda5 during installation
UUID=b4381dd8-e81d-4315-9775-84ceadbf1259 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 100.032344818 = 107.408912384  boot/grub/core.img                             1
 100.304519653 = 107.701157888  boot/grub/grub.cfg                             1
   3.042037964 = 3.266363392    boot/initrd.img-2.6.38-10-generic              1
  78.724887848 = 84.530204672   boot/vmlinuz-2.6.38-10-generic                 2
   3.042037964 = 3.266363392    initrd.img                                     1
  78.724887848 = 84.530204672   vmlinuz                                        2

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda3

00000000  18 ff 89 ba e0 29 5d 9e  27 1c be cf 67 f7 1d b2  |.....)].'...g...|
00000010  7e 50 66 60 8c 08 ae 48  a8 b9 b0 74 99 a5 f8 37  |~Pf`...H...t...7|
00000020  4d 3d 46 dc c2 00 54 eb  bb 67 e2 28 8b 49 c1 88  |M=F...T..g.(.I..|
00000030  af 2e 5e f6 d6 6d 39 41  c1 a2 55 32 6c 77 0e 9e  |..^..m9A..U2lw..|
00000040  44 19 33 70 10 ac c8 87  d0 ee 0e c0 64 4d 74 99  |D.3p........dMt.|
00000050  6a d4 f0 4f a7 60 dd a6  37 aa e5 65 1a ae 9f c8  |j..O.`..7..e....|
00000060  8a 4f c7 77 22 e4 11 47  38 c8 59 ab 82 93 fd d1  |.O.w"..G8.Y.....|
00000070  37 55 56 d9 bf c0 9b 2a  c4 f4 b6 ad bf 8e 64 a3  |7UV....*......d.|
00000080  44 27 96 27 5e 53 02 a9  7b ff 57 df 89 13 bd 2a  |D'.'^S..{.W....*|
00000090  b9 f1 32 d5 35 c1 a9 29  1f f9 d5 b9 e6 0f 1c 4e  |..2.5..).......N|
000000a0  64 3c 6f 33 5a 7f 3f 4b  ed 45 d6 37 ae b9 a1 e9  |d<o3Z.?K.E.7....|
000000b0  74 f1 c6 f0 da e5 df 17  e2 78 e0 e5 ac 22 bb c2  |t........x..."..|
000000c0  e5 7d 2e 35 a2 20 aa 2a  ab a5 6b 06 5d 44 c5 49  |.}.5. .*..k.]D.I|
000000d0  5b a8 ea 87 0d c7 f8 5b  25 3a 3a 6f 72 72 9b 7e  |[......[%::orr.~|
000000e0  13 f0 fc 53 76 5a 22 a5  28 48 60 08 49 55 63 97  |...SvZ".(H`.IUc.|
000000f0  2d 61 28 4f 0c 75 73 36  c3 fe bc a3 51 9a 77 4d  |-a(O.us6....Q.wM|
00000100  69 3f a4 3b 1e e1 55 a9  51 35 83 17 6d 62 3e 16  |i?.;..U.Q5..mb>.|
00000110  f6 e9 5a d2 9f d3 9c 8a  bb f5 e2 ea ae f9 e4 70  |..Z............p|
00000120  cf e5 9e 5f d0 67 d5 87  f3 0c 10 d6 56 01 48 ae  |..._.g......V.H.|
00000130  0c 29 98 d1 f0 85 c2 4c  2c d4 15 fd 55 95 de 41  |.).....L,...U..A|
00000140  ed e0 79 5d f4 e0 07 c2  2d 30 ef c7 14 b7 46 fc  |..y]....-0....F.|
00000150  83 76 18 d0 90 30 19 32  14 e7 f1 5f fc 6b f8 8b  |.v...0.2..._.k..|
00000160  78 06 3d 6c ec 20 19 1a  0e 47 3a 5c 08 03 26 40  |x.=l. ...G:\..&@|
00000170  40 36 f4 ca da 01 f3 2e  33 02 e7 3a 0a 90 1e 89  |@6......3..:....|
00000180  01 e2 cf 84 05 6b 45 3e  2f ab 09 a8 35 12 11 54  |.....kE>/...5..T|
00000190  dd 8c 46 4c 5e c5 8b f1  5e 0d 05 7a b3 9b 8d 8b  |..FL^...^..z....|
000001a0  fc 8b fa 03 86 21 88 05  9f ba a7 75 9d 3f f7 5b  |.....!.....u.?.[|
000001b0  b7 f4 1a fc 24 82 19 e9  cd 22 2c 1b 3c 83 00 fe  |....$....",.<...|
000001c0  ff ff 82 fe ff ff 02 58  93 0a 00 e8 5d 00 00 00  |.......X....]...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

 </code>

---

### Post by YesWeCan on 2011-09-07
The # symbol is at the top right of the editing window.

<code> and </code> will work if you use [] instead of <>.

---

### Post by rmcellig on 2011-09-07
are you able to see anything in the text i posted that may be causing the problem?

---

### Post by YesWeCan on 2011-09-07
There is no menu entry for Windows in grub.cfg.

A couple of times I said to run sudo update-grub. What happened when you did this - what output did you see?

Tell me if this is correct:
1. After you did the last grub-install (with sda1 mounted) you rebooted and you were able to log in to Pinguy ok.
2. You then ran sudo update-grub and watched the output. Did you see Windows listed or did you see any errors such as os-prober missing?
3. You then rebooted and this time when you tried to log in you got a power management error and could not log in.

Is that right?

---

### Post by rmcellig on 2011-09-07
OK This is what i did:


Then boot live CD (asme version as installed)
sudo mount /dev/sdax /mnt
choose x as the number of your Ubuntu root (or boot) partition.
sudo grub-install --root-directory=/mnt /dev/sda

after i di this i restarted the machine, saw the GRUB menu with just the pinguy os. Clicked on it and then was presented with that window I described where it prompted me for user/password. That's as far as i got. I am now booted in the live cd awaiting further instructions. Thanks so much for your help!!!!

---

### Post by rmcellig on 2011-09-07
i just want to get something straight. I was supposed to run sudo update grub after booting correctly into pinguy? If so, i was unable to do this because i never got to boot right into pinguy because of the window that came up with the configuration error.

---

### Post by YesWeCan on 2011-09-07
Ok, that now makes sense.
Since you cannot log in to Pinguy you'll have to use chroot (see: [https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)).

From live CD run these commands (one at a time):
```
sudo mount /dev/sda1 /mnt
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
update-grub
grub-install /dev/sda
exit

```
Then immediately reboot the hard disk.
Report any error messages.

---

### Post by rmcellig on 2011-09-07
OK so this is what I did from the Live CD. I'm still restarting to that window that has the configuration error. I wish I could take a screen shot for you.

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/#

---

### Post by YesWeCan on 2011-09-07
The os-prober is missing. This is needed to detect other OSs like Windows.

Start again (fresh boot of live CD) then do
```
sudo mount /dev/sda1 /mnt
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
sudo apt-get install os-prober
update-grub
grub-install /dev/sda
exit
```

Yes, I would like to see that screenshot. Some Googling will be needed to figure out why you cannot log in to Pinguy. One thing at a time.

---

### Post by rmcellig on 2011-09-07
OK I am rebooting now.

Here is what I entered in terminal:


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# sudo apt-get install os-prober
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
os-prober is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# exit

---

### Post by rmcellig on 2011-09-07
It still starts up to the login window with the power management error.

---

### Post by YesWeCan on 2011-09-07
No, that didn't work either.
Well all I can think of now is to remove Pinguy's Grub and reinstall it from scratch. Again, this is from the Ubuntu Grub2 webpage:
```
sudo mount /dev/sda1 /mnt
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
apt-get update
apt-get purge grub-common grub-pc
apt-get install grub-pc
exit
```
It will ask you where to install the Grub/boot code: choose sda (do NOT choose sda1 or sda2, etc)

---

### Post by rmcellig on 2011-09-07
maybe i should just reformat my drive, reinstall windows 7 and then install my linux OS's side by side like I did when I installed the linux OS's on my drive. Just thinking out load.

---

### Post by YesWeCan on 2011-09-07
> **rmcellig said:**
> It still starts up to the login window with the power management error.
Would you post the exact error message and any other details you think might be significant?

So you get a login screen ok. Then you enter name and password and click to log in and then something happens and you end up at the login screen again with an error message displayed somewhere?

Is the Pinguy login screen like ubuntu's do you know? Are there menus at the bottom to select various options?

---

### Post by rmcellig on 2011-09-07
just to be sure, how can i tell if i have grub 2?

---

### Post by oldfred on 2011-09-07
When you ran commands to use grub with sda2 you got part of grub into the Windows partition.

> sda2: ___________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       [COLOR=Red]/boot/grub/core.img[/COLOR]

Windows will not work as you have two folders it sees as /Boot since it is not case sensitive like Linux. You need to delete the /boot folder with grub in it but be careful not to delete the /Boot folder with the BCD as that is essential for Windows.

---

### Post by YesWeCan on 2011-09-07
> **rmcellig said:**
> maybe i should just reformat my drive, reinstall windows 7 and then install my linux OS's side by side like I did when I installed the linux OS's on my drive. Just thinking out load.
That's a last resort option. Windows is probably fine. The issue is that the Grub in Pinguy is not working properly to detect it. A Grub purge/install should solve this. 

So a Windows reinstall is probably not necessary. A Pinguy reinstall might be if either you cannot solve the power mgmt error or you're tired of trying.

If you want to get Windows booting on its own you can restore the normal MBR boot code (this removes Grub from the MBR):
In live CD
[COLOR="DarkSlateBlue"]sudo apt-get install lilo
sudo lilo -M /dev/sda mbr[/COLOR]

---

### Post by YesWeCan on 2011-09-07
> **oldfred said:**
> When you ran commands to use grub with sda2 you got part of grub into the Windows partition.



Windows will not work as you have two folders it sees as /Boot since it is not case sensitive like Linux. You need to delete the /boot folder with grub in it but be careful not to delete the /Boot folder with the BCD as that is essential for Windows.
+1
Well spotted.

---

### Post by YesWeCan on 2011-09-07
> **rmcellig said:**
> just to be sure, how can i tell if i have grub 2?
The bootinfoscript showed you have Grub2 because there is a /boot/grub/grub.cfg file.

Otherwise, you have to be booted into the OS or using chroot and then run
grub-install -v

Grub1 has version < 1.0 and Grub2 has versions >1.9

---

### Post by rmcellig on 2011-09-07
Still the same thing. I think i will reformat my drive and reinstall everything from scratch. Thanks so much for your help and patience!!! At least now I know that I should install Windows first before installing any Linux OS's. It would seem it is easier that way.

---

### Post by rmcellig on 2011-09-07
The startup window does not look like a typical pinguy login window.

---

### Post by YesWeCan on 2011-09-07
> **rmcellig said:**
> Still the same thing. I think i will reformat my drive and reinstall everything from scratch. Thanks so much for your help and patience!!! At least now I know that I should install Windows first before installing any Linux OS's. It would seem it is easier that way.
Normally, it is not a big deal when using Ubuntu. I've done this many times.
Sorry that didn't work out. Hope the fresh install goes well.

---

### Post by rmcellig on 2011-09-07
It has an icon of a computer and right below it home HP Pavillion-dv2700 Notebook PC. Right below that is the user home. When i click on it it prompts me for a password. Then in the upper right hand corner of the screen is a box with an error in it. Install problem! The config defaults for gnome power manager have not been installed correctly. Please contact your computer administrator. 

This is the error I see.

---

### Post by rmcellig on 2011-09-07
i didn't reformat yet. waiting to hear back if you know what that dialog is on startup as described in my previous post.

---

### Post by YesWeCan on 2011-09-07
Interesting. Stand by while I consider this and try to picture it in my mind.
I don't know what the Pinguy login screen looks like. But this isn't it, right?

---

### Post by rmcellig on 2011-09-07
To the best of my knowledge it isn't. But if it is, I'm not sure what the other error could be. Something is missing preventing it from starting up properly?

---

### Post by YesWeCan on 2011-09-07
Ah, an idea. Did you shrink your Pinguy partition to make space for Windows?

---

### Post by rmcellig on 2011-09-07
Yes. I shrank the partition to make some allocated space so that I could create a windows ntfs partition. Would this play into it?

---

### Post by YesWeCan on 2011-09-07
[http://www.geekdevs.com/2010/04/solved-unable-to-boot-due-to-gnome-power-manager-error/](http://www.geekdevs.com/2010/04/solved-unable-to-boot-due-to-gnome-power-manager-error/)
[http://ubuntuforums.org/archive/index.php/t-980711.html](http://ubuntuforums.org/archive/index.php/t-980711.html)

This is likely if you inadvertently shrank it too much. I've found a couple of web pages where this very error can occur if there is insufficient space in the root partition.

---

### Post by rmcellig on 2011-09-07
So I am SOL? If so that's OK and as a linux newbie (i am a mac user) i learned a valuable lesson. That's why i have two laptops that i use for testing stuff like this so that i can continue to learn new things regarding linux.

---

### Post by YesWeCan on 2011-09-07
SOL?

I think you can probably fix this easily (famous last words). Boot live CD and run GParted and resize the Windows partition - move its start to the right a little bit and then move the end of sda1 to the right. A GB or two should be enough.

GParted should show you how much unused space there is in sda1. If it is all "yellowed in" then there is no free space.

---

### Post by rmcellig on 2011-09-07
SOL means s--t out of luck. I will try what you mentioned above right now and post back the outcome. :)

---

### Post by YesWeCan on 2011-09-07
> **rmcellig said:**
> SOL means s--t out of luck. I will try what you mentioned above right now and post back the outcome. :)
The great thing about linux is that there is always one more thing to try. The problem is trying enough ideas before you die of old age. :P

---

### Post by rmcellig on 2011-09-07
Reminds me of Steve Jobs when he does his keynote addresses. Before he finishes he always says, "Just one more thing". :)

---

### Post by YesWeCan on 2011-09-07
FYI moving the start of the Windows partition will break the Windows boot. This is a general problem with OS partitions because they use fixed sector addressing in their boot code. It may be fixable by booting the Windows installation CD and selecting "repair". But you might as easily reinstall it as you haven't had chance to use it yet. ;)

---

### Post by rmcellig on 2011-09-07
yes. i just received a gparted warning regarding this. I will start all over again. thanks again for all of your help as i continue to learn and explore linux. i am really starting to love the things you can do with this amazing os!

---

### Post by YesWeCan on 2011-09-07
You're welcome. Other readers pick up hints from these "explorations" too.
Don't forget to mark this post solved in [COLOR="Red"]Thread Tools[/COLOR] when you are good and ready. :)

---

### Post by rmcellig on 2011-09-07
Done and thanks again!! I now have Windows 7 loaded on the laptop and want to install Ubuntu. I have another related question. What I did before all this stuff started happening is that I installed a different linux distro using the side by side option. Is that the right way to do it? I don't want to use Virtual box so this way allows me to choose my distro from the GRUB menu and then go from there.

---

### Post by oldfred on 2011-09-07
You can do that and it should work if you have deleted all the old Linux partitions. Otherwise you need to do that first.

But I like to have control over partitions and partitions sizes. I recommend a separate NTFS partition for data so you do not write into the Windows system partition and potentially cause Windows issues.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).

One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

---

