---
title: "Grub2 menuentry to boot Gentoo?"
date: 2011-04-26
forum: General Help
---

### Post by HankB on 2011-04-26
I've partially installed Gentoo to a separate (RAID0) partition and would like to boot it from my Ubuntu 10.04 Grub installation. I have a /boot on RAID1 (mirror) and Ubuntu root on RAID1 (stripe set.) I have added what I could figure out to 
```
hbarta@olive:~$ cat /etc/grub.d/40_custom 
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

# /dev/md2: UUID="4b8da118-c3fd-4313-9239-9d091967bff0" TYPE="ext4" 
# /dev/md0: UUID="6b74e77e-a0f8-4ce9-941e-0e7fba116b48" TYPE="ext4" 

menuentry "Gentoo Linux" --class gnu-linux --class gnu --class os  { 
	recordfail
        insmod raid
        insmod mdraid
        insmod ext2
	set root='(md0)' 
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux /kernel-genkernel-x86_64-2.6.37-gentoo-r4 root=4b8da118-c3fd-4313-9239-9d091967bff0  ro
	initrd /initramfs-genkernel-x86_64-2.6.37-gentoo-r4
} 
hbarta@olive:~$ 
```
/boot is on /dev/md0 and root is on /dev/md2.

For comparison, here is a section for an Ubuntu kernel:
```
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod raid
        insmod mdraid
        insmod ext2
        set root='(md0)'
        search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
        linux   /vmlinuz-2.6.32-31-generic root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro   quiet splash
        initrd  /initrd.img-2.6.32-31-generic
}

```
The Ubuntu root is on /dev/md1

```
hbarta@olive:~$ sudo blkid /dev/md[012]
/dev/md0: UUID="6b74e77e-a0f8-4ce9-941e-0e7fba116b48" TYPE="ext4" 
/dev/md1: UUID="a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1" TYPE="ext4" 
/dev/md2: UUID="4b8da118-c3fd-4313-9239-9d091967bff0" TYPE="ext4" 
hbarta@olive:~$ 

```

When I run 'update-grub' it does not list the Gentoo kernel though it does add that section to /boot/grub/grub.cfg'. When I boot, the Gentoo entry does not appear. I can type 'c' to get a console prompt. At that point I can enter:
```
linux (md0)/kernel-genkernel-x86_64-2.6.37-gentoo-r4
initrd (md0)/initramfs-genkernel-x86_64-2.6.37-gentoo-r4
boot
```
And it starts to boot the Gentoo kernel. (That fails when it cannot find the root partition, but I think that is past the point where grub has done it's work.)

Does anyone have any idea what I have wrong in the Gentoo menuentry that causes it not to show up? It's awkward to have to do that manually when you type like I do. ;)

thanks,
hank

---

### Post by HankB on 2011-04-27
No grub experts can offer a suggestion?

---

### Post by cipherboy_loc on 2011-04-27
Does update-grub + os-prober not detect the install? I am not on my laptop (with Gentoo) right now, but I remember having to modify the os-prober script in /etc/grub.d to allow all of the entries to show.


Cipherboy

---

### Post by HankB on 2011-04-27
> **cipherboy_loc said:**
> Does update-grub + os-prober not detect the install? I am not on my laptop (with Gentoo) right now, but I remember having to modify the os-prober script in /etc/grub.d to allow all of the entries to show.

I'd appreciate that - thanks.

Edit: OS Prober does not find Gentoo.

---

### Post by oldfred on 2011-04-27
I do not know RAID. But post this.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

Install these before running script:
Is able to search LVM partitions if the LVM2 package is install
# ("apt-get install lvm2" in debian based distros)
# Is able to search Linux Software Raid partitions (MD Raids) if
# the "mdadm" package is installed.


If you have Natty, gpt or other newer configurations you might try the test version 
Get last development version of Boot Info Script:
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

---

### Post by HankB on 2011-04-28
Here is bootinfo. I don't really care if /etc/grub.d/30_os-prober doesn't find the Gentoo kernel. I'm happy to add it manually via /etc/grub.d/40_custom if I could get that to work.

/dev/sd[ih] are my mp3 player (USB) and can be ignored.

thanks,
hank

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for (md0)/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for (md0)/grub.
 => No boot loader is installed in the MBR of /dev/sdi

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb8: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb9: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdi1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

md1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /etc/fstab

md0: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /boot/grub/grub.cfg /grub/core.img 
                       /boot/grub/core.img

md2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files/dirs:   /etc/fstab

md4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

md3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdh: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     1,992,059     1,991,997  fd Linux raid autodetect
/dev/sda2           1,992,121   390,716,864   388,724,744   5 Extended
/dev/sda5           1,992,123    21,992,984    20,000,862  fd Linux raid autodetect
/dev/sda6          21,993,048    29,993,354     8,000,307  82 Linux swap / Solaris
/dev/sda7          29,995,403    45,355,402    15,360,000  fd Linux raid autodetect
/dev/sda8          45,357,451    60,512,650    15,155,200  fd Linux raid autodetect
/dev/sda9          60,514,699   390,716,864   330,202,166  fd Linux raid autodetect


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     1,992,059     1,991,997  fd Linux raid autodetect
/dev/sdb2           1,992,121   390,716,864   388,724,744   5 Extended
/dev/sdb5           1,992,123    21,992,984    20,000,862  fd Linux raid autodetect
/dev/sdb6          21,993,048    29,993,354     8,000,307  82 Linux swap / Solaris
/dev/sdb7          29,995,403    45,355,402    15,360,000  fd Linux raid autodetect
/dev/sdb8          45,357,451    60,512,650    15,155,200  fd Linux raid autodetect
/dev/sdb9          60,514,699   390,716,864   330,202,166  fd Linux raid autodetect


Drive: sdi ___________________ _____________________________________________________

Disk /dev/sdi: 7969 MB, 7969177600 bytes
221 heads, 20 sectors/track, 3521 cylinders, total 15564800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdi1               8,192    15,564,799    15,556,608   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/md0         6b74e77e-a0f8-4ce9-941e-0e7fba116b48   ext4                                     
/dev/md1         a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1   ext4                                     
/dev/md2         4b8da118-c3fd-4313-9239-9d091967bff0   ext4                                     
/dev/md3         c7efbf66-aa81-476f-afef-f786d149c12b   ext4                                     
/dev/md4         75ae7269-ee68-44a8-9938-2a2baf5b4e0f   ext4                                     
/dev/sda1        8a58b207-36d6-9762-e368-bf24bd0fce41   linux_raid_member                               
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7ceb1908-9fcb-6d93-e368-bf24bd0fce41   linux_raid_member                               
/dev/sda6        6e9fd64a-ead6-4d9f-a85a-a9e5f0e4f44e   swap                                     
/dev/sda7        720a8650-4c59-3823-c9fc-47093c1deb17   linux_raid_member                               
/dev/sda8        7d4c1b22-61a1-bd08-c9fc-47093c1deb17   linux_raid_member                               
/dev/sda9        ee6c6b3d-8e5e-dd73-c9fc-47093c1deb17   linux_raid_member                               
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8a58b207-36d6-9762-e368-bf24bd0fce41   linux_raid_member                               
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        7ceb1908-9fcb-6d93-e368-bf24bd0fce41   linux_raid_member                               
/dev/sdb6        c48a07b6-bca9-4ce1-ae3e-70c4c4b6ad4f   swap                                     
/dev/sdb7        720a8650-4c59-3823-c9fc-47093c1deb17   linux_raid_member                               
/dev/sdb8        7d4c1b22-61a1-bd08-c9fc-47093c1deb17   linux_raid_member                               
/dev/sdb9        ee6c6b3d-8e5e-dd73-c9fc-47093c1deb17   linux_raid_member                               
/dev/sdb: PTTYPE="dos" 
/dev/sdh         0123-4567                              vfat                                     
/dev/sdi1        7880-3787                              vfat                                     
/dev/sdi: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/md1         /                        ext4       (rw,errors=remount-ro)
/dev/md0         /boot                    ext4       (rw)
/dev/md3         /home                    ext4       (rw)
/dev/sdh         /media/0123-4567         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdi1        /media/7880-3787         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ md1/etc/fstab: ================================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md1 during installation
UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/md0 during installation
UUID=6b74e77e-a0f8-4ce9-941e-0e7fba116b48 /boot           ext4    defaults        0       2

# /home was on /dev/md2 during installation
##UUID=b814a97f-3e18-4e18-b49f-10197ed4eb55 /home           ext4    defaults        0       2
#/dev/md3: UUID="c7efbf66-aa81-476f-afef-f786d149c12b" TYPE="ext4" 
# UUID=c7efbf66-aa81-476f-afef-f786d149c12b /home           ext4    defaults        0       2
## ARRAY /dev/md3 level=raid1 num-devices=2 metadata=00.90 UUID=ee6c6b3d:8e5edd73:c9fc4709:3c1deb17
# /dev/md3: UUID="ee6c6b3d:8e5edd73:c9fc4709:3c1deb17" TYPE="ext4" 
# UUID=ee6c6b3d:8e5edd73:c9fc4709:3c1deb17 /home           ext4    defaults        0       2
# /dev/md3: UUID="c7efbf66-aa81-476f-afef-f786d149c12b" TYPE="ext4" 
UUID=c7efbf66-aa81-476f-afef-f786d149c12b /home           ext4    defaults        0       2



# swap was on /dev/sda6 during installation
UUID=6e9fd64a-ead6-4d9f-a85a-a9e5f0e4f44e none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
UUID=c48a07b6-bca9-4ce1-ae3e-70c4c4b6ad4f none            swap    sw              0       0

oak:/export/redwood /mnt/oak    nfs rw,user,auto 0 0
oak:/export/share /mnt/share    nfs rw,user,auto 0 0



==================== md1: Location of files loaded by Grub: ====================


    .3GB: initrd.img
    .3GB: initrd.img.old
    .3GB: vmlinuz
    .2GB: vmlinuz.old

============================== md0/grub/grub.cfg: ==============================

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
set default="${saved_entry}"
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
insmod ext2
set root='(md1)'
search --no-floppy --fs-uuid --set a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1
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
set root='(md0)'
search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
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
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux	/vmlinuz-2.6.32-31-generic root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro   quiet splash
	initrd	/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	echo	'Loading Linux 2.6.32-31-generic ...'
	linux	/vmlinuz-2.6.32-31-generic root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux	/vmlinuz-2.6.32-30-generic root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro   quiet splash
	initrd	/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	echo	'Loading Linux 2.6.32-30-generic ...'
	linux	/vmlinuz-2.6.32-30-generic root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-preempt-bfs' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux	/vmlinuz-2.6.32-30-preempt-bfs root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro   quiet splash
	initrd	/initrd.img-2.6.32-30-preempt-bfs
}
menuentry 'Ubuntu, with Linux 2.6.32-30-preempt-bfs (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	echo	'Loading Linux 2.6.32-30-preempt-bfs ...'
	linux	/vmlinuz-2.6.32-30-preempt-bfs root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-30-preempt-bfs
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux	/vmlinuz-2.6.32-28-generic root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro   quiet splash
	initrd	/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/vmlinuz-2.6.32-28-generic root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-preempt' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux	/vmlinuz-2.6.32-31-preempt root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro   quiet splash
	initrd	/initrd.img-2.6.32-31-preempt
}
menuentry 'Ubuntu, with Linux 2.6.32-31-preempt (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	echo	'Loading Linux 2.6.32-31-preempt ...'
	linux	/vmlinuz-2.6.32-31-preempt root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-31-preempt
}
menuentry 'Ubuntu, with Linux 2.6.32-30-preempt' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux	/vmlinuz-2.6.32-30-preempt root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro   quiet splash
	initrd	/initrd.img-2.6.32-30-preempt
}
menuentry 'Ubuntu, with Linux 2.6.32-30-preempt (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	echo	'Loading Linux 2.6.32-30-preempt ...'
	linux	/vmlinuz-2.6.32-30-preempt root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-30-preempt
}
menuentry 'Ubuntu, with Linux 2.6.31-11-rt' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux	/vmlinuz-2.6.31-11-rt root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro   quiet splash
	initrd	/initrd.img-2.6.31-11-rt
}
menuentry 'Ubuntu, with Linux 2.6.31-11-rt (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	echo	'Loading Linux 2.6.31-11-rt ...'
	linux	/vmlinuz-2.6.31-11-rt root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.31-11-rt
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if sleep --verbose --interruptible 5 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

# /dev/md2: UUID="4b8da118-c3fd-4313-9239-9d091967bff0" TYPE="ext4" 
# /dev/md0: UUID="6b74e77e-a0f8-4ce9-941e-0e7fba116b48" TYPE="ext4" 

menuentry "Gentoo Linux" --class gnu-linux --class gnu --class os  { 
	recordfail
        insmod raid
        insmod mdraid
        insmod ext2
	set root='(md0)' 
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux /kernel-genkernel-x86_64-2.6.37-gentoo-r4 root=4b8da118-c3fd-4313-9239-9d091967bff0  ro
	initrd /initramfs-genkernel-x86_64-2.6.37-gentoo-r4
} 
### END /etc/grub.d/40_custom ###

=========================== md0/boot/grub/grub.cfg: ===========================

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
set default="${saved_entry}"
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
insmod ext2
set root='(md1)'
search --no-floppy --fs-uuid --set a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1
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
set root='(md0)'
search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
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
menuentry 'Ubuntu, with Linux 2.6.32-31-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux	/vmlinuz-2.6.32-31-generic root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro   quiet splash
	initrd	/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	echo	'Loading Linux 2.6.32-31-generic ...'
	linux	/vmlinuz-2.6.32-31-generic root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-31-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux	/vmlinuz-2.6.32-30-generic root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro   quiet splash
	initrd	/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	echo	'Loading Linux 2.6.32-30-generic ...'
	linux	/vmlinuz-2.6.32-30-generic root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-30-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-30-preempt-bfs' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux	/vmlinuz-2.6.32-30-preempt-bfs root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro   quiet splash
	initrd	/initrd.img-2.6.32-30-preempt-bfs
}
menuentry 'Ubuntu, with Linux 2.6.32-30-preempt-bfs (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	echo	'Loading Linux 2.6.32-30-preempt-bfs ...'
	linux	/vmlinuz-2.6.32-30-preempt-bfs root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-30-preempt-bfs
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux	/vmlinuz-2.6.32-28-generic root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro   quiet splash
	initrd	/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	echo	'Loading Linux 2.6.32-28-generic ...'
	linux	/vmlinuz-2.6.32-28-generic root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-31-preempt' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux	/vmlinuz-2.6.32-31-preempt root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro   quiet splash
	initrd	/initrd.img-2.6.32-31-preempt
}
menuentry 'Ubuntu, with Linux 2.6.32-31-preempt (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	echo	'Loading Linux 2.6.32-31-preempt ...'
	linux	/vmlinuz-2.6.32-31-preempt root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-31-preempt
}
menuentry 'Ubuntu, with Linux 2.6.32-30-preempt' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux	/vmlinuz-2.6.32-30-preempt root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro   quiet splash
	initrd	/initrd.img-2.6.32-30-preempt
}
menuentry 'Ubuntu, with Linux 2.6.32-30-preempt (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	echo	'Loading Linux 2.6.32-30-preempt ...'
	linux	/vmlinuz-2.6.32-30-preempt root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-30-preempt
}
menuentry 'Ubuntu, with Linux 2.6.31-11-rt' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux	/vmlinuz-2.6.31-11-rt root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro   quiet splash
	initrd	/initrd.img-2.6.31-11-rt
}
menuentry 'Ubuntu, with Linux 2.6.31-11-rt (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	echo	'Loading Linux 2.6.31-11-rt ...'
	linux	/vmlinuz-2.6.31-11-rt root=UUID=a6fd80e6-e5a2-4f46-9f6e-2ca824da83f1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.31-11-rt
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod raid
	insmod mdraid
	insmod ext2
	set root='(md0)'
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if sleep --verbose --interruptible 5 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

# /dev/md2: UUID="4b8da118-c3fd-4313-9239-9d091967bff0" TYPE="ext4" 
# /dev/md0: UUID="6b74e77e-a0f8-4ce9-941e-0e7fba116b48" TYPE="ext4" 

menuentry "Gentoo Linux" --class gnu-linux --class gnu --class os  { 
	recordfail
        insmod raid
        insmod mdraid
        insmod ext2
	set root='(md0)' 
	search --no-floppy --fs-uuid --set 6b74e77e-a0f8-4ce9-941e-0e7fba116b48
	linux /kernel-genkernel-x86_64-2.6.37-gentoo-r4 root=4b8da118-c3fd-4313-9239-9d091967bff0  ro
	initrd /initramfs-genkernel-x86_64-2.6.37-gentoo-r4
} 
### END /etc/grub.d/40_custom ###

==================== md0: Location of files loaded by Grub: ====================


    .1GB: boot/grub/core.img
    .2GB: boot/grub/grub.cfg
    .3GB: boot/initramfs-genkernel-x86_64-2.6.37-gentoo-r4
    .2GB: boot/initrd.img-2.6.31-11-rt
    .1GB: boot/initrd.img-2.6.32-28-generic
    .1GB: boot/initrd.img-2.6.32-30-generic
    .1GB: boot/initrd.img-2.6.32-30-preempt
    .3GB: boot/initrd.img-2.6.32-30-preempt-bfs
    .3GB: boot/initrd.img-2.6.32-31-generic
    .3GB: boot/initrd.img-2.6.32-31-preempt
    .1GB: boot/vmlinuz-2.6.31-11-rt
    .1GB: boot/vmlinuz-2.6.32-28-generic
    .1GB: boot/vmlinuz-2.6.32-30-generic
    .1GB: boot/vmlinuz-2.6.32-30-preempt
    .3GB: boot/vmlinuz-2.6.32-30-preempt-bfs
    .2GB: boot/vmlinuz-2.6.32-31-generic
    .2GB: boot/vmlinuz-2.6.32-31-preempt
    .1GB: grub/core.img
    .2GB: grub/grub.cfg
    .3GB: initramfs-genkernel-x86_64-2.6.37-gentoo-r4
    .2GB: initrd.img-2.6.31-11-rt
    .1GB: initrd.img-2.6.32-28-generic
    .1GB: initrd.img-2.6.32-30-generic
    .1GB: initrd.img-2.6.32-30-preempt
    .3GB: initrd.img-2.6.32-30-preempt-bfs
    .3GB: initrd.img-2.6.32-31-generic
    .3GB: initrd.img-2.6.32-31-preempt
    .1GB: vmlinuz-2.6.31-11-rt
    .1GB: vmlinuz-2.6.32-28-generic
    .1GB: vmlinuz-2.6.32-30-generic
    .1GB: vmlinuz-2.6.32-30-preempt
    .3GB: vmlinuz-2.6.32-30-preempt-bfs
    .2GB: vmlinuz-2.6.32-31-generic
    .2GB: vmlinuz-2.6.32-31-preempt

================================ md2/etc/fstab: ================================

# my /etc/fstab
/dev/md124	/		ext4	noatime			1	2
/dev/md123	/boot		ext4	defaults,noatime	0	1

proc		/proc		proc	defaults		0	0
shm		/dev/shm	tmpfs	nodev,nosuid,noexec	0	0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  9b 6e e7 f0 ac 2a 6e f7  d4 2e df 8b cf ea 29 09  |.n...*n.......).|
00000010  8f 82 c6 a1 b3 46 31 d6  4c 0a 2d 2f a5 e2 c9 bb  |.....F1.L.-/....|
00000020  11 b3 3d ea 14 6b 35 27  16 f6 3e a1 be eb cb cc  |..=..k5'..>.....|
00000030  65 b9 a8 ab 6c 96 63 5e  9a e7 c4 54 33 ee b2 85  |e...l.c^...T3...|
00000040  44 d0 00 00 00 00 09 70  4c 25 28 98 41 10 1e 07  |D......pL%(.A...|
00000050  8b 87 9a 46 d8 e6 c5 42  cf 22 7a 4e aa a8 ff ff  |...F...B."zN....|
00000060  ff aa 1c 25 fc 93 ce ac  ef f5 c9 8e 37 36 71 ec  |...%........76q.|
00000070  3c 9a 40 ad 00 00 00 90  49 72 d8 64 00 46 2c 8d  |<.@.....Ir.d.F,.|
00000080  11 96 1f 99 f9 2e 85 29  d8 73 4a 2c 2d 1a 44 3e  |.......).sJ,-.D>|
00000090  d4 2c 07 4f 13 03 51 24  65 2d 2b 19 97 8f 9b 0b  |.,.O..Q$e-+.....|
000000a0  d0 89 a9 03 a2 06 d4 57  e4 32 8d 24 27 62 eb de  |.......W.2.$'b..|
000000b0  fb 76 c7 d0 68 ff d3 e3  f9 ff 1d 69 93 26 d0 59  |.v..h......i.&.Y|
000000c0  5a bf 12 68 ce 8b 49 47  9d ea 21 57 64 36 ba 66  |Z..h..IG..!Wd6.f|
000000d0  0d 2d 78 28 5b c4 c5 3a  4c 51 b4 ec dd 96 87 24  |.-x([..:LQ.....$|
000000e0  c7 f6 bb fd 8a a7 9d c7  ba dd 6f 6a d4 63 af b7  |..........oj.c..|
000000f0  63 ff fb 90 60 f9 00 04  3c 55 d1 6b 0c 34 74 3e  |c...`...<U.k.4t>|
00000100  02 3a 2a 31 83 1e 8f 75  53 51 a7 b0 d3 58 c8 85  |.:*1...uSQ...X..|
00000110  ea 34 90 89 8a eb ec 00  00 80 00 72 84 e8 6e 3e  |.4.........r..n>|
00000120  04 14 bd 7b 27 e1 93 17  73 34 b4 e0 83 a0 0d 97  |...{'...s4......|
00000130  27 50 c1 8b d1 59 cf ff  ff fd e5 ff d4 96 3a 87  |'P...Y........:.|
00000140  37 76 f3 82 c7 03 21 f1  03 00 37 8c 45 88 00 00  |7v....!...7.E...|
00000150  00 02 53 bb 46 e8 2c 47  15 c5 8c 59 99 89 bd f1  |..S.F.,G...Y....|
00000160  7c 94 de 33 3a ad 88 b2  7a 91 09 a4 64 68 bc d5  ||..3:...z...dh..|
00000170  bb 3b d9 62 b5 f6 6a ca  fc 9f 0e da a0 d1 ef 31  |.;.b..j........1|
00000180  8c 81 21 ac 34 cf ff fa  2e e0 89 14 e8 8a 66 9b  |..!.4.........f.|
00000190  eb 70 f5 ee ee ef a3 a7  93 a4 82 d0 d3 74 a1 a6  |.p...........t..|
000001a0  bd 18 e8 20 29 62 c3 88  05 49 22 0b 44 58 98 22  |... )b...I".DX."|
000001b0  11 84 72 c3 8c e1 e4 0f  60 aa b1 62 e4 19 00 01  |..r.....`..b....|
000001c0  01 7c fd fe ff ff 02 00  00 00 5e 30 31 01 00 fe  |.|........^01...|
000001d0  ff ff 05 fe ff ff 60 30  31 01 72 13 7a 00 00 00  |......`01.r.z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb2

00000000  7c 4a 53 bf 2c e9 90 bf  52 4e 0c 40 9e af 87 c0  ||JS.,...RN.@....|
00000010  87 41 ae bf eb c0 88 c0  1b f5 68 bf 40 0d 8d bf  |.A........h.@...|
00000020  63 2f 06 40 f0 b1 13 40  aa d9 64 c0 bb d4 4f c0  |c/.@...@..d...O.|
00000030  dc f2 81 3f 93 03 29 3f  2f 72 aa 3f b6 11 56 c0  |...?..)?/r.?..V.|
00000040  83 ea 16 3f 0f 83 7c 40  c8 91 27 3e 2c 72 dd c0  |...?..|@..'>,r..|
00000050  9a 28 64 c0 50 ad 0c c0  fa 73 14 40 92 1e 8d c0  |.(d.P....s.@....|
00000060  d9 5d 72 3f f3 2a 2e c0  8e 6b 49 40 98 d4 8e c0  |.]r?.*...kI@....|
00000070  b3 5a 8d 3f 19 ca c8 c0  d3 18 d4 bf d4 b0 61 bf  |.Z.?..........a.|
00000080  95 42 34 c0 44 0c 4a c0  3d ce ba 3f b0 12 2e 40  |.B4.D.J.=..?...@|
00000090  87 52 ce 3f 54 24 08 bf  d8 72 50 c0 4d 6b e8 3e  |.R.?T$...rP.Mk.>|
000000a0  f6 9a 90 40 ae 53 7b be  ef 90 4f 3f 1d ef a8 3f  |...@.S{...O?...?|
000000b0  9e 5f a0 bf 00 a8 2e c0  27 ee 84 bf 99 dd 4d 3f  |._......'.....M?|
000000c0  c8 b2 08 c0 ac 03 1c 3f  c3 9b a8 bf 67 01 1d 3f  |.......?....g..?|
000000d0  d4 a2 9b c0 32 1a b0 c0  bc 69 30 40 b3 01 04 c0  |....2....i0@....|
000000e0  c2 17 07 40 3d 2e 71 bf  ee 85 9e bf d1 0f 0c 3f  |...@=.q........?|
000000f0  e6 be 38 bf 38 af b6 be  db 35 50 c0 b2 07 09 40  |..8.8....5P....@|
00000100  ad 3b 9b c0 08 04 81 be  bb 07 bb 3f 20 9d 96 3f  |.;.........? ..?|
00000110  cd c0 01 c0 38 eb 42 c0  17 27 55 c0 69 11 e9 bf  |....8.B..'U.i...|
00000120  3a 7a 11 40 b0 48 07 40  36 32 e9 3f 7c ad 53 c0  |:z.@.H.@62.?|.S.|
00000130  32 0d 98 bf 9c 09 a1 c0  54 3b 52 bf e2 71 55 be  |2.......T;R..qU.|
00000140  55 3e 19 40 25 a9 07 c0  1f b4 cf 3f 9f c5 0f 40  |U>.@%......?...@|
00000150  7f 7a 9c 3e a0 23 14 40  18 86 2d 40 e9 39 c4 be  |.z.>.#.@..-@.9..|
00000160  d4 20 7a bf b5 e4 88 3f  00 f0 8b bf ed 5b 99 c0  |. z....?.....[..|
00000170  d9 73 7f c0 b1 90 af c0  00 00 00 00 00 00 00 40  |.s.............@|
00000180  b6 56 e4 31 00 00 00 00  00 00 00 00 00 20 9c 40  |.V.1......... .@|
00000190  04 b5 28 00 5a 00 00 00  ab 28 a5 9d 04 2d 6b 9b  |..(.Z....(...-k.|
000001a0  48 31 00 00 c8 00 00 00  48 31 3b 20 63 6c 65 61  |H1......H1; clea|
000001b0  6e 65 64 24 49 64 3a 20  73 70 6c 69 74 53 00 01  |ned$Id: splitS..|
000001c0  01 7c fd fe ff ff 02 00  00 00 5e 30 31 01 00 fe  |.|........^01...|
000001d0  ff ff 05 fe ff ff 60 30  31 01 72 13 7a 00 00 00  |......`01.r.z...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 
```

---

### Post by oldfred on 2011-04-28
I do not understand RAID and which is md and sda etc.

But it seems like you only have one boot partition. You cannot do that. Each distribution has to have its own boot whether a separate partition or included in / (root).

The script is showing all the files in md0, Ubuntu in its /boot and Gentoo in / of md0. While the files are at different levels of / & /boot inside md0, I am not sure it can work without some files getting mixed up.

---

### Post by HankB on 2011-04-28
> **oldfred said:**
> I do not understand RAID and which is md and sda etc.Fair enough. But this is not a RAID issue.

> But it seems like you only have one boot partition. You cannot do that. Each distribution has to have its own boot whether a separate partition or included in / (root).Correct. there is only one /boot. I thought I could share that between distros since it basically holds initrd, kernel and grub info necessary to load those and point to the correct root. But perhaps that is wrong. I suppose I could repeat the Gentoo install with /boot not mounted so that it is self contained within it's own partition. I definitely will not have /boot mounted at any time I'm working with Gentoo.

> The script is showing all the files in md0, Ubuntu in its /boot and Gentoo in / of md0. While the files are at different levels of / & /boot inside md0, I am not sure it can work without some files getting mixed up.I'm not sure where you're seeing that, but perhaps this is causing some confusion:
```
hbarta@olive:~$ ls -l /boot
total 113816
...
lrwxrwxrwx 1 root root       1 2011-04-25 11:57 boot -> .
```

So files within /boot can appear at any desired level. ;) Otherwise both Ubuntu and Gentoo kernels are in /boot

thanks,
hank

---

### Post by srs5694 on 2011-04-28
Actually, it *is* possible to share a /boot partition between distributions. I've done it in the past. It's not generally recommended, though, because there are a number of problems associated with it. The biggest of these is generally the probability of the two distributions each trying to reconfigure the boot loader, perhaps using different boot loader versions and creating a mess of it. There's also a possibility of conflict over files with identical names in both distributions, like /boot/vmlinuz (the kernel); however, Ubuntu at least seems to append the version number to such filenames, which should minimize the risk of conflict. Since Gentoo tends to have users do things manually more often than not, you're less likely to unwittingly overwrite a critical /boot file in Gentoo than in many distributions.

Overall, I'd have to recommend against sharing a /boot partition between distributions. If somebody insisted on doing it in an Ubuntu/Gentoo dual-boot, I'd say to let Ubuntu manage it and to manually add Gentoo kernels to Ubuntu's /etc/grub.d/40_custom file if Ubuntu's GRUB scripts don't detect them automatically.

---

### Post by HankB on 2011-04-28
> **srs5694 said:**
> Actually, it *is* possible to share a /boot partition between distributions. I've done it in the past. It's not generally recommended, though, because there are a number of problems associated with it. The biggest of these is generally the probability of the two distributions each trying to reconfigure the boot loader, perhaps using different boot loader versions and creating a mess of it. There's also a possibility of conflict over files with identical names in both distributions, like /boot/vmlinuz (the kernel); however, Ubuntu at least seems to append the version number to such filenames, which should minimize the risk of conflict. Since Gentoo tends to have users do things manually more often than not, you're less likely to unwittingly overwrite a critical /boot file in Gentoo than in many distributions.That's pretty much what I thought. I did find that with /boot mounted during the Gentoo install, I could no longer boot Ubuntu and update-grub was not sufficient to fix whatever problem Gentoo caused. grub-install was required. Further, I did not install grub during the Gentoo installation as it does not use grub2.

> Overall, I'd have to recommend against sharing a /boot partition between distributions. If somebody insisted on doing it in an Ubuntu/Gentoo dual-boot, I'd say to let Ubuntu manage it and to manually add Gentoo kernels to Ubuntu's /etc/grub.d/40_custom file if Ubuntu's GRUB scripts don't detect them automatically.I will only ever copy the Gentoo kernel to /boot it necessary. If possible I will boot the Gentoo partition directly (from a RAID0.) Apparently that is possible as I was do so from the grub console. I just cannot figure out what to put in /etc/grub.d/40_custom to get grub to list Gentoo in the menu.

thanks,
hank

---

### Post by ecormier on 2011-07-31
Hi Hank, I'm using a dual boot with the Ubuntu boot loader as default, and I had the exact same problem at first until I figured out that you have to install grub on the gentoo partition for Ubuntu to locate it....just skip the last step "grub-install --no-floppy /dev/sda". Once you have emerged grub and edited /boot/grub/grub.conf, then try running update-grub in Ubuntu again....should all work automatically now

Eugene

---

### Post by HankB on 2011-08-01
> **ecormier said:**
> Hi Hank, I'm using a dual boot with the Ubuntu boot loader as default, and I had the exact same problem at first until I figured out that you have to install grub on the gentoo partition for Ubuntu to locate it....just skip the last step "grub-install --no-floppy /dev/sda". Once you have emerged grub and edited /boot/grub/grub.conf, then try running update-grub in Ubuntu again....should all work automatically now

Eugene
Thanks for the tip. I was pretty leery about trying anything like that since Ubuntu and Gentoo are on different Grub versions (unless that's changed.) I'll have to give that a shot.

---

