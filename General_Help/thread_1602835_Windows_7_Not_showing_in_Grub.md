---
title: "Windows 7 Not showing in Grub"
date: 2010-10-21
forum: General Help
---

### Post by Pyroman1010 on 2010-10-21
I Currently am running Ubuntu 10.10 on a hard drive with three partitions. One with Ubuntu, a Media partition (Music, Videos, pictures, etc.) and the last is my Windows 7 installation. I can acess all of these partitions in nautilus as well. However when I start up my computer it automaticly loads into Ubuntu and when I manage to see Grub I only see 3 Entries Which are the Ubuntu kernel, Ubuntu recovery Kernal and memtest86+. How do I make Grub recognise my Windows 7 Installation?

---

### Post by drs305 on 2010-10-21
If you haven't done so already, while in Ubuntu open a terminal (Applications, Accessories, Terminal) and run this command:
```
sudo update-grub
```
If you aren't used to "sudo", it will ask for your password. Type it in the terminal and press ENTER. You won't see the characters as you type ...

Sometimes Grub 2 doesn't pick up Windows during the install. Running the above command after the install often does. If Grub2 does find it, the next time you boot it should be listed on the menu.

---

### Post by Pyroman1010 on 2010-10-21
Ok ran the command it did not find Windows still the same three entries. This is what the terminal brought up:
> Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done


---

### Post by drs305 on 2010-10-21
OK, try running this in a terminal to see if you have os-prober:
```
sudo os-prober
```
If you get a message saying that it isn't installed:
```
sudo apt-get install os-prober
```


If it runs, make sure the 30_os-prober file is executable. This is the file that actually looks for Windows when you run "update-grub".
```
sudo chmod +x /etc/grub.d/30_os-prober
```

Then try updating Grub again. If it finds Windows, you will see a message in the terminal as the command runs. Or after you can see the menu entries without booting by running this:
```
grep menuentry /boot/grub/grub.cfg
```

---

### Post by Pyroman1010 on 2010-10-21
Os-prober is installed and I ran it Windows is still not found

---

### Post by drs305 on 2010-10-22
I don't know why it isn't finding it. I'm assuming Windows works, as update-grub looks for files necessary for Windows to boot.

Please run the boot info script, which will tell us about Grub and your installs. If nothing else, it will give us enough info to build you a custom entry for Windows.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by oldfred on 2010-10-22
Lets run this as it will show everything related to booting about your system so we can see if something is missing:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Pyroman1010 on 2010-10-22
Here is the Results.txt
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/burg.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 142868735 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   299,894,594   299,894,532  83 Linux
/dev/sda2         299,894,784   557,326,979   257,432,196   7 HPFS/NTFS
/dev/sda3         557,327,041   976,768,064   419,441,024   f W95 Ext d (LBA)
/dev/sda5         557,327,043   976,768,064   419,441,022   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        c51f0eaf-e722-41cd-bbad-037c289e3237   ext4                                     
/dev/sda2        40442BAB442BA320                       ntfs       Media                         
/dev/sda3: PTTYPE="dos" 
/dev/sda5        12FE8073FE805141                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda2        /media/Media             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c51f0eaf-e722-41cd-bbad-037c289e3237
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set c51f0eaf-e722-41cd-bbad-037c289e3237
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c51f0eaf-e722-41cd-bbad-037c289e3237
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=c51f0eaf-e722-41cd-bbad-037c289e3237 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c51f0eaf-e722-41cd-bbad-037c289e3237
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=c51f0eaf-e722-41cd-bbad-037c289e3237 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c51f0eaf-e722-41cd-bbad-037c289e3237
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c51f0eaf-e722-41cd-bbad-037c289e3237
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=c51f0eaf-e722-41cd-bbad-037c289e3237 /               ext4    errors=remount-ro 0       1

=================== sda1: Location of files loaded by Grub: ===================


  73.1GB: boot/grub/core.img
 107.7GB: boot/grub/grub.cfg
   1.3GB: boot/initrd.img-2.6.35-22-generic
  73.1GB: boot/vmlinuz-2.6.35-22-generic
   1.3GB: initrd.img
  73.1GB: vmlinuz
```

---

### Post by drs305 on 2010-10-22
It appears you are using BURG and not grub. I think the command for updating it is
```
sudo update-burg
```
But you have a mixture of Grub and burg and I'm not sure if the BURG files are complete.

To install grub from the desktop:
```
sudo grub-install /dev/sda
```

---

### Post by Pyroman1010 on 2010-10-22
Ok sorry for that it still doesn't find windows. Results of terminal:

> Generating burg.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
done


I reinstalled GRUB though
Tried sudo update-grub again and Windows still has not been found

---

### Post by oldfred on 2010-10-22
Windows only boots from a primary partition and your install is in a logical partition. You are also missing these files that were either in a separate boot partition that was primary or another install of windows that was a primary partition. Windows will not repair and reinstall these files to a logical partition. Ubuntu works just fine from logical partitions.

/bootmgr /Boot/BCD

Since you have only 4 partitions I have seen some rewrite the partition table to convert your sda5 to sda3. Make sure you have good backups, if you want to try to do this.  You could then still create a small  sda4 extended partition and put swap into sda5.

Delete & recreate partition table - srs5694:
[http://ubuntuforums.org/showthread.php?t=1597557&highlight=fdisk](http://ubuntuforums.org/showthread.php?t=1597557&highlight=fdisk)
Use sfdisk to edit partitions
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt

---

### Post by Pyroman1010 on 2010-10-24
> **oldfred said:**
> Windows only boots from a primary partition and your install is in a logical partition. You are also missing these files that were either in a separate boot partition that was primary or another install of windows that was a primary partition. Windows will not repair and reinstall these files to a logical partition. Ubuntu works just fine from logical partitions.

/bootmgr /Boot/BCD

Since you have only 4 partitions I have seen some rewrite the partition table to convert your sda5 to sda3. Make sure you have good backups, if you want to try to do this.  You could then still create a small  sda4 extended partition and put swap into sda5.

Delete & recreate partition table - srs5694:
[http://ubuntuforums.org/showthread.php?t=1597557&highlight=fdisk](http://ubuntuforums.org/showthread.php?t=1597557&highlight=fdisk)
Use sfdisk to edit partitions
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
Backup partition table to text file
sudo sfdisk -d /dev/sda > PT.txt
So what exactly would I have to backup? And would I have to reinstall Windows, Ubuntu or both??

---

### Post by oldfred on 2010-10-24
Anytime you edit partitions there is a risk, especially low level editing.

If you just want to reinstall then you should only have to reinstall windows, but it has to be into a primary partition.

---

### Post by mr clark25 on 2010-10-24
to me, it sounds like re-installing grub would be a lot easier. i think the first link in my signature should help if you want to re-install grub.

i have tested the script mentioned there myself, and it seems to work. i just don't know if it will generate a new grub.cfg file. (this shouldnt be anything to worry about, as long as you have a live-cd/live-usb drive around)

---

### Post by Pyroman1010 on 2010-10-24
What would you suggest a novice to do I don't want to mess this up

---

### Post by oldfred on 2010-10-24
It looks like you had wubi. Back up wubi's root.disk from the windows partition if you have any data you want saved from that. Back up everything you want to save from your windows install. Delete the windows partition and the extended partition and create a new sda3 that is NTFS, set boot flag on. 

If you make it exactly the same size as your existing partition, (see details in results.txt),  I would be curious if gparted just writes partition table and your windows is still sitting in the new partition, and then it might be repairable. I doubt it, but it may be worth rerunning the boot script after using gparted just to see it it sees the old windows. If not reinstall windows in the new NTFS sda3 partition.

Later you may want to shrink windows by a couple of GB and create a new extended and put a logical 2GB swap partition in.

---

### Post by Pyroman1010 on 2010-10-24
Ok so how would I go about doing so? I am still a newbie when it comes to using terminal

---

### Post by oldfred on 2010-10-25
Only after you have backed up all your data:

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)

---

### Post by Pyroman1010 on 2010-10-26
Ok I solved it. What I ended up doing was:

   1)Backup my files
   2)Delete my Windows partion using gparted
   3)Create Two new partions One for Windows and a 2GB partion for linux swap
   4)Reinstall Windows
   5)Add Ubuntu 10.10 entry using Easy BCD

For those who are curious here is my new disk layout:
>    Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18668   149947266   83  Linux
/dev/sdb2           18668       34692   128716098    7  HPFS/NTFS
/dev/sdb3   *       34693       60541   207625216    7  HPFS/NTFS
/dev/sdb4           60541       60802     2097152   82  Linux swap / Solaris


Thanks oldfred and drs305 for the help.

---

