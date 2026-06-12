---
title: "GRUB2 has me all messed up..."
date: 2010-08-01
forum: General Help
---

### Post by pFREDq on 2010-08-01
I am trying to triple boot Vista, XP, and Ubuntu 10.04, but it seems the great computer Jebus simply does not want it to be. Everything that could go wrong has, and after putting in well over twelve hours on trying to get this to work, I'm about to just give up. At the moment, I might be close to finally getting it to work, but the MBR was overwritten with Vista's (don't ask) and my attempt to re-install GRUB2 has led to the laptop booting up with a console-like interface, and I am unable to restore Vista's MBR. Since Ubuntu has made the switch to GRUB2, I have no idea how to re-install it the way I want. If this has been asked a thousand times already I apologize, but after almost an hour of searching, I can't find anything like this.
I have Vista and (possibly) XP installed on my laptop's hard drive and Ubuntu 10.04 installed on my external hard drive. I am currently using the Live CD. I want GRUB2 installed on my laptop's internal HDD with the configuration files (stuff in /etc/grub.d, etc.) to go on a small (5GB) ext4-formatted partition on the internal HDD. In other words I want EVERYTHING that has to do with GRUB2 on my internal HDD, that way I can boot through GRUB regardless of whether or not my external HDD is plugged in. I know how I would go about doing this with older GRUB versions, but GRUB2 seems to be completely different. Any help would great. Thanks!

---

### Post by prodigy_ on 2010-08-01
Boot from Ubuntu Live CD, use Boot Info script linked in signature and post the results here.

---

### Post by pFREDq on 2010-08-02
I managed to restore Vista's bootloader. Anyway, here is RESULTS.txt:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /boot/bcd /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   255,229,950   255,229,888   7 HPFS/NTFS
/dev/sda2         255,229,952   282,492,927    27,262,976   7 HPFS/NTFS
/dev/sda3         282,494,974   292,976,639    10,481,666   5 Extended
/dev/sda5         282,494,976   292,976,639    10,481,664  83 Linux
/dev/sda4         292,978,688   312,569,855    19,591,168   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,932,882,326 1,932,882,264   7 HPFS/NTFS
/dev/sdb2       1,932,886,016 1,953,519,615    20,633,600  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D2D0CA67D0CA5201                       ntfs                                     
/dev/sda2        0C5C98DF5C98C4BC                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        5E1ACD781ACD4E29                       ntfs       PRESARIO_RP                   
/dev/sda5        2f485898-8782-4ccf-814e-c56957efa8ae   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D27431CF7431B6D7                       ntfs       Iomega HDD                    
/dev/sdb2        fa7409e4-8d1c-421a-9897-b51e56864d9b   ext3                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sdb2/boot/grub/grub.cfg: ===========================

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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set fa7409e4-8d1c-421a-9897-b51e56864d9b
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set fa7409e4-8d1c-421a-9897-b51e56864d9b
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
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set fa7409e4-8d1c-421a-9897-b51e56864d9b
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=fa7409e4-8d1c-421a-9897-b51e56864d9b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set fa7409e4-8d1c-421a-9897-b51e56864d9b
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=fa7409e4-8d1c-421a-9897-b51e56864d9b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set fa7409e4-8d1c-421a-9897-b51e56864d9b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set fa7409e4-8d1c-421a-9897-b51e56864d9b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set d2d0ca67d0ca5201
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 5e1acd781acd4e29
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows XP Home"{
set root=(hd0,2)
}
### END /etc/grub.d/40_custom ###

=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=fa7409e4-8d1c-421a-9897-b51e56864d9b /               ext3    errors=remount-ro 0       1

=================== sdb2: Location of files loaded by Grub: ===================


 995.7GB: boot/grub/core.img
 995.7GB: boot/grub/grub.cfg
 995.7GB: boot/initrd.img-2.6.32-21-generic
 995.7GB: boot/vmlinuz-2.6.32-21-generic
 998.7GB: grub/core.img
 995.7GB: initrd.img
 995.7GB: vmlinuz
```

---

### Post by prodigy_ on 2010-08-02
Are you still experiencing any problems? Everything should work fine if you'll try to boot from your Iomega drive. You have two Vista entries in Grub2 menu, but the second one points to a recovery partition so you can just ignore it.

---

### Post by pFREDq on 2010-08-02
Grub is only installed on the Iomega external HDD (sdb), what I'm trying to do is install it on my internal HDD (sda) so that I can boot through Grub even if the external (Iomega) isn't there. I'm just not sure how I would do that correctly with Grub2 (last time I tried it didn't work out so well).

---

### Post by 23dornot23d on 2010-08-02
Switch your boot device in the BIOS to boot from the second drive ...... sdb

When its unplugged it should boot from the main drive ..... sda

If not set it to do that in the BIOS.

? does that work or not .......

Windows is on sda so that should boot if sdb is removed

________________________________________________________________________

To get the grub2 on the main drive ..... so you can run Linux when the USB
is unplugged.

I think you need to install grub after ...... you boot into Linux.

grub-install /dev/sda

---

### Post by pFREDq on 2010-08-02
I'm trying to install XP alongside Vista on my internal HDD. If GRUB isn't there, then it would only boot Vista or XP depending on what MBR was last installed and I wouldn't get to choose. I want GRUB on the internal HDD so I can boot either one whenever I want. Although now that I think about, it would probably be easier to just find a different bootloader and forget about GRUB...

---

### Post by 23dornot23d on 2010-08-02
I have seen this problem many times and the problem lies with the two versions of Windows ,,,,

as you say .... a boot loader that looks after those would solve your problem .....

GRUB2 ..... may not let you do what you want - it may be easily solved like you say

 Windows really needs to be a bit more flexible ..... in the way it needs to boot up ... or allow

a linux boot from its menu system.

---

### Post by -kg- on 2010-08-02
> **pFREDq said:**
> Grub is only installed on the Iomega external HDD (sdb), [COLOR="Red"]what I'm trying to do is install it on my internal HDD (sda) so that I can boot through Grub even if the external (Iomega) isn't there.[/COLOR] I'm just not sure how I would do that correctly with Grub2 (last time I tried it didn't work out so well).

I'm not surprised you had trouble.  GRUB in the MBR is only the bootloader.  It looks to subsequent stages of GRUB in the "/boot" directory, which is normally a subdirectory of "/" (root).  You disconnect the external drive, you've robbed the bootloader of access to the rest of itself, and it won't work.

The only way to do it (I believe...I won't guarantee this, and further research is needed) is to create a separate "/boot" partition on your internal drive during the installation process (it can be done from your current installation, but is a bit of a PITA).  Around 100 MB is good.

That way, the GRUB bootloader will have access to it's subsequent stages with the external unplugged.  The only problem with this is that the installation on your external will be tied to that computer only, since it's boot files will be on the internal drive.  If you want to use Ubuntu on other computers, I would leave everything as is and just select the external drive during bootup when you want to use Ubuntu, leaving the Vista bootloader on the internal drive.

If you have bootup sequence set up in BIOS and want to boot to Windows without changing BIOS settings every time, just unplug the external drive until you're booted up, then plug the internal back in if you need access to the drive under Windows.

---

### Post by -kg- on 2010-08-02
> **23dornot23d said:**
> Windows really needs to be a bit more flexible ..... in the way it needs to boot up ... or allow a linux boot from its menu system.

Come to think of it, you might check out [EasyBCD]("http://neosmart.net/dl.php?id=1").

---

### Post by pFREDq on 2010-08-02
I had heard of EasyBCD before, so I tried that out and so far it's working great. I think I'll just stick with it for now. Thanks guys!

---

### Post by Quackers on 2010-08-02
Strangely enough I am using Easybcd to boot 2 OSes but I can't get it to boot Ubuntu. Tried different ways but no-go. I just use the grub menu to boot all 3. But it does irk me a bit :-)

---

### Post by 23dornot23d on 2010-08-02
That would possibly sort it ..... might even try this myself has anybody used it on here before to confirm its
reliability. ( ok answered my question ) posted at similar times ;)

I currently [boot 13 systems]("http://sites.google.com/site/23dornot23d/") .... and have 3 USBs ...... and can boot from 2 separate MENUS ..... but I need to
keep at least one USB plugged in to do it ,,,,,

---

### Post by wilee-nilee on 2010-08-02
I  see post 10 mentions easybcd2.

---

### Post by pFREDq on 2010-08-02
> **23dornot23d said:**
> That would possibly sort it ..... might even try this myself has anybody used it on here before to confirm its
reliability. ( ok answered my question ) posted at similar times ;)

I currently [boot 13 systems]("http://sites.google.com/site/23dornot23d/") .... and have 3 USBs ...... and can boot from 2 separate MENUS ..... but I need to
keep at least one USB plugged in to do it ,,,,,
13? Suddenly my triple boot setup doesn't seem so unnecessary. :)
Anyway, EasyBCD isn't the perfect setup in the world (I can't boot straight to Ubuntu, I have to use it to boot into GRUB and then boot into Ubuntu from there) but it gets the job done.

---

### Post by 23dornot23d on 2010-08-02
I am waiting in anticipation for a better method of booting up with a easy option
for adding and removing USB's ..... as for extra OS's being so unnecessary I like to see
where they are all up to .... and I like working out problems.

I have the GRUB2 bootloader on sda and sdc ..... but sdb is proving to be a problem.

I think that there are always solutions though - no doubt in the future this will all be so much easier.

                                       ________________________________________

Once you have multiple USBs Hard Drives they switch positions depending on a cold boot or warm boot
which leads to allsorts of other problems too .... ;) hope you get yours working as you want it to.

Once they are set up properly they are fine ......

---

### Post by oldtraveler on 2010-08-02
I solved a similar problem by adding another linux OS - namely Ubuntu 9.04 - which installs grub legacy rather than grub 2. Grub legacy runs seamlessly with my multiple boot system and includes an option to boot to Windows 7 bootloader on which there are two bootable OS. For this to work you must make Ubuntu 9.04 the last OS to be installed.

---

