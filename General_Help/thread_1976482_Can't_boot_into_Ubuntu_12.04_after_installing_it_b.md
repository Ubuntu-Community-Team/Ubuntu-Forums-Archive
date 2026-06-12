---
title: "Can't boot into Ubuntu 12.04 after installing it beside windows 7"
date: 2012-05-08
forum: General Help
---

### Post by And21 on 2012-05-08
Hi,

this is my first time here, I've been using win7 for the past years but now I really wish to give Linux a try.

After struggling with this for a day I'm trying to get some tips here..

The problem is that after installing Ubuntu it goes straight into windows 7 and there's nothing I can do to start Ubuntu.

Further explanation here..

So I have a rather strong pc (8gb ram, 1 SSD for system files, 1 HDD for storage. I have windows 7 installed on the SSD, and I want to install Ubuntu on this same SSD.
First I had to "shrink" that drive inside windows. This had some issues, but with various defragmentation programs I could manage to do that.

I read and watched multiple tutorials on how to do the Ubuntu install, none of them worked so far (installing did, but I couldn't boot Ubuntu). Here's my experience:

- I booted up from the USB liveCD, I selected the first option (try ubuntu), then selected the unformatted free space (that remained after the "shrink" in windows), created a new partition on it (unformatted since it will be formatted with the installer).

- After the partition for Ubuntu is ready the system looks like this: sda1 and sda2 are for windows (the latter is just a 100mb something for booting) sda3 is the newly created partition for Ubuntu.

- I select install ubuntu on the desktop, where I have 3 options:
1. install ubuntu alongside win 7: this won't let me select the SSD drive for the install, only the HDD storage, which is not where I want to install Ubuntu on.
2. replace windows: this is not what I want
3. something else: so I go with this, and select sda3 where I set ext4 format, "/" as the mounting path, and "sda" for device for boot loater. For this last option I set sda3 in the few early tries, which didn't work, but I read it should be "sda" (which contains sda1,2,3) so that GRUB can run.

- Installing completes nicely, prompts for a needed restart, I say ok.

- Just before booting I plug the USB out, because otherwise it boots from there and I can just go to the "free run" of ubuntu but not the actual OS I installed.

- And finally Windows 7 start automatically, no selection screen whatsoever.


I know that probably the best option would be to make a clean install of both Windows and Ubuntu, but I can't do that now.
I also tried to launch wubi, but I couldn't figure out how that worked (it just seemed to advice me for restarting with a live cd).
I did error checking on my disks, nothing seemed to be wrong.

I read lots of tips about updating GRUB or whatever, but I can't even get to my Ubuntu install so I have no chance of accessing any of that.

One addition that might have nothing to do with it: I select no swapping partition since I have an SSD and 8GB of ram. This gives me a warning but I can proceed.

Can anyone help me what else is there for me to try? 
I have a feeling the issue can be connected with the fact that I can't select the SSD when going with the first install option (install Ubuntu alongside windows 7)..

Really appreciated.

Andrew

---

### Post by vegarend on 2012-05-08
Not sure I get all the details, did you only specify '/'? What might be helpful is if you boot from USB again, follow installation until disk partitioning, and post the partitioning/configuration you see now.

---

### Post by wilee-nilee on 2012-05-08
Download this link and extract and it to your desktop, using a live Ubuntu cd or usb. Run the command in the terminal and post the results.txt that appears on the forum. When you post it click on the # in the reply window and put the all the text from the results.txt you will see, between the code tags.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

---

### Post by miasmablk on 2012-05-08
correct me if im wrong because i am unsure of this, but could the problem possibly be corrected using windows 7 boot recovery > cmd > then bootrec /fixmbr ?

---

### Post by wilee-nilee on 2012-05-08
> **miasmablk said:**
> correct me if im wrong because i am unsure of this, but could the problem possibly be corrected using windows 7 boot recovery > cmd > then bootrec /fixmbr ?

Possibly, but even though my nic is wilee-nilee I want exact information before I give advice. Do no harm is the ideal I live by. :)

---

### Post by swright007 on 2012-05-08
If it is just a matter of fixing the MBR, you can always boot from a live CD or Boot flash drive of Ubuntu, open a terminal, and issue the command 

sudo update-grub

---

### Post by wilee-nilee on 2012-05-08
> **swright007 said:**
> If it is just a matter of fixing the MBR, you can always boot from a live CD or Boot flash drive of Ubuntu, open a terminal, and issue the command 

sudo update-grub


This command is useless on the live cd unless you are chrooted in, nor does it reload the mbr.

All it takes is a syntax error on a post to give the wrong impression of  what the thread starter wants or has. There is evidence of this. If the sda  SSD has only 2 ntfs partitions and a ext4 for Ubuntu the third on it, Ubuntu would install there  easily.

To be honest there are enough loose strings in the thread post for me to want to see the whole setup. :)

---

### Post by oldfred on 2012-05-09
+1 on    	wilee-nilee's wanting to see boot info scripts output.

Too often users do not know the details and while we can guess and sometimes be correct, it is better to be sure.

I think the grub just got installed to a different drive or USB?, but with script output we will know for sure.

---

### Post by Moo321 on 2012-05-09
I have the same problem, I install ubuntu 12.04, i have windows 7, but when i try to get in i can't, grub doesn't appear, anyone know what's the problem?

---

### Post by wilee-nilee on 2012-05-09
> **Moo321 said:**
> I have the same problem, I install ubuntu 12.04, i have windows 7, but when i try to get in i can't, grub doesn't appear, anyone know what's the problem?

Start your own thread and follow the instructions on making a bootscript above and post it. Hardly ever are these problems identical, so individual threads just make this easier. Feel free to pm me if you get a thread made. :)

---

### Post by And21 on 2012-05-09
Wow, I didn't expect this many answers in such a short time, thankt to all of you!

Yes, for mount point on the partition (/dev/sda3) I only specified "/", according to multiple tutorials I read. Is this wrong ?

---

### Post by wilee-nilee on 2012-05-09
> **And21 said:**
> Wow, I didn't expect this many answers in such a short time, thankt to all of you!

Yes, for mount point on the partition (/dev/sda3) I only specified "/", according to multiple tutorials I read. Is this wrong ?

Can you post the bootscript, post 3, this script is a debugging tool that will separate the wheat from the chaffe. :)

---

### Post by drtheradio on 2012-05-09
OK 

Boot off the LIVE CD .


Terminal

sudo install -d /mnt/rad                                  

sudo mnt /dev/sda3        /mnt/rad                          

sudo grub-install --root-directory=/mnt/rad /dev/sda 
      ok i looked this is it

then you boot linux
and 
RUN
sudo update-grub   in terminal

works all the time for me...

---

### Post by And21 on 2012-05-09
> **wilee-nilee said:**
> Download this link and extract and it to your desktop, using a live Ubuntu cd or usb. Run the command in the terminal and post the results.txt that appears on the forum. When you post it click on the # in the reply window and put the all the text from the results.txt you will see, between the code tags.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```

Ok so I ran that, it gave: "gawk" could not be found, using "busybox awk", this may lead to unreliable results), so I can try to download that as well if you need me to.

Here is the results.txt:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /ubuntu/winboot/wubildr 
                       /ubuntu/winboot/wubildr.mbr

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre1
    Boot sector info:  Syslinux looks at sector 30502 of /dev/sdc1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 96.0 GB, 96029466624 bytes
255 heads, 63 sectors/track, 11674 cylinders, total 187557552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   135,757,823   135,550,976   7 NTFS / exFAT / HPFS
/dev/sda3         135,757,824   187,555,839    51,798,016  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 3,907,026,943 3,907,024,896   7 NTFS / exFAT / HPFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 4008 MB, 4008706048 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7829504 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *             63     7,829,503     7,829,441   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CEB615AEB6159853                       ntfs       System Reserved
/dev/sda2        4EA017D3A017C07F                       ntfs       
/dev/sda3        2505da00-caf1-4925-84c7-903d50c477d4   ext4       
/dev/sdb1        AEA49EAEA49E7913                       ntfs       andris2tb
/dev/sdc1        1A09-3216                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root 2505da00-caf1-4925-84c7-903d50c477d4
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root 2505da00-caf1-4925-84c7-903d50c477d4
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="$1"
	if [ "$1" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 2505da00-caf1-4925-84c7-903d50c477d4
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=2505da00-caf1-4925-84c7-903d50c477d4 ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 2505da00-caf1-4925-84c7-903d50c477d4
	echo	'Loading Linux 3.2.0-23-generic ...'
	linux	/boot/vmlinuz-3.2.0-23-generic root=UUID=2505da00-caf1-4925-84c7-903d50c477d4 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 2505da00-caf1-4925-84c7-903d50c477d4
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos3)'
	search --no-floppy --fs-uuid --set=root 2505da00-caf1-4925-84c7-903d50c477d4
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root CEB615AEB6159853
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
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=2505da00-caf1-4925-84c7-903d50c477d4 /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

=========================== sdc1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

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
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdc1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdc1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdc1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdc1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
/home/ubuntu/Desktop/bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected


```

---

### Post by wilee-nilee on 2012-05-09
> **drtheradio said:**
> OK 

Boot off the LIVE CD .

sudo fdisk -l
look for  what  /dev/sda1 2 or 3> is it  hda ????  sda1  hda1 mabe

Teminal

sudo install -d /mnt/rad                                  

sudo mnt /dev/????        /mnt/rad                          

sudo grub-install --root-directory=/mnt/rad /dev/sda   or mabe sdb , hda Fdisk tells you.      <<<<this is you device NO NUMBER.


hope this helps

That is all garbage please do not do that.

---

### Post by drtheradio on 2012-05-09
I fixed it

that works ..... I have use it more than a few times.

there are longer ways to go about doing the same thing.

It was all messy...

---

### Post by wilee-nilee on 2012-05-09
So your missing this from the ubuntu in the sda3

```
/boot/grub/core.img
```And grub is missing from the MBR which is sda no numbers.

So boot the live ubuntu cd use this link to chroot to the Ubuntu install and run these commands. We are purging the grub you have and reinstalling, and loading the bootloader to the mbr

[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

Once you're chrooted in run these.

```
apt-get purge grub-pc grub-common
```Then run

```
apt-get install grub-pc grub-common 
```Then

```
grub-install /dev/sda
```When asked where grub goes choose sda and use the space key to tick sda then enter.

Then 

```
update-grub
```Unmount the chroot and reboot, and run this command in the Ubuntu install once in.

```
sudo update-grub
```

---

### Post by wilee-nilee on 2012-05-09
> **drtheradio said:**
> I fixed it

that works ..... I have use it more than a few times.

there are longer ways to go about doing the same thing.

It was all messy...

Support threads are not for argument's. At the least you should have posted a link to a grub 2 wiki like the one above, and really should have waited till the person posted the bootscript. 

No biggie but we try to help, not just post cause it feels like we should with inaccurate commands. Which by the way if you look would not have fixed this problem. I recognized your commands they are on this wiki, but yours are mangled and confusing. :)

---

### Post by And21 on 2012-05-09
> **wilee-nilee said:**
> So your missing this from the ubuntu in the sda3

```
/boot/grub/core.img
```And grub is missing from the MBR which is sda no numbers.

So boot the live ubuntu cd use this link to chroot to the Ubuntu install and run these commands. We are purging the grub you have and reinstalling, and loading the bootloader to the mbr

[https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

Once you're chrooted in run these.

```
apt-get purge grub-pc grub-common
```Then run

```
apt-get install grub-pc grub-common 
```Then

```
grub-install /dev/sda
```When asked where grub goes choose sda and use the space key to tick sda then enter.

Then 

```
update-grub
```Reboot to the grub menu it should show Ubuntu boot in and run this in the Ubuntu install.

```
sudo update-grub
```


I'm not 100% sure about how to do the chroot part, because it has some points (software raid, critical virtual filesystems) of which I have no idea about...

So to sum up, in case I have sda1, sda2 for win 7, sda3 for ubuntu, are these the commands I have to type into terminal?

```

sudo mount /dev/sda3 /mnt
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done (I'm really not sure what this does and hope it wouldn't mess up the windows part of my drive)

sudo chroot /mnt

sudo mount /dev/sda3 /boot ( although I guess this is not needed because I dont have a separate boot partition right?)

update-grub

grub-install /dev/sda

grub-install --recheck /dev/sda

CTRL-D
reboot

and now run the command that you gave me (although some of it seem to have already been done with this chroot)

Is this correct?


```

---

### Post by wilee-nilee on 2012-05-09
Try this part of the link it gives clearer instructions on the chroot and the grub purge and reinstall and the dis-mount of the chroot to the reboot.

[https://help.ubuntu.com/community/Grub2#Purge_.26_Reinstall](https://help.ubuntu.com/community/Grub2#Purge_.26_Reinstall)

I neglected to give you a heads up on the unmount from the chroot, rather then just rebooting from the last command I gave you. Read carefully you will figure it out.

Worse case here you can just reinstall to that sda3 partition choosing   the something other option at the gui of where you want to install   Ubuntu on the live cd install. In the something other option use the   drop down to point grub at sda only not a partition. Then click change   for sda3 set the mount as / and tick the partition box choose the ext4  in the dropdown there and install.

Since this is a fresh install this might be a easier way to go.

---

### Post by And21 on 2012-05-09
> **wilee-nilee said:**
> Try this part of the link it gives clearer instructions on the chroot and the grub purge and reinstall and the dis-mount of the chroot to the reboot.

[https://help.ubuntu.com/community/Grub2#Purge_.26_Reinstall](https://help.ubuntu.com/community/Grub2#Purge_.26_Reinstall)

I neglected to give you a heads up on the unmount from the chroot, rather then just rebooting from the last command I gave you. Read carefully you will figure it out.

Worse case here you can just reinstall to that sda3 partition choosing the something other option at the gui of where you want to install Ubuntu on the live cd install. In the something other option use the drop down to point grub at sda only not a partition. Then click change for sda3 set the mount as / and tick the partition box and install.

Since this is a fresh install this might be a easier way to go.

Yes reinstalling is not a problem so I'd prefer that. But that's what not working ... I pick the 3rd option (which is my only option really, since the first doesn't let me select the SSD only the hdd drive that I use for storage only - and by the way why is this? I think this can be the root of the problem),
and there I set "sda" for "device for boot loader install", set "sda3" to format and mount as "/" and install. This is what I tried at least 5 times yesterday and the grub didn't show up. For some reason looks like the ubuntu installer cant seem to "write" into the master boot record to enable grub

---

### Post by wilee-nilee on 2012-05-09
> **And21 said:**
> Yes reinstalling is not a problem so I'd prefer that. But that's what not working ... I pick the 3rd option (which is my only option really, since the first doesn't let me select the SSD only the hdd drive that I use for storage only - and by the way why is this? I think this can be the root of the problem),
and there I set "sda" for "device for boot loader install", set "sda3" to format and mount as "/" and install. This is what I tried at least 5 times yesterday and the grub didn't show up. For some reason looks like the ubuntu installer cant seem to "write" into the master boot record to enable grub

You have Ubuntu on the sda drive this is the SSD isn't it?

I am not sure why the missing files you should have in the sda3 partition are actually in the sdc. It may be that the sdc is supposed to have them I see a boot set of files that looks like a multiload usb set up.

---

### Post by And21 on 2012-05-09
> **wilee-nilee said:**
> You have Ubuntu on the sda drive this is the SSD isn't it?

I am not sure why the missing files you should have in the sda3 partition are actually in the sdc. It may be that the sdc is supposed to have them I see a boot set of files that looks like a multiload usb set up.

Yes, sda is my "c" drive, the SSD that has sda1 and sda2 for windows 7 purposes (one of them being just a 100mb partition that windows created), sda3 is a 25GB partition formatted with GParted for installing Ubuntu.

sdb is the 2TB HDD that I use for storage. Nothing there just movies, etc.

sdc is the pendrive that I use as the live cd to install ubuntu.
Maybe I should try deploying the livecd to the usb again because something went wrong there?

But I think it's really about why I can't select my SSD as the drive when selecting "install ubuntu alongside windows" (aka the first option)...it's really strange why only the 2TB storage is shown there...

---

### Post by wilee-nilee on 2012-05-09
> **And21 said:**
> Yes, sda is my "c" drive, the SSD that has sda1 and sda2 for windows 7 purposes (one of them being just a 100mb partition that windows created), sda3 is a 25GB partition formatted with GParted for installing Ubuntu.

sdb is the 2TB HDD that I use for storage. Nothing there just movies, etc.

sdc is the pendrive that I use as the live cd to install ubuntu.
Maybe I should try deploying the livecd to the usb again because something went wrong there?

But I think it's really about why I can't select my SSD as the drive when selecting "install ubuntu alongside windows" (aka the first option)...it's really strange why only the 2TB storage is shown there...

You are installed in the SSD drive, if you choose to install along side you have no free space unallocated. You need to use the something other option at the bottom of those choices and follow my comments I have already posted on installing from there.

From post #20

> Worse case here you can just reinstall to that sda3 partition choosing  the something other option at the gui of where you want to install  Ubuntu on the live cd install. In the something other option use the  drop down to point grub at sda only not a partition. Then click change  for sda3 set the mount as / and tick the partition box choose the ext4 in the dropdown there and install.I think you have gotten stuck in not understand that a custom install using that sda3 already formatted is the way to go. 

I have not used the install along side in like 3 years maybe, it used to have a sliding bar to resize the partitions to leave a unallocated space for the install. Problem is a auto install like this on your set up will make 4 primary partitions and a swap 5 altogether if you had shrunk the sda3. Four is the limit on a single HD. It would make another ext4 and a swap this would turn your HD dynamic, Ubuntu will not do this unless forced.

I have to crash I hope this is understandable, use the something other option as my quote describes I think you will be set then.

It has been user error that has kept you from getting a good install I think. :)

There is also the option of opening gparted on the live cd and deleting sda3 and then close gparted and hit install, and choose the alongside again. I think you got it in the SSD the first time you tried, but each consecutive retry without removing the sda3 was a fail due to the 4 partition limit.

I added the choose the ext4 in the quote as it seems that you have not done this before so a exact set of instructions is important, no biggie I just want you installed and happy. :)

---

### Post by And21 on 2012-05-09
> **wilee-nilee said:**
> You are installed in the SSD drive, if you choose to install along side you have no free space unallocated. You need to use the something other option at the bottom of those choices and follow my comments I have already posted on installing from there.

From post #20

I think you have gotten stuck in not understand that a custom install using that sda3 already formatted is the way to go. 

I have not used the install along side in like 3 years maybe, it used to have a sliding bar to resize the partitions to leave a unallocated space for the install. Problem is a auto install like this on your set up will make 4 primary partitions and a swap 5 altogether if you had shrunk the sda3. Four is the limit on a single HD. It would make another ext4 and a swap this would turn your HD dynamic, Ubuntu will not do this unless forced.

I have to crash I hope this is understandable, use the something other option as my quote describes I think you will be set then.

It has been user error that has kept you from getting a good install I think. :)

There is also the option of opening gparted on the live cd and deleting sda3 and then close gparted and hit install, and choose the alongside again. I think you got it in the SSD the first time you tried, but each consecutive retry without removing the sda3 was a fail due to the 4 partition limit.

I added the choose the ext4 in the quote as it seems that you have not done this before so a exact set of instructions is important, no biggie I just want you installed and happy. :)

I think I didnt express myself well, or maybe I still misunderstand something, but:
so since the first option did not include my ssd, I went with the 3rd option all the time! And prior to that here's what I did:
I created a new partition on that unallocated space set it's format to unformatted (because in one of the tutorials I read it will be set to ext4 by the installer).

You were right that if I delete the partition in gparted (leaving an unallocated space) I will be able to choose "install alongside", this now I tried though and it resulted in the same (booted right into win7). (And yes you were right it now resulted in 5 partition, under sda3 (which is now extended I have sda5 ext 4 and sda6 linux-swap).

To really avoid any confusing I'm gonna try another install, describing everything I do along the way:
(now I have an install that doesnt boot, so I start by removing that)
1. open gparted, swapoff sda6 (to be able to delete), delete sda3,5,6. Result I have sda1,2 in ntfs for windows and 24.7 GiB unallocated (and 2TB hdd for sdb but that doesnt matter)

2. create the partition: in gparted I click with right on the unallocated space, select new:
primary,
ext4,
label: Ubuntu,
free space following, preceding: 0
new size: 25293 (default value,its the max I guess)
-> click on add

3. click on install -> english -> continue -> didnt select to download updates and third party -> continue -> choose the third option ("something else")

4. Here click on sda3, change -> use as: ext4 journaling, format: yes, mount point: "/"

5. same screen: set "device for boot loader after installation:" to "/dev/sda"

6. Prompt saying I havent selected swap partition -> continue 

7. I set my location, keyboard, user pass during the installation, I don't wish to import setting from win 7.

8. Installation finishes, prompts for a restart 

9. after the screen goes black before booting I plug out the USB so that it wont boot from there

10. Win 7 starts.

The next thing I'll try is to leave unallocated inside gparted, and make the partition from within the installer, but I think that wont make a difference.

---

### Post by oldfred on 2012-05-09
Your install procedure looks correct. Is that with only the SSD installed? Sometimes BIOS promotes a flash drive to sda, so then you end up installing grub to the flash drive.

Also a few BIOS have locked the MBR write process for security. 

BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS

---

### Post by And21 on 2012-05-09
> **oldfred said:**
> Your install procedure looks correct. Is that with only the SSD installed? Sometimes BIOS promotes a flash drive to sda, so then you end up installing grub to the flash drive.

Also a few BIOS have locked the MBR write process for security. 

BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS

I'll try it with the HDD as well, to see if it makes any difference. 

My motherboard is "Asrock Z68 Pro 3", it has a UEFI bios.

I tried to see for your suggestions, but the only options I see are:
- setup prompt timeout: 1
- boot numlok: on
- pci rom priority: legacy rom
- full screen logo: enabled
- addonromdisplay: enabled
- boot from onboard land: disabled
- boot failure guard: enabled
- boot failure guard count: 3

Checked the advanced tab as well..

Should I try with something like "Boot Repair" from the live cd ? Or EasyBCD from within windows? 
Or I could manually type commands to restore grub as advised to me by "wilee-nilee" but I'm a bit afraid of that to be honest.

---

### Post by oldfred on 2012-05-09
Your installs are in BIOS mode, so UEFI should not matter.

Boot-Repair should work, but sometimes you need advanced settings and I do not know all those. I think trying the recommended is worth doing.

If not the full chroot repair as suggested wilee-nilee should also work. The only issue with chroot would be is if you do not have Internet if will not be able to reinstall grub2. Otherwise it should also just work.

---

### Post by wilee-nilee on 2012-05-09
> **oldfred said:**
> Your installs are in BIOS mode, so UEFI should not matter.

Boot-Repair should work, but sometimes you need advanced settings and I do not know all those. I think trying the recommended is worth doing.

If not the full chroot repair as suggested wilee-nilee should also work. The only issue with chroot would be is if you do not have Internet if will not be able to reinstall grub2. Otherwise it should also just work.

I checked out the boot repair last week or so the advanced allows you to choose the grub placement like a custom install basically. I have the bootrepair cd on my multiload thumb, I will check it out closer and take some screen shots.

Thanks for your help always oldfred. :)

---

### Post by And21 on 2012-05-09
> **wilee-nilee said:**
> I checked out the boot repair last week or so the advanced allows you to choose the grub placement like a custom install basically. I have the bootrepair cd on my multiload thumb, I will check it out closer and take some screen shots.

Thanks for your help always oldfred. :)


Thanks to both of you I will try boot repair then, if not working then the chroot method. I ll wait with this till I save all my windows related work so I can be sure to not mess anything up. 

Argh it's so annoying though, what could have been the problem? Maybe the windows defragmentation programs messed something up, or I dunno..

---

### Post by And21 on 2012-05-10
> **And21 said:**
> Thanks to both of you I will try boot repair then, if not working then the chroot method. I ll wait with this till I save all my windows related work so I can be sure to not mess anything up. 

Argh it's so annoying though, what could have been the problem? Maybe the windows defragmentation programs messed something up, or I dunno..

Ok, this Boot Repair fixed it, now it goes to the GRUB os selector screen, thanks ! 

I know it's a different topic, but it would take me hours to figure out through trial and error so can I have a few more questions?

What is the easiest way to update for example nvidia drivers? Many tutorials say terminal commands..
The other problem is it didnt detect my second display. I found a gui way of setting this in nvidia panel on a tutorial but first I had to switch to "gnome classic" from "unity" to be able to reach those settings with the driver updates, then it complained about x server needing to be restarted which for I needed to do some other terminal commands.
This whole procedure just seems a bit cumbersome and I wonder if I'm doing something wrong. I really wish to switch to linux because I love its philosophy and its clean gui, safety, etc, but user friendliness could really be better I think - and I'm a developer working on computers for 6 years.

Also can you advise a good "theme" or "launcher" (not sure what its called exactly) that has a dock just like "unity" (but I prefer that on the bottom like on osx or windows) but with the more "advanced" settings panels. I mean currently the settings looks like on osx, just a few items to edit, and some tutorials point to locations like the above mentioned nvidia panel that seem to be inaccessible from unity.

Sorry I see it's a lot of questions and you already helped a lot..

---

### Post by oldfred on 2012-05-10
For the default nVidia, I use nomodeset on first boot. And then just install the default suggested driver. 

nVidia released a buggy version and just released the fix. It really only was a problem for some of the older 7 & 8 video cards.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

NVIDIA 295.49 Fixes Linux Performance Regression
[http://www.phoronix.com/scan.php?page=news_item&px=MTA5NjQ](http://www.phoronix.com/scan.php?page=news_item&px=MTA5NjQ)
Fixing the performance regression of the 295.40 driver that affected GeForce 6 and GeForce 7 series hardware. 

Warning for nVidia GeForce 6, 7, and 8800 cards with 12.04 Precise
[http://ubuntuforums.org/showthread.php?t=1969754](http://ubuntuforums.org/showthread.php?t=1969754)
serious issue with the GeForce 6, 7, and 8800 GTS/GTX cards, K/Ubuntu 12.04, and their latest 295.40 driver. 

I have only one monitor but have seen a fair number of threads on dual & triple monitors. You may want to search and see if they help or start a new thread.

I just use the fallback mode as it is almost gnome2. I have also seen a lot of posts of different configurations, but do not know details. 

Is Docky what you want?
[http://www.liberiangeek.net/2011/09/use-gnome-desktop-with-docky-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/09/use-gnome-desktop-with-docky-in-ubuntu-11-10-oneiric-ocelot/)

---

### Post by And21 on 2012-05-12
> **oldfred said:**
> For the default nVidia, I use nomodeset on first boot. And then just install the default suggested driver. 

nVidia released a buggy version and just released the fix. It really only was a problem for some of the older 7 & 8 video cards.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

NVIDIA 295.49 Fixes Linux Performance Regression
[http://www.phoronix.com/scan.php?page=news_item&px=MTA5NjQ](http://www.phoronix.com/scan.php?page=news_item&px=MTA5NjQ)
Fixing the performance regression of the 295.40 driver that affected GeForce 6 and GeForce 7 series hardware. 

Warning for nVidia GeForce 6, 7, and 8800 cards with 12.04 Precise
[http://ubuntuforums.org/showthread.php?t=1969754](http://ubuntuforums.org/showthread.php?t=1969754)
serious issue with the GeForce 6, 7, and 8800 GTS/GTX cards, K/Ubuntu 12.04, and their latest 295.40 driver. 

I have only one monitor but have seen a fair number of threads on dual & triple monitors. You may want to search and see if they help or start a new thread.

I just use the fallback mode as it is almost gnome2. I have also seen a lot of posts of different configurations, but do not know details. 

Is Docky what you want?
[http://www.liberiangeek.net/2011/09/use-gnome-desktop-with-docky-in-ubuntu-11-10-oneiric-ocelot/](http://www.liberiangeek.net/2011/09/use-gnome-desktop-with-docky-in-ubuntu-11-10-oneiric-ocelot/)

Thanks a lot! Ill check these out.

---

### Post by turbos4 on 2012-05-14
> **miasmablk said:**
> correct me if im wrong because i am unsure of this, but could the problem possibly be corrected using windows 7 boot recovery > cmd > then bootrec /fixmbr ?


Windows 7 will just create the same issu. How to fix windows 7 mbr boot.

win7 bootmbr are just booting Windows 7 and windows 2008 and windows 2008 r2.

Use Ubuntu livecd.

Download ms-sys

[http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

install it!

open terminal

#sudo su

#ms-sys -m /dev/sda (where '/dev/sda' is windows 7 bootmbr...

then install grub. This  work for me!

---

### Post by wilee-nilee on 2012-05-14
> **turbos4 said:**
> Windows 7 will just create the same issu. How to fix windows 7 mbr boot.

win7 bootmbr are just booting Windows 7 and windows 2008 and windows 2008 r2.

Use Ubuntu livecd.

Download ms-sys

[http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

install it!

open terminal

#sudo su

#ms-sys -m /dev/sda (where '/dev/sda' is windows 7 bootmbr...

then install grub. This  work for me!

Please read the thread this was fixed 3 days ago. ms-sys is also way out of date and not a good choice, :)

---

### Post by turbos4 on 2012-05-14
Why is it not markt as SOLVED?

I tryed the tread solution, but didn't work for me!

I don't know what i did wrong, but i got all sort of error after word.

So i used ms-sys. Mabye it's old, but work for me. Had now issu

---

### Post by wilee-nilee on 2012-05-14
> **turbos4 said:**
> Why is it not markt as SOLVED?

I tryed the tread solution, but didn't work for me!

I don't know what i did wrong, but i got all sort of error after word.

So i used ms-sys. Mabye it's old, but work for me. Had now issu

Some users forget to mark the thread as solved, all you have to do is read it to tell what is up. :)

---

### Post by legalaliens5 on 2012-09-07
I just installed 12.04 in a dual boot configuration, giving Ubuntu about 130 GB of space.
I installed on an INTEL 480 GB SSD.  Windows 7 is on the same SSD.
I created the following partiions:

/
/home
/boot

and a swap partition

The install seemed to go well and when I rebooted into WIndows, I downloaded EasyBCD and set up a new boot entry for Ubuntu 12.04.

Then I rebooted again, and this time I could choose either Win 7 or Ubuntu.

When I choose WIn 7, it works just fine.

When I choose Ubuntu, all I get is a GRUB prompt.

Here is the output of running the bootinfoscript:
                 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:
    Boot files:        /grub/grub.cfg

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:
    Boot files:

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 20110518
    Boot sector info:  Syslinux looks at sector 1462288 of /dev/sdb1 for its
                       second stage. SYSLINUX is installed in the  directory.
                       The integrity check of the ADV area failed. According
                       to the info in the boot sector, sdb1 starts at sector
                       0. But according to the info from fdisk, sdb1 starts
                       at sector 32.
    Operating System:
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 480.1 GB, 480103981056 bytes
255 heads, 63 sectors/track, 58369 cylinders, total 937703088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   671,090,687   670,883,840   7 NTFS / exFAT / HPFS
/dev/sda3         671,092,734   937,701,375   266,608,642   5 Extended
/dev/sda5         671,092,736   672,090,111       997,376  83 Linux
/dev/sda6         672,092,160   708,943,871    36,851,712  83 Linux
/dev/sda7         708,945,920   921,313,279   212,367,360  83 Linux
/dev/sda8         921,315,328   937,701,375    16,386,048  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 16.0 GB, 16022241280 bytes
64 heads, 32 sectors/track, 15280 cylinders, total 31293440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    31,293,439    31,293,408   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs
/dev/sda1        70BA29D7BA299A9C                       ntfs       System Reserved
/dev/sda2        FE962B2F962AE7BB                       ntfs
/dev/sda5        dcd01c75-ae35-4799-a834-9b08a983891c   ext4
/dev/sda6        541a032e-c8cd-4e5d-b653-32049a6b207e   ext4
/dev/sda7        871328e5-0f65-46b7-a851-a3143a859868   ext4
/dev/sda8        3264f780-de21-4fb1-9856-f77df511cda9   swap
/dev/sdb1        7E65-6D83                              vfat

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================= sda5/grub/grub.cfg: ==============================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 541a032e-c8cd-4e5d-b653-32049a6b207e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root dcd01c75-ae35-4799-a834-9b08a983891c
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
        set gfxpayload="$1"
        if [ "$1" = "keep" ]; then
                set vt_handoff=vt.handoff=7
        else
                set vt_handoff=
        fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos5)'
        search --no-floppy --fs-uuid --set=root dcd01c75-ae35-4799-a834-9b08a983891c
        linux   /vmlinuz-3.2.0-23-generic root=UUID=541a032e-c8cd-4e5d-b653-32049a6b207e ro   quiet splash $vt_handoff
        initrd  /initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos5)'
        search --no-floppy --fs-uuid --set=root dcd01c75-ae35-4799-a834-9b08a983891c
        echo    'Loading Linux 3.2.0-23-generic ...'
        linux   /vmlinuz-3.2.0-23-generic root=UUID=541a032e-c8cd-4e5d-b653-32049a6b207e ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos5)'
        search --no-floppy --fs-uuid --set=root dcd01c75-ae35-4799-a834-9b08a983891c
        linux16 /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos5)'
        search --no-floppy --fs-uuid --set=root dcd01c75-ae35-4799-a834-9b08a983891c
        linux16 /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set=root 70BA29D7BA299A9C
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
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/grub.cfg                                  1
               =                initrd.img-3.2.0-23-generic                    2
               =                vmlinuz-3.2.0-23-generic                       2

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=541a032e-c8cd-4e5d-b653-32049a6b207e /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=dcd01c75-ae35-4799-a834-9b08a983891c /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=871328e5-0f65-46b7-a851-a3143a859868 /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=3264f780-de21-4fb1-9856-f77df511cda9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

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
        linux   /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
        initrd  /casper/initrd.lz
}
menuentry "Install Ubuntu" {
        set gfxpayload=keep
        linux   /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
        initrd  /casper/initrd.lz
}
menuentry "Check disc for defects" {
        set gfxpayload=keep
        linux   /casper/vmlinuz  boot=casper integrity-check quiet splash --
        initrd  /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

Please help - I know I must be close...

Thanks

---

### Post by legalaliens5 on 2012-09-07
Sorry - does this work better?

```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________  ________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________  ________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________  ________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sda5: __________________________________________________  ________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:
    Boot files:        /grub/grub.cfg

sda6: __________________________________________________  ________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /etc/fstab

sda7: __________________________________________________  ________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:
    Boot files:

sda8: __________________________________________________  ________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

sdb1: __________________________________________________  ________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 20110518
    Boot sector info:  Syslinux looks at sector 1462288 of /dev/sdb1 for its
                       second stage. SYSLINUX is installed in the  directory.
                       The integrity check of the ADV area failed. According
                       to the info in the boot sector, sdb1 starts at sector
                       0. But according to the info from fdisk, sdb1 starts
                       at sector 32.
    Operating System:
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg
                       /efi/boot/bootx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda __________________________________________________  ___________________

Disk /dev/sda: 480.1 GB, 480103981056 bytes
255 heads, 63 sectors/track, 58369 cylinders, total 937703088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   671,090,687   670,883,840   7 NTFS / exFAT / HPFS
/dev/sda3         671,092,734   937,701,375   266,608,642   5 Extended
/dev/sda5         671,092,736   672,090,111       997,376  83 Linux
/dev/sda6         672,092,160   708,943,871    36,851,712  83 Linux
/dev/sda7         708,945,920   921,313,279   212,367,360  83 Linux
/dev/sda8         921,315,328   937,701,375    16,386,048  82 Linux swap / Solaris


Drive: sdb __________________________________________________  ___________________

Disk /dev/sdb: 16.0 GB, 16022241280 bytes
64 heads, 32 sectors/track, 15280 cylinders, total 31293440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32    31,293,439    31,293,408   c W95 FAT32 (LBA)


"blkid" output: __________________________________________________  ______________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs
/dev/sda1        70BA29D7BA299A9C                       ntfs       System Reserved
/dev/sda2        FE962B2F962AE7BB                       ntfs
/dev/sda5        dcd01c75-ae35-4799-a834-9b08a983891c   ext4
/dev/sda6        541a032e-c8cd-4e5d-b653-32049a6b207e   ext4
/dev/sda7        871328e5-0f65-46b7-a851-a3143a859868   ext4
/dev/sda8        3264f780-de21-4fb1-9856-f77df511cda9   swap
/dev/sdb1        7E65-6D83                              vfat

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat        (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,i   ocharset=iso8859-1,shortname=mixed,errors=remount-ro)


============================= sda5/grub/grub.cfg: ==============================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 541a032e-c8cd-4e5d-b653-32049a6b207e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root dcd01c75-ae35-4799-a834-9b08a983891c
  set locale_dir=($root)/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
        set gfxpayload="$1"
        if [ "$1" = "keep" ]; then
                set vt_handoff=vt.handoff=7
        else
                set vt_handoff=
        fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos5)'
        search --no-floppy --fs-uuid --set=root dcd01c75-ae35-4799-a834-9b08a983891c
        linux   /vmlinuz-3.2.0-23-generic root=UUID=541a032e-c8cd-4e5d-b653-32049a6b207e ro   quiet splash $vt_handoff
        initrd  /initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos5)'
        search --no-floppy --fs-uuid --set=root dcd01c75-ae35-4799-a834-9b08a983891c
        echo    'Loading Linux 3.2.0-23-generic ...'
        linux   /vmlinuz-3.2.0-23-generic root=UUID=541a032e-c8cd-4e5d-b653-32049a6b207e ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos5)'
        search --no-floppy --fs-uuid --set=root dcd01c75-ae35-4799-a834-9b08a983891c
        linux16 /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos5)'
        search --no-floppy --fs-uuid --set=root dcd01c75-ae35-4799-a834-9b08a983891c
        linux16 /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set=root 70BA29D7BA299A9C
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
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                grub/grub.cfg                                  1
               =                initrd.img-3.2.0-23-generic                    2
               =                vmlinuz-3.2.0-23-generic                       2

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=541a032e-c8cd-4e5d-b653-32049a6b207e /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=dcd01c75-ae35-4799-a834-9b08a983891c /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=871328e5-0f65-46b7-a851-a3143a859868 /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=3264f780-de21-4fb1-9856-f77df511cda9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

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
        linux   /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
        initrd  /casper/initrd.lz
}
menuentry "Install Ubuntu" {
        set gfxpayload=keep
        linux   /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
        initrd  /casper/initrd.lz
}
menuentry "Check disc for defects" {
        set gfxpayload=keep
        linux   /casper/vmlinuz  boot=casper integrity-check quiet splash --
        initrd  /casper/initrd.lz
}
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/chain.c32                             1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/chain.c32                 :  COM32R module (v4.xx)
 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected

```

---

### Post by offgridguy on 2012-09-07
I have just installed ubuntu 12.04  alongside windows 7,  have yet to restart so i may need this info
myself,  thank you.

---

### Post by offgridguy on 2012-09-07
I know this thread is old news and not marked solved,  just wanted to say i did shut off and
reboot to either windows or ubuntu, no issues.

---

