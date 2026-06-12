---
title: "Cannot boot into Windows after installing Ubuntu 10.04"
date: 2010-06-03
forum: General Help
---

### Post by dbreeder on 2010-06-03
Hello,

I am a new user to Ubuntu and Linux in general. I installed Ubuntu through a LiveCD of version. 9.04 and then updated to 10.04 through Ubuntu itself. Dual-booting into windows worked previously before I updated to 10.04 However, now when my computer loads and I select the Windows option, the screen just flickers and then the grub menu reappears.

I've tried updating grub without success. I also tried to repair the MBR from windows a few times and may have screwed it up. When the GRUB menu loads, the only option for windows is the "Windows Recovery Environment." 

I would really appreciate it if anyone could help me with the problem. I need to use windows since I am not (yet) too familiar with Linux. I've attached a copy of the /boot/grub/grub.cfg file if that helps.

Thanks in advance!

---

### Post by drs305 on 2010-06-03
this sounds very much like the problem (and solution) described here - Grub2 installed to the Windows Boot Sector:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")

Read through it. If it doesn't sound like the problem you are having please post the results from this script:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by dbreeder on 2010-06-04
Thanks for the help so far. 

After reading it over, it looks like that was indeed the problem. I used testdisk but when I select the "Windows Recovery Environment" option, I get a screen saying I need to use a recovery disc...

I then downloaded a Windows Recovery Disc and burned it to a DVD. However when I boot the computer with the DVD in the drive all I get is a black screen with a flashing cursor      " _ ".

It will make a few sounds as if its reading from the CD-Drive and then quiet down. Nothing changes...

Anything I can do?

BTW the boot script said this when I ran it which is why I'm guessing that was the problem...

" => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 203169080 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd"

---

### Post by wilee-nilee on 2010-06-04
Before you do any more fixes post the whole script in code tags for the best results and a fix to your problem.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end. You need to run the script again or at least after your last fix attempt so that it is correct.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
You might understand enough to do this yourself but it always helps to have others who know this stuff for a little confirmation. I think also that it may be that you need a full install dvd to run the repair, in that smoewhere something has been removed, but the script will indicate this.

---

### Post by Leppie on 2010-06-04
yes, please provide the full output of the boot info script.

---

### Post by dbreeder on 2010-06-04
Sure thing. I ran the script again and the output is as follows:
Thanks for the help.

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   201,149,864   201,149,802   7 HPFS/NTFS
/dev/sda2         201,149,865   294,905,204    93,755,340   5 Extended
/dev/sda5         201,149,928   290,969,279    89,819,352  83 Linux
/dev/sda6         290,969,343   294,905,204     3,935,862  82 Linux swap / Solaris
/dev/sda3         294,905,205   312,576,704    17,671,500   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3C368B0D368AC77C                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3aaf697c-e653-41be-b79d-f1b45f4d7557   ext4                                     
/dev/sda6        f4cee90c-7dac-4a48-b0e7-a9942a422a6b   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B69C138F9C1348EF                       ntfs       TOSHIBA EXT                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/2007.11.03_2329   udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)
/dev/sdb1        /media/TOSHIBA EXT       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 3aaf697c-e653-41be-b79d-f1b45f4d7557
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1024x768
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 3aaf697c-e653-41be-b79d-f1b45f4d7557
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3aaf697c-e653-41be-b79d-f1b45f4d7557
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=3aaf697c-e653-41be-b79d-f1b45f4d7557 ro  splash vga=791  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3aaf697c-e653-41be-b79d-f1b45f4d7557
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=3aaf697c-e653-41be-b79d-f1b45f4d7557 ro single  splash vga=791
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3aaf697c-e653-41be-b79d-f1b45f4d7557
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=3aaf697c-e653-41be-b79d-f1b45f4d7557 ro  splash vga=791  quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3aaf697c-e653-41be-b79d-f1b45f4d7557
    echo    'Loading Linux 2.6.31-14-generic ...'
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=3aaf697c-e653-41be-b79d-f1b45f4d7557 ro single  splash vga=791
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3aaf697c-e653-41be-b79d-f1b45f4d7557
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 3aaf697c-e653-41be-b79d-f1b45f4d7557
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3c368b0d368ac77c
    drivemap -s (hd0) ${root}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=3aaf697c-e653-41be-b79d-f1b45f4d7557 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f4cee90c-7dac-4a48-b0e7-a9942a422a6b none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 103.1GB: boot/grub/core.img
 107.8GB: boot/grub/grub.cfg
 111.9GB: boot/initrd.img-2.6.31-14-generic
 113.7GB: boot/initrd.img-2.6.32-22-generic
 103.8GB: boot/vmlinuz-2.6.31-14-generic
 111.6GB: boot/vmlinuz-2.6.32-22-generic
 113.7GB: initrd.img
 111.9GB: initrd.img.old
 111.6GB: vmlinuz
 103.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  fa 31 c0 8e d8 8e d0 bc  00 7c 89 e6 06 57 52 8e  |.1.......|...WR.|
00000010  c0 fb fc bf 00 06 b9 00  01 f3 a5 ea 20 06 00 00  |............ ...|
00000020  52 b4 41 bb aa 55 31 c9  30 f6 f9 cd 13 72 13 81  |R.A..U1.0....r..|
00000030  fb 55 aa 75 0d d1 e9 73  09 66 c7 06 8d 06 b4 42  |.U.u...s.f.....B|
00000040  eb 15 5a b4 08 cd 13 83  e1 3f 51 0f b6 c6 40 f7  |..Z......?Q...@.|
00000050  e1 52 50 66 31 c0 66 99  e8 66 00 e8 21 01 4d 69  |.RPf1.f..f..!.Mi|
00000060  73 73 69 6e 67 20 6f 70  65 72 61 74 69 6e 67 20  |ssing operating |
00000070  73 79 73 74 65 6d 2e 0d  0a 66 60 66 31 d2 bb 00  |system...f`f1...|
00000080  7c 66 52 66 50 06 53 6a  01 6a 10 89 e6 66 f7 36  ||fRfP.Sj.j...f.6|
00000090  f4 7b c0 e4 06 88 e1 88  c5 92 f6 36 f8 7b 88 c6  |.{.........6.{..|
000000a0  08 e1 41 b8 01 02 8a 16  fa 7b cd 13 83 c4 10 66  |..A......{.....f|
000000b0  61 c3 e8 c4 ff be be 7d  bf be 07 b9 20 00 f3 a5  |a......}.... ...|
000000c0  c3 66 60 89 e5 bb be 07  b9 04 00 31 c0 53 51 f6  |.f`........1.SQ.|
000000d0  07 80 74 03 40 89 de 83  c3 10 e2 f3 48 74 5b 79  |..t.@.......Ht[y|
000000e0  39 59 5b 8a 47 04 3c 0f  74 06 24 7f 3c 05 75 22  |9Y[.G.<.t.$.<.u"|
000000f0  66 8b 47 08 66 8b 56 14  66 01 d0 66 21 d2 75 03  |f.G.f.V.f..f!.u.|
00000100  66 89 c2 e8 ac ff 72 03  e8 b6 ff 66 8b 46 1c e8  |f.....r....f.F..|
00000110  a0 ff 83 c3 10 e2 cc 66  61 c3 e8 62 00 4d 75 6c  |.......fa..b.Mul|
00000120  74 69 70 6c 65 20 61 63  74 69 76 65 20 70 61 72  |tiple active par|
00000130  74 69 74 69 6f 6e 73 2e  0d 0a 66 8b 44 08 66 03  |titions...f.D.f.|
00000140  46 1c 66 89 44 08 e8 30  ff 72 13 81 3e fe 7d 55  |F.f.D..0.r..>.}U|
00000150  aa 0f 85 06 ff bc fa 7b  5a 5f 07 fa ff e4 e8 1e  |.......{Z_......|
00000160  00 4f 70 65 72 61 74 69  6e 67 20 73 79 73 74 65  |.Operating syste|
00000170  6d 20 6c 6f 61 64 20 65  72 72 6f 72 2e 0d 0a 5e  |m load error...^|
00000180  ac b4 0e 8a 3e 62 04 b3  07 cd 10 3c 0a 75 f1 cd  |....>b.....<.u..|
00000190  18 f4 eb fd 61 72 64 20  44 69 73 6b 00 52 65 61  |....ard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  4d 47 52 20 69 73 20 63  |...<.u..MGR is c|
000001c0  6f 6d 70 72 65 73 73 65  64 00 0d 0a 50 72 65 73  |ompressed...Pres|
000001d0  73 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 20 74  |s Ctrl+Alt+Del t|
000001e0  6f 20 72 65 73 74 61 72  74 0d 0a 00 00 00 00 00  |o restart.......|
000001f0  00 00 00 00 00 00 00 00  80 9d b2 ca 00 00 55 aa  |..............U.|
00000200


```

---

### Post by wilee-nilee on 2010-06-04
Is sdb1 the actual running windows main OS?, or is it sda3, sda1 is the recovery.

---

### Post by dbreeder on 2010-06-04
I think it is sda3 since there used to be an entry on the grub menu with windows on sda3, but I'm not sure.

---

### Post by wilee-nilee on 2010-06-04
> **dbreeder said:**
> I think it is sda3 since there used to be an entry on the grub menu with windows on sda3, but I'm not sure.

Yeah, there is some conflicting info on the bootscript sda3 shows a unidentified file type and no boot/bcd stuff, so hopefully the guys who can really dissect this stuff will notice the script and put on the hero's cape and swoop in for help.

Do you have access to a full install dvd, it will be a safety measure that will help in the future and maybe needed now. If you can get the oem recovery set, as well or make a usable backup of the recovery that might work as well. This is just information, to make sure in the future you have your ducks in a row. Lets see what the people who know say. ;)

---

### Post by Leppie on 2010-06-05
it looks like sda1 is your main windows partition and sda3 is your restore partition.
the problem is that you've installed grub2 to the boot record of sda1.
download a windows recovery disk here: [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
there's disks for both vista and 7
repair the windows boot sector with the disk you downloaded from this link, after that you will have to boot off a livecd (containing grub2, e.g. 9.10 or 10.04) and reinstall grub2 to the mbr of the drive.

---

### Post by dbreeder on 2010-06-06
Well, I used the Windows Recovery Disc and now used the 'Repair this Computer' option when it loaded. Now when I open my laptop the Grub menu is unchanged but when I select "Windows Recovery Environment" it somehow loads into Windows properly.

I never needed to reinstall grub or use a LiveCD as the grub menu stayed on startup after the windows repair and I was able to startup linux. I'm not too sure what's going on but it appears to work for now.

So thanks for all the help everyone!

---

### Post by drs305 on 2010-06-06
> **dbreeder said:**
> Now when I open my laptop the Grub menu is unchanged but when I select "Windows Recovery Environment" it somehow loads into Windows properly.

I've seen G2 fail to label an entry correctly. If you want to change the name without creating a custom menu, you can modify the instructions in Section 4 of my Grub 2 Title Tweaks thread:
[_http://ubuntuforums.org/showthread.php?t=1287602_]("http://ubuntuforums.org/showthread.php?t=1287602")

Here's the short version:

Backup and then open /etc/grub.d/30_os-prober as root:
```
sudo cp /etc/grub.d/30_os-prober /etc/grub.d/30_os-prober_orig
sudo chmod -x /etc/grub.d/30_os-prober_orig  # Added so this script isn't run during updates.
gksu gedit /etc/grub.d/30_os-prober
```

Find this section and add the section in dark red. Make sure the title is the exact title (within the quotes in /boot/grub/grub.cfg but without the "on /dev/sdXX") and that the Windows partition is correct (sdXY).

> 
for OS in ${OSPROBED} ; do
DEVICE="`echo ${OS} | cut -d ':' -f 1`"
LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
BOOT="`echo ${OS} | cut -d ':' -f 4`"

if [ -z "${LONGNAME}" ] ; then
LONGNAME="${LABEL}"
fi

[COLOR="DarkRed"]# Added to rename Windows Recovery to Windows
if [ "$LONGNAME" = "[COLOR="Red"]**Windows Recovery Environment**[/COLOR]" ] && [ "${DEVICE}" = "/dev/[COLOR="Red"]sda2[/COLOR]" ] ; then
LONGNAME="[COLOR="Red"]ENTER DESIRED TITLE HERE[/COLOR]"
fi
# End Added[/COLOR]


This should rename any menuentry that would have been named as shown in your existing menu AND found on sda2. 

Save the file and run "sudo update-grub".

---

### Post by infernooz on 2010-12-09
help me people if you can ....



i have the same problem 

[http://pastebin.com/YwXYhBih](http://pastebin.com/YwXYhBih)


please help me out

---

### Post by infernooz on 2010-12-09
above i have made a link to the  results.txt

i dont have a back up for my windows ........and i need to save my windows ....this actually took place  when i updated  my ubuntu..does it have have some issues ?

---

### Post by wilee-nilee on 2010-12-09
> **infernooz said:**
> above i have made a link to the  results.txt

i dont have a back up for my windows ........and i need to save my windows ....this actually took place  when i updated  my ubuntu..does it have have some issues ?

Best way to do this is correctly; start your own thread and paste that script in code tags. To get code tags open the new thread click on the # in the reply panel and paste the text between the code tags. My signature also gives you a manual description. 

Your problem is in no way similar to this original thread having this information mixed together can make things confusing;)

---

