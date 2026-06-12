---
title: "Reboot and select proper boot device..."
date: 2011-04-16
forum: General Help
---

### Post by Zortis on 2011-04-16
Reboot and select proper boot device or insert boot media in selected boot device and press a key.

I got this error after:

Reducing my Windows 7 partition by about 100gb.

Creating a new partition (100gb) and copying my Ubuntu partition (10gb) to the new partition.

After it was copied, and pasted, the original partition was deleted.

I now had two partitions a new 100gb Ubuntu partition and a 600gb (or so) Windows 7 partition.

All of this was done using a bootable USB with Ubuntu 10.10 and GParted partition editor.

Now when I boot I get the "Reboot and select proper boot device or insert boot media in selected boot device and press a key." error.

I can only boot from the USB so far.

---

### Post by Ad@m on 2011-04-16
The screenshot you posted indicates you have no Linux partition. I think you have deleted your ubuntu partition.

How did you copy your ubuntu partition over to your new partition? (You mean literally copy and paste the files / folders?)

Can you run this command in a terminal,

sudo fdisk -l

and paste the output here?

---

### Post by Zortis on 2011-04-16
The partition labelled 'System' is my Ubuntu. It's always been labelled that.

And I used GParted to copy and paste, you can right click a partition to copy the whole thing and then paste it.

---

### Post by dandnsmith on 2011-04-16
Problem is that you've created the new partition at the start of the HDD - all would have been well if you'd freed space at the higher end of the HDD and used that.
Now the start of Win7 has been dissociated from wher the boot record was pointing, and it is objecting.
Can you recover? - I really don't know, as I've never had any dealings with Win7 and its boot process.

Good luck

---

### Post by Zortis on 2011-04-16
So my computer is f*cked?

---

### Post by Zortis on 2011-04-16
Seriously need help on this.

---

### Post by Zortis on 2011-04-16
I now get 'BOOTMGR is missing'.

The only fixes I can find for that involve the Windows 7 CD, which I don't have.

---

### Post by Zortis on 2011-04-16
BOOTMGR is missing.

After making my Ubuntu partition larger and my Windows 7 partition smaller.

Apparently you can change the grub config file to look at another partition (or something like that).

The only problem is the only file my Grub folder has in is 'grubenv'.

---

### Post by kiyop on 2011-04-16
Boot with bootable USB and open terminal and type:
```
sudo su
```and if you are asked to type password, enter password.

The end of prompt will change to "#" if success.

Then, open this page with FireFox and copy the following:
```
dd if=/dev/sda bs=512 count=1 skip=$(fdisk -lu|grep /dev/sda2 2>/dev/null|tr -s " "|cut -d " " -f 3)|hd
dd if=/dev/sda bs=512 count=1 skip=$(fdisk -lu|grep /dev/sda2 2>/dev/null|tr -s " "|cut -d " " -f 4)|hd
```On terminal, right-click and select "Paste".
Press enter key and copy all the contents in terminal window and paste in this "Reply" "Message" column and submit reply.

---

### Post by kiyop on 2011-04-16
You had not made ["System Repair Disk"]("http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc") when you could boot Windows 7, had you?

---

### Post by Zortis on 2011-04-16
ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# dd if=/dev/sda bs=512 count=1 skip=$(fdisk -lu|grep /dev/sda2 2>/dev/null|tr -s " "|cut -d " " -f 3)|hd
1+0 records in
1+0 records out
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
512 bytes (512 B) copied00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 68 16 0e  |........?....h..|
, 7.8507e-05 s, 6.5 MB/s
00000020  00 00 00 00 80 00 80 00  f8 f7 3d 49 00 00 00 00  |..........=I....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  58 c7 b3 54 f4 b3 54 64  |........X..T..Td|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200
root@ubuntu:/home/ubuntu# dd if=/dev/sda bs=512 count=1 skip=$(fdisk -lu|grep /dev/sda2 2>/dev/null|tr -s " "|cut -d " " -f 4)|hd

---

### Post by Zortis on 2011-04-16
> You had not made ["System Repair Disk"]("http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc") when you could boot Windows 7, had you?

Nope :(

Is it possible that my computer is trying to still boot from /dev/sda1 while /dev/sda1/ no longer exists?

---

### Post by kiyop on 2011-04-16
Thanks for your reply, but please copy the following:
```
dd if=/dev/sda bs=512 count=1 skip=$(fdisk -lu|grep /dev/sda2|tr -s " "|cut -d " " -f 4) 2>/dev/null|hd
```
 and paste into terminal and push enter key and copy & paste all the result into "Reply Message" and submit.
I quess that the location (discrepancy) of first sector of Bootmgr from the PBR of /dev/sda2 was changed when you resize /dev/sda2, so, Bootmgr could not be found and PBR gives "Bootmgr is missing"

By googling, you may be able to download "Windows7 System Repair Disk". But I cannot say "it is safe to use the downloaded file" at all.

Now I cannot access to Windows 7 PC, so I cannot analyze the structure of PBR of Windwos 7 system partition.
I will analyze next week.

---

### Post by kiyop on 2011-04-16
> **Zortis said:**
> Nope :(

Is it possible that my computer is trying to still boot from /dev/sda1 while /dev/sda1/ no longer exists?
I think it is very difficult to boot. Maybe allmost impossible.
But I hope there is a way.
I guess that /dev/sda1 was system (boot) partition with "Boot" folder, "Bootmgr" and "BCD" and that /dev/sda2 conatains almost all contents of Windows 7.

---

### Post by Zortis on 2011-04-16
root@ubuntu:/home/ubuntu# dd if=/dev/sda bs=512 count=1 skip=$(fdisk -lu|grep /dev/sda2|tr -s " "|cut -d " " -f 4) 2>/dev/null|hd
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200

---

### Post by kiyop on 2011-04-16
> **Zortis said:**
> root@ubuntu:/home/ubuntu# dd if=/dev/sda bs=512 count=1 skip=$(fdisk -lu|grep /dev/sda2|tr -s " "|cut -d " " -f 4) 2>/dev/null|hd
00000000  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200
Thanks for submitting the result.
But, unfortunately, backup boot sector located at the end of NTFS partition seems not to have been prepared.

One thing seems strange is that /dev/sda3 is NTFS.

You mentioned that you copied your Ubuntu (10GB) partition to newly created 100GB partition on Gparted.

What was the filesystem of copied Ubuntu partition? NTFS? EXT2/3/4?

If it was not NTFS, the copy might have failed.

I want to know the contents of /dev/sda3 and /dev/sda2.

Boot with bootable USB and click "Places" and find /dev/sda2 and /dev/sda3 and click to open.

If file manager (nautilus) opens, find if there is the following.
Windows folder (directory)
Boot folder
BCD (maybe in Boot)

---

### Post by Zortis on 2011-04-16
/dev/sda2 is Windows and /dev/sda3 is 'System' (Ubuntu).

I'm pretty sure that the original Ubuntu partition was NTFS.

---

### Post by kiyop on 2011-04-16
Thanks for reply.
Please relax.
The problem is easy to be solved.
I will write later.

The label of /dev/sda2 is "Windows" and  /dev/sda2 is mounted on /media/Windows.
/dev/sda2 contains Windows folder, bootmgr, and ubuntu folder, wubildr, wubildr.mbr.
ubuntu seems to be  installed via [Wubi]("http://ubuntuforums.org/showthread.php?t=1639198") on /dev/sda2.

The label of /dev/sda3 is system and /dev/sda3 is mounted on /media/system.
/dev/sda3 contains Boot folder which may contains BCD.

So, you can "bootrec /fixmbr" and "bootrec /fixboot" to fix if you have only "System Repair Disk".

I hope and guess that your try to copy the Ubuntu partition failed.
If you tried to copy NTFS partition (with Wubi-installed ubuntu) with Gparted, please let me know.

---

### Post by Zortis on 2011-04-16
I hope so - I'm worried that this can't be solved.

Any other suggestions from other users are welcome - I'm desperate.

---

### Post by kiyop on 2011-04-16
Excuse me, 
> **Zortis said:**
> /dev/sda2 is Windows and /dev/sda3 is 'System' (Ubuntu).

I'm pretty sure that the original Ubuntu partition was NTFS.
I am confused.

You might have misunderstood what you were doing.
If /dev/sda2 is copied one, it is difficult to repair, maybe.

---

### Post by Zortis on 2011-04-16
Originally /dev/sda1 was Ubuntu and /dev/sda2 was Windows. Then /dev/sda3 was created and /dev/sda1 was copied to /dev/sda3 and after copying /dev/sda1 was deleted so now left with /dev/sda2 as Windows and /dev/sda3 as the copied Ubuntu.

---

### Post by kiyop on 2011-04-16
Thanks for your explanation.

I guess that you expanded /dev/sda3 to empty (former /dev/sda1) place after /dev/sda1 was deleted, did not you?

---

### Post by Zortis on 2011-04-16
Yes!

---

### Post by oldfred on 2011-04-16
Post this to see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.


You need to have a windows repair CD:

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by kiyop on 2011-04-16
<<Edited at 00:14 in Japan>>
Booting with  "System Repair Disc" which is downloadable at 
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
and executing "bootrec /fixmbr" and "bootrec /fixboot" seems easier.

<<Edited at 00:20 in Japan>>
I rewrote to correct some mistake.
[COLOR=gray]
I suggest you to backup MBR and PBR's and install grub4dos or some boot loader into MBR and chainload to /dev/sda2.

The way is as follows:

1) Boot with bootable USB.

2) Open terminal.

3) Open this page with FireFox.

<Backup MBR and PBR's>
4) Execute the following in terminal:
```
sudo mount -t ntfs-3g /dev/sda2 /mnt -o rw
```and 
```
sudo dd if=/dev/sda bs=512 count=63 of=/mnt/sdambr
sudo dd if=/dev/sda2 bs=512 count=63 of=/mnt/sda2pbr
sudo dd if=/dev/sda3 bs=512 count=63 of=/mnt/sda3pbr
sudo umount -l /mnt
```<Download Grub4dos-0.4.4>
5) Open FireFox and download grub4dos-0.4.4.zip at:
[http://sourceforge.net/projects/grub4dos/](http://sourceforge.net/projects/grub4dos/)
and right-click the downloaded file and uncompress it to generate directory "grub4dos-0.4.4"

<Change directory to uncompressed grub4dos-0.4.4 directory with command "cd">
6) Typie (copy and paste) the following in terminal:
```
cd download/grub4dos-0.4.4
```<Copy necessary files into /dev/sda3>
7) type (copy and paste) the following in terminal:
```
sudo mount -t ntfs-3g /dev/sda3 /mnt -o rw
sudo cp -a grldr grub.exe menu.lst /mnt/
```<Install Grub4dos-0.4.4 into MBR>
8) type (copy and paste) the following in terminal:
```
sudo ./bootlace.com /dev/sda
```<Modify menu.lst in /dev/sda3 to boot /dev/sda2 Windows7>
9) type (copy and paste) the following in terminal:
```
sudo su
echo >> /mnt/menu.lst <<EOF 
title chainload to bootmgr on /dev/sda2
root (hd0,1)
chainloader /bootmgr
EOF
```10) Reboot and remove bootable USB.

11) If "GRUB4DOS" is displayed, use down key to select "chainload to bootmgr on /dev/sda2"
[/COLOR]

---

### Post by Zortis on 2011-04-16
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdf

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdf1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdf1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *    236,349,440 1,465,147,391 1,228,797,952   7 HPFS/NTFS
/dev/sda3               2,048   236,349,439   236,347,392   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 2051 MB, 2051014656 bytes
64 heads, 62 sectors/track, 1009 cylinders, total 4005888 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             62     4,003,711     4,003,650   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       96721a91-e38d-4984-a57e-bd9308295dd7   ext4                                     
/dev/sda2        6454B3F454B3C758                       ntfs       Windows                       
/dev/sda3        D074B29174B27A34                       ntfs       System                        
/dev/sda: PTTYPE="dos" 
/dev/sdf1        25A9-4F9F                              vfat       PENDRIVE                      
/dev/sdf: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdf1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/System            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


======================== sda2/Wubi/boot/grub/grub.cfg: ========================

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
}

if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-25-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6454b3f454b3c758
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, Linux 2.6.35-25-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6454b3f454b3c758
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-25-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-25-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6454b3f454b3c758
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 6454b3f454b3c758
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d074b29174b27a34
    chainloader +1
}
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

============================= sda2/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda2/Wubi: Location of files loaded by Grub: =================


    .4GB: boot/grub/grub.cfg
   2.1GB: boot/initrd.img-2.6.35-22-generic
   1.6GB: boot/initrd.img-2.6.35-25-generic
   1.6GB: boot/vmlinuz-2.6.35-22-generic
    .3GB: boot/vmlinuz-2.6.35-25-generic
   1.6GB: initrd.img
   2.1GB: initrd.img.old
    .3GB: vmlinuz
   1.6GB: vmlinuz.old

=========================== sdf1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdf1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdf1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3e 00 40 00 00 00 00 00  |........>.@.....|
00000020  42 17 3d 00 40 0f 00 00  00 00 00 00 02 00 00 00  |B.=.@...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 9f 4f a9 25 20  20 20 20 20 20 20 20 20  |..).O.%         |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 a8  1e 00 00 66 ba 00 00 00  |..E}.f.....f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

```
sdb sdc sdd sde

---

### Post by Zortis on 2011-04-16
I'll try Kiyop's suggestion now.

---

### Post by kiyop on 2011-04-16
> **oldfred said:**
> If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
...
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Thanks oldfred.

That will repair.

---

### Post by kiyop on 2011-04-16
> **Zortis said:**
> I'll try Kiyop's suggestion now.
No! No!
You should use Windows Repair Disc. It is easier, I think.

---

### Post by Zortis on 2011-04-16
Is it at all possible to use the Windows 7 recovery disc as a USB? I don't actually have an empty disc at the moment.

---

### Post by kiyop on 2011-04-16
> **Zortis said:**
> Is it at all possible to use the Windows 7 recovery disc as a USB? I don't actually have an empty disc at the moment.
I am not sure.

If you prefer, you can look [#25]("http://ubuntuforums.org/showthread.php?p=10683533#post10683533") again. I have rewritten to correct my mistake at 00:20 in Japan.

---

### Post by oldfred on 2011-04-16
I was not able to create windows repair USB from Ubuntu with any of the usual tools. I ended up creating one by burning a CD and then using the CD to copy itself to the USB following windows instructions. 

I do not remember exact commands:

Create Windows 7 USB
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
[http://technet.microsoft.com/en-us/magazine/dd535816.aspx](http://technet.microsoft.com/en-us/magazine/dd535816.aspx)
[http://store.microsoft.com/Help/ISO-Tool](http://store.microsoft.com/Help/ISO-Tool)
[http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/](http://www.intowindows.com/how-to-install-windows-7vista-from-usb-drive-detailed-100-working-guide/)
Repair USBs
Post #25 w/pendrive yumi
[http://ubuntuforums.org/showthread.php?t=1711323](http://ubuntuforums.org/showthread.php?t=1711323)
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://mintywhite.com/windows-7/7maintenance/windows-wont-load-system-repair-disc-fix-pc/](http://mintywhite.com/windows-7/7maintenance/windows-wont-load-system-repair-disc-fix-pc/)

---

### Post by Zortis on 2011-04-16
bash: cd: download/grub4dos-0.4.4: No such file or directory

I'll keep trying with this until I can get my hands on a blank CD/DVD.

---

### Post by Zortis on 2011-04-16
Tried Kiyop's solution but it only prompted me to use a Windows repair CD - Hopefully this will fix things.

---

### Post by Zortis on 2011-04-16
Is it possible to undo all changes made by the code in post #25?

I now have a Windows 7 repair CD but after repairing the computer will only boot with grub.

---

### Post by oldfred on 2011-04-16
It looks like your sda2 was missing /Boot/BCD. You do have one in sda3 but sda2 is the one with the boot flag so that is the one windows would repair. Did the win repair include  adding the missing BCD?

From command line. If you run auto repairs you have to run them 3 times and then it will probably overwrite grub in the MBR. You can reinstall grub after testing that it boots windows ok.

BootRec.exe /RebuildBcd

---

### Post by Zortis on 2011-04-16
The CD worked (Thank you), all of my data from Ubuntu has, however, been lost.

I'll re-install Ubuntu at a later date or on a different computer all together.

Thanks for your help guys.

---

### Post by kiyop on 2011-04-16
> **Zortis said:**
> Tried Kiyop's solution but it only prompted me to use a Windows repair CD - Hopefully this will fix things.Thanks for reporting my proposal (#25) did not solve the problem.
As oldfred wrote, /dev/sda2 did not have effective BCD file (BCD in /dev/sda3 may be modified to work, but it's over.)

Windows System Repair Disc solved the problem.
Thanks oldfred for variable help.

---

### Post by oldfred on 2011-04-17
Glad you got it working.

Are you sure all your Ubuntu data is lost? Windows will not see it, but it may still be there. You can check with liveCD to see if it is there. If you then reinstall grub2's boot loader to the MBR then you can dual boot.

---

