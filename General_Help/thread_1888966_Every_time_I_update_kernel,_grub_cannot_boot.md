---
title: "Every time I update kernel, grub cannot boot"
date: 2011-11-30
forum: General Help
---

### Post by zachlac on 2011-11-30
Every time I do an update to the linux kernel, GRUB fails to boot.  To fix this problem, every time I have to boot from a rescue CD, do lots of crazy mount commands to get a chroot-ed environment set up, then to a dpkg-reconfigure grub.

How can I fix this so that GRUB updates itself correctly when a new kernel is installed?

Machine specifics:
Linux 2.6.35-std210-amd64 #2 SMP Fri Apr 1 21:13:29 UTC 2011 x86_64 GNU/Linux
Ubuntu 10.04.3 LTS

It's set up with RAID 1, so here is the disk info:

# fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   fd  Linux raid autodetect
/dev/sda2           28450       30394    15623212+  82  Linux swap / Solaris
/dev/sda3              32       28449   228267585   fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/sdb: 251.1 GB, 251059544064 bytes
255 heads, 63 sectors/track, 30522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x24c60f47

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          31      248976   fd  Linux raid autodetect
/dev/sdb2           28450       30394    15623212+  82  Linux swap / Solaris
/dev/sdb3              32       28449   228267585   fd  Linux raid autodetect

Partition table entries are not in disk order

Disk /dev/md127: 233.7 GB, 233745940480 bytes
2 heads, 4 sectors/track, 57066880 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md127 doesn't contain a valid partition table

Disk /dev/md126: 254 MB, 254869504 bytes
2 heads, 4 sectors/track, 62224 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md126 doesn't contain a valid partition table

---

### Post by zachlac on 2011-11-30
bump

---

### Post by zachlac on 2011-12-05
one more bump, then I give up

---

### Post by CharlesA on 2011-12-05
Bumped over the General Help. Maybe you will get more responses there.

What happened if you manually update grub before rebooting?

---

### Post by oldfred on 2011-12-05
Not familar with RAID, but what does this show. The dpkg reinstall of grub should reset this to the correct location.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by zachlac on 2011-12-05
Hello,

Thank you for the response.  When I run update-grub, it still fails to boot afterwards.  What I have to end up doing (which is not viable on a web server in the middle of the day) is booting with a rescue CD, doing all of the mounting shenanigans, and running "dpkg-reconfigure grub."

Here's the result from the server right now, in a broken state:

# debconf-show grub-pc
  grub-pc/kopt_extracted: false
  grub2/kfreebsd_cmdline:
* grub-pc/install_devices: /dev/disk/by-id/ata-WDC_WD2502ABYS-18B7A0_WD-WCAT1D671537, /dev/disk/by-id/ata-WDC_WD2502ABYS-02B7A0_WD-WCAT1E543018
  grub-pc/postrm_purge_boot_grub: false
  grub-pc/disk_description:
* grub2/linux_cmdline:
  grub-pc/install_devices_empty: false
  grub2/kfreebsd_cmdline_default: quiet
  grub-pc/partition_description:
  grub-pc/install_devices_failed: false
* grub-pc/install_devices_disks_changed: /dev/disk/by-id/ata-WDC_WD2502ABYS-18B7A0_WD-WCAT1D671537, /dev/disk/by-id/ata-WDC_WD2502ABYS-02B7A0_WD-WCAT1E543018
* grub2/linux_cmdline_default: quiet splash
  grub-pc/chainload_from_menu.lst: true
  grub-pc/hidden_timeout: true
  grub-pc/timeout: 10

---

### Post by elliotn on 2011-12-05
update grub after updating before u restarting and see if it'll work

---

### Post by zachlac on 2011-12-05
> **elliotn said:**
> update grub after updating before u restarting and see if it'll work

I've tried that.  If I run "update-grub" it goes through the motions ("Found xxx, generating yyy.") with no errors.  Yet, when I reboot, it fails to start, instead going into grub rescue.

---

### Post by oldfred on 2011-12-05
Did you manually install nVidia drivers and then they are not getting recompiled? (grasping at straws:))

---

### Post by zachlac on 2011-12-05
I actually don't have any nvidia drivers installed, nor any X server.  It's just a console interface to the server.

---

### Post by oldfred on 2011-12-05
I am out of ideas.

I might try running boot_info script before and after you install to see what is going where. It seems that with your RAID it may be installing to the MBR when it has to install to the RAID.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install mawk

---

### Post by zachlac on 2011-12-05
> **oldfred said:**
> I am out of ideas.

I might try running boot_info script before and after you install to see what is going where. It seems that with your RAID it may be installing to the MBR when it has to install to the RAID.


Thanks for helping!  I'll try to do that, and next time I have to dig around the rescue CD console, I'll try to note the exact errors related to running update-grub, etc.

---

### Post by zachlac on 2012-01-31
I hate to revive an old thread, but since this is a direct continuation, I'll do just that.

To briefly recap, our server won't boot directly, giving a grub error and dropping to grub rescue.  However, I can boot using a rescue CD and booting to an existing partition.

If I go through a bunch of steps on the rescue CD to re-install grub, sometimes it works.  I admit that I'm no grub expert, so I possibly am making mistakes.

I finally had time to run boot_info script on our web server.  The output is below.

To give you an idea of the disk setup:

Two 250GB disks (sda and sdb) have 3 partitions, all in RAID1.  One has an ext4 FS and is mapped to /boot.  Another is swap space.  The third is an LVM member, and is mapped to / (root).

Two 500GB disks (sdc and sdd) have no partitions, and instead are handled completely by lvm.  All of the space is mapped to / (root).

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (md126)/grub on this drive.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks for (md126)/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

vg-main-root': _________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg-main-vm-mail-swap': _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

vg-main-vm-test': ______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

md127: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

md126: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

md125: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/core.img

sdd: ___________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63       498,014       497,952  fd Linux raid autodetect
/dev/sda2         457,033,185   488,279,609    31,246,425  82 Linux swap / Solaris
/dev/sda3             498,015   457,033,184   456,535,170  fd Linux raid autodetect


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 251.1 GB, 251059544064 bytes
255 heads, 63 sectors/track, 30522 cylinders, total 490350672 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  63       498,014       497,952  fd Linux raid autodetect
/dev/sdb2         457,033,185   488,279,609    31,246,425  82 Linux swap / Solaris
/dev/sdb3             498,015   457,033,184   456,535,170  fd Linux raid autodetect


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/vg--main-root abc9f20d-ff1f-4eea-9b8f-a71d5dbff0b6   ext3       
/dev/md125       d54f277f-a643-48c7-9754-deff211e81f5   ext3       
/dev/md126       uyBTrW-rf4k-jtsS-QqYG-SXrO-xHoa-kZ1d54 LVM2_member 
/dev/md127       mi9Kfu-PyZU-zD1T-wgdj-V835-O3T7-BVYpdF LVM2_member 
/dev/sda1        bd3359c4-80b3-19cc-7113-9569110324e5   linux_raid_member 
/dev/sda2        197d0fb0-a2c9-4cb2-b796-7b66652b299c   swap       
/dev/sda3        8e417583-8c44-f592-56db-ed4ca597c77a   linux_raid_member 
/dev/sdb1        bd3359c4-80b3-19cc-7113-9569110324e5   linux_raid_member 
/dev/sdb3        8e417583-8c44-f592-56db-ed4ca597c77a   linux_raid_member 
/dev/sdc         85d58391-88ef-3673-7cef-913bc1b0ff19   linux_raid_member 
/dev/sdd         85d58391-88ef-3673-7cef-913bc1b0ff19   linux_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
vg--main-root
vg--main-vm--mail--swap
vg--main-vm--test

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/vg--main-root /                        ext3       (rw,errors=remount-ro)
/dev/md125       /boot                    ext3       (rw)


============================= md125/grub/grub.cfg: =============================

--------------------------------------------------------------------------------
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
insmod raid
insmod mdraid
insmod lvm
insmod ext2
set root='(vg-main-root)'
search --no-floppy --fs-uuid --set abc9f20d-ff1f-4eea-9b8f-a71d5dbff0b6
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
insmod raid
insmod mdraid
insmod ext2
set root='(md125)'
search --no-floppy --fs-uuid --set d54f277f-a643-48c7-9754-deff211e81f5
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-38-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md125)'
    search --no-floppy --fs-uuid --set d54f277f-a643-48c7-9754-deff211e81f5
    linux    /vmlinuz-2.6.32-38-server root=/dev/mapper/vg--main-root ro   quiet splash
    initrd    /initrd.img-2.6.32-38-server
}
menuentry 'Ubuntu, with Linux 2.6.32-38-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md125)'
    search --no-floppy --fs-uuid --set d54f277f-a643-48c7-9754-deff211e81f5
    echo    'Loading Linux 2.6.32-38-server ...'
    linux    /vmlinuz-2.6.32-38-server root=/dev/mapper/vg--main-root ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-38-server
}
menuentry 'Ubuntu, with Linux 2.6.32-37-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md125)'
    search --no-floppy --fs-uuid --set d54f277f-a643-48c7-9754-deff211e81f5
    linux    /vmlinuz-2.6.32-37-server root=/dev/mapper/vg--main-root ro   quiet splash
    initrd    /initrd.img-2.6.32-37-server
}
menuentry 'Ubuntu, with Linux 2.6.32-37-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md125)'
    search --no-floppy --fs-uuid --set d54f277f-a643-48c7-9754-deff211e81f5
    echo    'Loading Linux 2.6.32-37-server ...'
    linux    /vmlinuz-2.6.32-37-server root=/dev/mapper/vg--main-root ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-37-server
}
menuentry 'Ubuntu, with Linux 2.6.32-36-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md125)'
    search --no-floppy --fs-uuid --set d54f277f-a643-48c7-9754-deff211e81f5
    linux    /vmlinuz-2.6.32-36-server root=/dev/mapper/vg--main-root ro   quiet splash
    initrd    /initrd.img-2.6.32-36-server
}
menuentry 'Ubuntu, with Linux 2.6.32-36-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md125)'
    search --no-floppy --fs-uuid --set d54f277f-a643-48c7-9754-deff211e81f5
    echo    'Loading Linux 2.6.32-36-server ...'
    linux    /vmlinuz-2.6.32-36-server root=/dev/mapper/vg--main-root ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-36-server
}
menuentry 'Ubuntu, with Linux 2.6.32-35-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md125)'
    search --no-floppy --fs-uuid --set d54f277f-a643-48c7-9754-deff211e81f5
    linux    /vmlinuz-2.6.32-35-server root=/dev/mapper/vg--main-root ro   quiet splash
    initrd    /initrd.img-2.6.32-35-server
}
menuentry 'Ubuntu, with Linux 2.6.32-35-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md125)'
    search --no-floppy --fs-uuid --set d54f277f-a643-48c7-9754-deff211e81f5
    echo    'Loading Linux 2.6.32-35-server ...'
    linux    /vmlinuz-2.6.32-35-server root=/dev/mapper/vg--main-root ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-35-server
}
menuentry 'Ubuntu, with Linux 2.6.32-34-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md125)'
    search --no-floppy --fs-uuid --set d54f277f-a643-48c7-9754-deff211e81f5
    linux    /vmlinuz-2.6.32-34-server root=/dev/mapper/vg--main-root ro   quiet splash
    initrd    /initrd.img-2.6.32-34-server
}
menuentry 'Ubuntu, with Linux 2.6.32-34-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md125)'
    search --no-floppy --fs-uuid --set d54f277f-a643-48c7-9754-deff211e81f5
    echo    'Loading Linux 2.6.32-34-server ...'
    linux    /vmlinuz-2.6.32-34-server root=/dev/mapper/vg--main-root ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-34-server
}
menuentry 'Ubuntu, with Linux 2.6.32-33-server' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md125)'
    search --no-floppy --fs-uuid --set d54f277f-a643-48c7-9754-deff211e81f5
    linux    /vmlinuz-2.6.32-33-server root=/dev/mapper/vg--main-root ro   quiet splash
    initrd    /initrd.img-2.6.32-33-server
}
menuentry 'Ubuntu, with Linux 2.6.32-33-server (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod raid
    insmod mdraid
    insmod ext2
    set root='(md125)'
    search --no-floppy --fs-uuid --set d54f277f-a643-48c7-9754-deff211e81f5
    echo    'Loading Linux 2.6.32-33-server ...'
    linux    /vmlinuz-2.6.32-33-server root=/dev/mapper/vg--main-root ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-33-server
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=================== md125: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

   0.034757614 = 0.037320704    grub/core.img                                  2
   0.031746864 = 0.034087936    grub/grub.cfg                                  1
   0.113757133 = 0.122145792    initrd.img-2.6.32-33-server                   46
   0.121025085 = 0.129949696    initrd.img-2.6.32-34-server                   44
   0.136857986 = 0.146950144    initrd.img-2.6.32-35-server                   38
   0.152696609 = 0.163956736    initrd.img-2.6.32-36-server                   38
   0.168553352 = 0.180982784    initrd.img-2.6.32-37-server                   38
   0.017086029 = 0.018345984    initrd.img-2.6.32-38-server                   40
   0.104753494 = 0.112478208    vmlinuz-2.6.32-33-server                      18
   0.097802162 = 0.105014272    vmlinuz-2.6.32-34-server                      21
   0.127746582 = 0.137166848    vmlinuz-2.6.32-35-server                      18
   0.141038895 = 0.151439360    vmlinuz-2.6.32-36-server                      18
   0.158939362 = 0.170659840    vmlinuz-2.6.32-37-server                      18
   0.006294250 = 0.006758400    vmlinuz-2.6.32-38-server                      17

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on vg-main-root'


Unknown BootLoader on vg-main-vm-mail-swap'


Unknown BootLoader on vg-main-vm-test'



=============================== StdErr Messages: ===============================

  skip_dev_dir: Couldn't split up device name vg-main-root'
  Volume group name vg-main-root' has invalid characters
  Skipping volume group vg-main-root'
  skip_dev_dir: Couldn't split up device name vg-main-root'
  Volume group name vg-main-root' has invalid characters
  Skipping volume group vg-main-root'
  skip_dev_dir: Couldn't split up device name vg-main-root'
  Volume group name vg-main-root' has invalid characters
  Skipping volume group vg-main-root'
hexdump: /dev/mapper/vg-main-root': No such file or directory
hexdump: /dev/mapper/vg-main-root': No such file or directory
  skip_dev_dir: Couldn't split up device name vg-main-vm-mail-swap'
  Volume group name vg-main-vm-mail-swap' has invalid characters
  Skipping volume group vg-main-vm-mail-swap'
  skip_dev_dir: Couldn't split up device name vg-main-vm-mail-swap'
  Volume group name vg-main-vm-mail-swap' has invalid characters
  Skipping volume group vg-main-vm-mail-swap'
  skip_dev_dir: Couldn't split up device name vg-main-vm-mail-swap'
  Volume group name vg-main-vm-mail-swap' has invalid characters
  Skipping volume group vg-main-vm-mail-swap'
hexdump: /dev/mapper/vg-main-vm-mail-swap': No such file or directory
hexdump: /dev/mapper/vg-main-vm-mail-swap': No such file or directory
  skip_dev_dir: Couldn't split up device name vg-main-vm-test'
  Volume group name vg-main-vm-test' has invalid characters
  Skipping volume group vg-main-vm-test'
  skip_dev_dir: Couldn't split up device name vg-main-vm-test'
  Volume group name vg-main-vm-test' has invalid characters
  Skipping volume group vg-main-vm-test'
  skip_dev_dir: Couldn't split up device name vg-main-vm-test'
  Volume group name vg-main-vm-test' has invalid characters
  Skipping volume group vg-main-vm-test'
hexdump: /dev/mapper/vg-main-vm-test': No such file or directory
hexdump: /dev/mapper/vg-main-vm-test': No such file or directory
mdadm: no devices found for /dev/md0
mdadm: no devices found for /dev/md1

```

---

### Post by oldfred on 2012-02-01
I do not know RAID, so I cannot tell if something is out of place or not.

I do know many have the /boot outside of the RAID. I guess that makes boot easier?

You may want to start a new thread with RAID in the title in the server sub forum as they more often use RAID.

---

### Post by zachlac on 2012-02-01
OK, I can try that.  Basically, in the past I've set up our servers to use RAID 1 on the /boot partition (and install GRUB to both disk's MBRs) but kept it outside of LVM, using a normal ext4 file system with partitions.  This seems to work fine.

I'll repost this with RAID in the description.  Thanks for replying!

---

