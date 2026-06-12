---
title: "Grub Rescue"
date: 2010-08-29
forum: General Help
---

### Post by alcuino on 2010-08-29
Hi 
I am having trouble booting
I am getting the "grub rescue" prompt on my screen
I went through the forum and found a script to run to check my system  and the contents of the txt file are as below:

I am also new to this forum and do not know how to send the large txt  file which is not possible in this post.

I am currently sending only part of it and will send to your email when I  have your contact details.

Please help. thanks, Alcuino
============================= Boot Info Summary:  ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the  same drive 
    in partition #9 for /boot/grub.
 => Grub1.97 is installed in the MBR of /dev/sdb and looks on the  same drive 
    in partition #1 for .

sda1:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/bcd

sda2:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe  /grldr

sda3:  _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5:  _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab  /boot/grub/core.img

sda6:  _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4:  _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info:  =============================

Drive: sda ___________________  _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,466,809    20,466,747  12 Compaq  diagnostics
/dev/sda2    *     20,467,712   220,247,634   199,779,923   7 HPFS/NTFS
/dev/sda3         220,248,062   323,074,047   102,825,986   5 Extended
/dev/sda5         264,314,880   320,557,055    56,242,176  83 Linux
/dev/sda6         320,559,104   323,074,047     2,514,944  82 Linux swap  / Solaris
/dev/sda4         323,074,048   625,139,711   302,065,664   7 HPFS/NTFS


Drive: sdb ___________________  _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null:  ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="PQSERVICE" UUID="76F011DFE49BED2A" TYPE="ntfs" 
/dev/sda2: UUID="D20AA6D40AA6B53F" TYPE="ntfs" 
/dev/sda4: LABEL="DATA" UUID="A46A6A046A69D418" TYPE="ntfs" 
/dev/sda5: UUID="58052f53-8bbf-49f6-a16f-36d3607424ec" TYPE="ext4" 
/dev/sda6: UUID="c41f884b-2fbb-4a4c-b7d9-ca09781fa973" TYPE="swap"

---

### Post by quixote on 2010-08-30
What the bootinfo is saying is that sdb (the second drive) has no partitions or isn't formatted.  Is that right?  Or was that some of the further part of the text that you didn't post?  It should come after this bit: > Drive: sdb ___________________ __________________________________________________ ___

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System


On the first drive (sda), you have two Windows boot partitions, and a Windows-type data partition.  Does that sound right? And then sda5 is your ubuntu partition.

what I'd suggest is worrying about the second drive later.  For now, let's just see if we can get it to boot off the ubuntu partition.  Then you can rebuild grub, get at your Windows install(s), and fix the second drive.  To fix grub, try the following steps at the grub rescue prompt. Hit the enter key after each command. (Taken from [Grub2 Docs]("https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot").) ```
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot
```Hopefully, that then boots into ubuntu.  If so, then *before you reboot*, run```
sudo update-grub
```That should fix your grub, and the next time you reboot, the choices should actually work.  If anything's not clear, keep asking. :D

---

### Post by alcuino on 2010-08-30
Hi,
Thanks for the advice.
What you have observed from the posted text file is right. I have a new unformated drive and the rest of the facts stated by you are also accurate.
I have tried to solve the issue with your suggested commands, but it did'nt work.
There is no activity after entering the first 02 lines, but I get the reply that "command not reconised" after entering the onwards the 3rd command.  I have also attached the full text output.  Maybe you would be able to help me better if this was available in the first place, but I am new to the forum. 
Thanks for your help.
awaiting your response.

---

### Post by andrewthomas on 2010-08-30
Try using 
```
set prefix=(hd1,5)/boot/grub
set root=(hd1,5)
linux /vmlinuz root=/dev/sda5 ro
initrd /initrd.img
boot
```

---

### Post by alcuino on 2010-08-30
Thanks again for the quick reply.

Again it is the same state.

there is no response for the 1st 02 commands.

From the 3rd command onwards (same here) systems responds with "Unknown Command 'linux /vmlinuz" ......

Thanks.

---

### Post by quixote on 2010-08-30
Well, all that means is that it's not finding the files needed to boot where we're telling it.  So the next step is to go the longer way around.  You use "ls" to list the contents of directories until you find the real one.  

However, maybe we can avoid that tedium if you can post your new "results.txt."  Unfortunately the attachment didn't work.  Don't worry about copying the whole thing into your answer if you need to.  Attachments are a better way, but if they're not working for you, the important thing is to get the problem solved.

---

### Post by alcuino on 2010-08-30
Hi Thanks for the reply,

I am pasting below the whole contents of the txt file.



============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #9 for /boot/grub.
 => Grub1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for .

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    20,466,809    20,466,747  12 Compaq diagnostics
/dev/sda2    *     20,467,712   220,247,634   199,779,923   7 HPFS/NTFS
/dev/sda3         220,248,062   323,074,047   102,825,986   5 Extended
/dev/sda5         264,314,880   320,557,055    56,242,176  83 Linux
/dev/sda6         320,559,104   323,074,047     2,514,944  82 Linux swap / Solaris
/dev/sda4         323,074,048   625,139,711   302,065,664   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="PQSERVICE" UUID="76F011DFE49BED2A" TYPE="ntfs" 
/dev/sda2: UUID="D20AA6D40AA6B53F" TYPE="ntfs" 
/dev/sda4: LABEL="DATA" UUID="A46A6A046A69D418" TYPE="ntfs" 
/dev/sda5: UUID="58052f53-8bbf-49f6-a16f-36d3607424ec" TYPE="ext4" 
/dev/sda6: UUID="c41f884b-2fbb-4a4c-b7d9-ca09781fa973" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 58052f53-8bbf-49f6-a16f-36d3607424ec
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 58052f53-8bbf-49f6-a16f-36d3607424ec
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 58052f53-8bbf-49f6-a16f-36d3607424ec
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=58052f53-8bbf-49f6-a16f-36d3607424ec ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 58052f53-8bbf-49f6-a16f-36d3607424ec
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=58052f53-8bbf-49f6-a16f-36d3607424ec ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 58052f53-8bbf-49f6-a16f-36d3607424ec
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 58052f53-8bbf-49f6-a16f-36d3607424ec
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 76f011dfe49bed2a
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb2)" {
	insmod ntfs
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set d20aa6d40aa6b53f
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=58052f53-8bbf-49f6-a16f-36d3607424ec /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=c41f884b-2fbb-4a4c-b7d9-ca09781fa973 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 135.3GB: boot/grub/grub.cfg
 135.3GB: boot/initrd.img-2.6.32-21-generic
 135.3GB: boot/vmlinuz-2.6.32-21-generic
 135.3GB: initrd.img
 135.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  0b 46 f2 9d 11 02 7d 8b  46 53 ab d5 9b 32 d4 fa  |.F....}.FS...2..|
00000010  76 7d 40 4d e6 4c c6 b8  fe fe 9b 3b ca 7c 82 a2  |v}@M.L.....;.|..|
00000020  41 bf 87 0b f5 de 59 84  6a 0d a0 5a d4 7a cb 80  |A.....Y.j..Z.z..|
00000030  4d 43 e3 bf 91 5a 56 ae  be eb 4f f0 c9 03 c8 e8  |MC...ZV...O.....|
00000040  a4 26 ec 73 99 6f 22 17  90 32 01 b9 3e e0 d0 35  |.&.s.o"..2..>..5|
00000050  70 33 bf 61 fc 74 64 cf  27 13 5c 3e 90 9e 51 95  |p3.a.td.'.\>..Q.|
00000060  4c df 83 f9 83 fe fc c8  bb 99 6f ab 52 e2 3c b5  |L.........o.R.<.|
00000070  be f7 8e 43 14 4a 0c 44  a8 7f 74 da b3 df ba d3  |...C.J.D..t.....|
00000080  33 08 0d a4 4c df 27 70  4c 35 1a 03 b9 52 df e7  |3...L.'pL5...R..|
00000090  5a 57 fa 21 f7 f3 9a dc  aa da 43 91 42 3f 60 58  |ZW.!......C.B?`X|
000000a0  2d 1a 34 26 4c 98 53 bf  2a 9c ce 50 e9 07 bd 5e  |-.4&L.S.*..P...^|
000000b0  4e b9 ae ee f6 1b 57 94  5f 67 9c fd fc 4b 44 02  |N.....W._g...KD.|
000000c0  71 42 3d 3f a5 29 e5 82  fa 20 b4 9c 35 71 13 fb  |qB=?.)... ..5q..|
000000d0  ee e5 bb 64 dc 3c 4f 2f  7c 03 b0 3b 15 3e e7 60  |...d.<O/|..;.>.`|
000000e0  8f ee bf fb 1e 68 b7 96  dc 43 36 57 2f 3a 07 00  |.....h...C6W/:..|
000000f0  bb 3b 19 ef f3 ed c6 ca  04 b7 8f 72 c2 3b 12 a1  |.;.........r.;..|
00000100  97 e7 10 74 24 43 e8 da  ac f7 8b ca f7 ef 23 74  |...t$C........#t|
00000110  24 e1 e1 7a 45 6d c0 3b  33 7b 61 cc 3d 1f 33 85  |$..zEm.;3{a.=.3.|
00000120  16 2c be 40 a2 1f 7e e6  0c 9c 0f c8 db 68 f5 9f  |.,.@..~......h..|
00000130  6f fe a9 15 12 d2 0e c6  d2 8f 28 b6 d1 94 77 7e  |o.........(...w~|
00000140  21 87 26 dd 98 db b1 15  71 01 38 0c fd c8 b9 bb  |!.&.....q.8.....|
00000150  29 34 02 a4 79 72 66 3f  e1 e3 cb 94 98 18 77 b6  |)4..yrf?......w.|
00000160  7e 8a 1c 80 e7 48 b8 2b  d9 7e 31 f1 1b 1c b5 ba  |~....H.+.~1.....|
00000170  38 43 0f 12 fd 94 1b 7d  c0 ea b5 47 e8 de cb da  |8C.....}...G....|
00000180  ea 74 fc 75 29 99 8d a8  d1 c7 14 ac ac 8a 4f 9a  |.t.u).........O.|
00000190  7e 24 5e cb b7 39 25 2b  94 ad 8f 29 22 24 4f ad  |~$^..9%+...)"$O.|
000001a0  2a b0 b0 69 93 6b 0b 3c  5f b4 22 2c c4 1c fd 9c  |*..i.k.<_.",....|
000001b0  60 30 a9 48 00 66 7c 4f  0b 7d a7 87 a2 68 00 fe  |`0.H.f|O.}...h..|
000001c0  ff ff 83 fe ff ff 02 68  a0 02 00 30 5a 03 00 fe  |.......h...0Z...|
000001d0  ff ff 05 fe ff ff 02 98  fa 05 00 68 26 00 00 00  |...........h&...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Rubi1200 on 2010-08-30
This is part of the problem:
GRUB is looking in all the wrong places.

This is how you can sort things out using the Lucid LiveCD:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Use the first method and follow the instructions to the letter.

You want to mount sda5 and install GRUB to sda

Hopefully, this gets at least 1 drive booting and then we can sort out any other problems.

EDIT: correction; I just saw the results of fstab in the second results.txt. So, did you install Ubuntu to the 1st or 2nd drive? Because fstab seems to indicate it was sdb which nows shows nothing?!?

---

### Post by oldfred on 2010-08-30
Rubi1200 is mostly correctly but grub 1.97 is an older version of grub2 (grub legacy was 0.97), but you do want to reinstall grub2. That both ended in 97  for a while has lead to some confusion. The instructions he linked to should let your reinstall grub2.

Since we have your results.txt (it would be better is you posted in code tags by highlighting and clicking on the # in the edit panel)

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

It looks like in grub's menu that it refers to hd1, so you had another drive installed but the search should find the correct drive if the MBR is updated. Did you not install grub2 to the MBR of this drive and it still has an older version of grub in it?

---

### Post by quixote on 2010-08-30
Yes, as oldfred points out, grub is expecting to find the ubuntu (and windows!) bootable files on the second drive (sdb) which is unformatted.  I've heard that upgrades to Lucid will sometimes renumber the drives, so that what was the first becomes the third, or whatever, thus confusing the system, the user, itself, and everybody else. :rolleyes:

But what I don't understand is why when you point grub at the right drive and partition (hd0,5), as in the commands in my first comment, it's not finding it.  The link Rubi1200 provides (the bit you want is actually up several screens' worth from where you land) provides a more thorough list of commands that I remember using once successfully.  Definitely worth a try if the first method didn't work.  These are the commands as listed:```
1. ls
2. set prefix=(hdX,Y)/boot/grub
3. set root=(hdX,Y)
4. set
5. ls /boot     
6. insmod /boot/grub/linux.mod
7. linux /vmlinuz root=/dev/sdXY ro
8. initrd /initrd.img
9. boot 
```
If I've understood your setup correctly, this is what they would look like in your case:```
1. ls   *[shows the available partitions]*

2. set prefix=(hd0,5)/boot/grub

3*. set root=(hd0,5)

4. set

5. ls /boot         *[directory listing of /boot so you can check it]*

6. insmod /boot/grub/linux.mod

7*. linux /vmlinuz root=/dev/sda5 ro

8. initrd /initrd.img

9. boot 
```
It looks like there's an MBR on *both* sda and sdb, and maybe that's causing confusion.  At some point, what was the second drive became the first somewhere in the system's tiny mind, and that's what's been giving you grief.

---

