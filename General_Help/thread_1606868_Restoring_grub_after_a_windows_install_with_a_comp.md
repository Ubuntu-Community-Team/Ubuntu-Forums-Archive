---
title: "Restoring grub after a windows install with a complex partition setup"
date: 2010-10-27
forum: General Help
---

### Post by OEP on 2010-10-27
Hello

My partition setup:

SDA:
1. Windows 7
2. /boot (ext2)

SDB
1. / (ext4)
2. /home (ext4)
3. swap

This rough partition setup was working fine after installing Ubuntu 10.04. However, windows crapped out and I installed Windows 7 which of course broke grub2.

I have followed the recommended guides. I boot into Ubuntu Live using a USB key. I mount SDA2 at /mnt/boot. I do:

$> grub-install --root-directory=/mnt /dev/sda

So now grub is on the MBR of SDA.

The first time I did this I got a functional grub2 prompt with no obvious ways to boot into any OS. Afterwards I have gotten a "[UUID]: device not found" error upon booting.

I understand that the documentation recommends using "update-grub2" to fix the UUID error. However, this returns an error message when I run it in the Live environment which says "grub-probe: Cannot find a device for /".

Any ideas?

Thanks! I am turning in for the night so I am sorry if I can't answer any questions for a while, and I may not have the most convenient access to my computer until later in the day tomorrow.

---

### Post by oldfred on 2010-10-27
Post this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

For desktops I prefer not to have a separate /boot. You have to also mount that when reinstalling grub2 and that is just one more complication. I also prefer to have each hard drive stand alone. Or the MBR of a drive boots the system on that drive.

---

### Post by OEP on 2010-10-28
Neat script :)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/core.img

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sdf1 starts 
                       at sector 1. But according to the info from fdisk, 
                       sdf1 starts at sector 33. According to the info in the 
                       boot sector, sdf1 has 247322 sectors.. But according 
                       to the info from the partition table , it has 253406 
                       sectors.
    Operating System:  
    Boot files/dirs:   

sdc: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   486,319,679   486,319,617   7 HPFS/NTFS
/dev/sda2         486,326,270   488,280,063     1,953,794   5 Extended
/dev/sda5         486,326,272   488,280,063     1,953,792  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   117,186,559   117,184,512  83 Linux
/dev/sdb2         117,188,606   312,580,095   195,391,490   5 Extended
/dev/sdb5         117,188,608   121,186,303     3,997,696  82 Linux swap / Solaris
/dev/sdb6         121,188,352   312,580,095   191,391,744  83 Linux


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 129 MB, 129892352 bytes
16 heads, 16 sectors/track, 991 cylinders, total 253696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             33       253,439       253,407   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        589045D79045BC6E                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        8867145e-9a7e-4182-b94c-673506ca50cf   ext2                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8d93cc3a-01d3-4439-ad83-80d0e1c1c429   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        e7c7507d-6f6b-4410-82d0-eb66f6ac4ade   swap                                     
/dev/sdb6        8a8bcb52-9c8c-4f7f-afb3-04a7ce6299eb   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc         2C83-E21B                              vfat                                     
/dev/sdf1        4A40-ED56                              vfat       PHONE CARD                    
/dev/sdf: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc         /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdf1        /media/PHONE CARD        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,umask=0077)


=================== sda5: Location of files loaded by Grub: ===================


 249.1GB: grub/core.img

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=8d93cc3a-01d3-4439-ad83-80d0e1c1c429 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
# /dev/sda3 /boot           ext2    defaults        0       2
# /home was on /dev/sdb6 during installation
UUID=8a8bcb52-9c8c-4f7f-afb3-04a7ce6299eb /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=e7c7507d-6f6b-4410-82d0-eb66f6ac4ade none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  6f 6c 65 61 6e 0a 20 20  20 20 20 20 3c 2f 73 70  |olean.      </sp|
00000010  61 6e 3e 0a 20 20 20 20  20 20 3c 73 70 61 6e 20  |an>.      <span |
00000020  63 6c 61 73 73 3d 22 73  79 6d 70 61 64 22 3e 69  |class="sympad">i|
00000030  73 52 65 6d 6f 76 65 64  3c 2f 73 70 61 6e 3e 0a  |sRemoved</span>.|
00000040  20 20 20 20 20 20 3c 73  70 61 6e 20 63 6c 61 73  |      <span clas|
00000050  73 3d 22 6e 6f 72 6d 61  6c 22 3e 28 29 3c 2f 73  |s="normal">()</s|
00000060  70 61 6e 3e 0a 20 20 20  20 3c 2f 68 34 3e 0a 20  |pan>.    </h4>. |
00000070  20 20 20 20 20 3c 64 69  76 20 63 6c 61 73 73 3d  |     <div class=|
00000080  22 61 70 69 2d 6c 65 76  65 6c 22 3e 0a 20 20 20  |"api-level">.   |
00000090  20 20 20 20 20 0a 20 20  53 69 6e 63 65 3a 20 3c  |     .  Since: <|
000000a0  61 20 68 72 65 66 3d 22  2e 2e 2f 2e 2e 2f 2e 2e  |a href="../../..|
000000b0  2f 2e 2e 2f 67 75 69 64  65 2f 61 70 70 65 6e 64  |/../guide/append|
000000c0  69 78 2f 61 70 69 2d 6c  65 76 65 6c 73 2e 68 74  |ix/api-levels.ht|
000000d0  6d 6c 23 6c 65 76 65 6c  31 22 3e 41 50 49 20 4c  |ml#level1">API L|
000000e0  65 76 65 6c 20 31 3c 2f  61 3e 0a 0a 20 20 20 20  |evel 1</a>..    |
000000f0  20 20 3c 2f 64 69 76 3e  0a 20 20 20 20 3c 64 69  |  </div>.    <di|
00000100  76 20 63 6c 61 73 73 3d  22 6a 64 2d 64 65 74 61  |v class="jd-deta|
00000110  69 6c 73 2d 64 65 73 63  72 22 3e 0a 20 20 20 20  |ils-descr">.    |
00000120  20 20 0a 20 20 3c 64 69  76 20 63 6c 61 73 73 3d  |  .  <div class=|
00000130  22 6a 64 2d 74 61 67 64  61 74 61 20 6a 64 2d 74  |"jd-tagdata jd-t|
00000140  61 67 64 65 73 63 72 22  3e 3c 70 3e 52 65 74 75  |agdescr"><p>Retu|
00000150  72 6e 73 20 77 68 65 74  68 65 72 20 74 68 69 73  |rns whether this|
00000160  20 6e 6f 64 65 20 68 61  73 20 62 65 65 6e 20 72  | node has been r|
00000170  65 6d 6f 76 65 64 20 62  79 20 69 6e 76 6f 6b 69  |emoved by invoki|
00000180  6e 67 20 74 68 65 20 6d  65 74 68 6f 64 20 3c 63  |ng the method <c|
00000190  6f 64 65 20 63 6c 61 73  73 3d 22 43 6f 64 65 20  |ode class="Code |
000001a0  70 72 65 74 74 79 70 72  69 6e 74 22 3e 72 65 6d  |prettyprint">rem|
000001b0  6f 76 65 4e 6f 64 65 28  29 3c 2f 63 6f 64 00 fe  |oveNode()</cod..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d0 1d 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sda5

00000000  20 20 20 20 20 3c 73 70  61 6e 20 63 6c 61 73 73  |     <span class|
00000010  3d 22 73 79 6d 70 61 64  22 3e 6b 65 79 73 53 70  |="sympad">keysSp|
00000020  69 3c 2f 73 70 61 6e 3e  0a 20 20 20 20 20 20 3c  |i</span>.      <|
00000030  73 70 61 6e 20 63 6c 61  73 73 3d 22 6e 6f 72 6d  |span class="norm|
00000040  61 6c 22 3e 28 29 3c 2f  73 70 61 6e 3e 0a 20 20  |al">()</span>.  |
00000050  20 20 3c 2f 68 34 3e 0a  20 20 20 20 20 20 3c 64  |  </h4>.      <d|
00000060  69 76 20 63 6c 61 73 73  3d 22 61 70 69 2d 6c 65  |iv class="api-le|
00000070  76 65 6c 22 3e 0a 20 20  20 20 20 20 20 20 0a 20  |vel">.        . |
00000080  20 53 69 6e 63 65 3a 20  3c 61 20 68 72 65 66 3d  | Since: <a href=|
00000090  22 2e 2e 2f 2e 2e 2f 2e  2e 2f 2e 2e 2f 67 75 69  |"../../../../gui|
000000a0  64 65 2f 61 70 70 65 6e  64 69 78 2f 61 70 69 2d  |de/appendix/api-|
000000b0  6c 65 76 65 6c 73 2e 68  74 6d 6c 23 6c 65 76 65  |levels.html#leve|
000000c0  6c 31 22 3e 41 50 49 20  4c 65 76 65 6c 20 31 3c  |l1">API Level 1<|
000000d0  2f 61 3e 0a 0a 20 20 20  20 20 20 3c 2f 64 69 76  |/a>..      </div|
000000e0  3e 0a 20 20 20 20 3c 64  69 76 20 63 6c 61 73 73  |>.    <div class|
000000f0  3d 22 6a 64 2d 64 65 74  61 69 6c 73 2d 64 65 73  |="jd-details-des|
00000100  63 72 22 3e 0a 20 20 20  20 20 20 0a 20 20 3c 64  |cr">.      .  <d|
00000110  69 76 20 63 6c 61 73 73  3d 22 6a 64 2d 74 61 67  |iv class="jd-tag|
00000120  64 61 74 61 20 6a 64 2d  74 61 67 64 65 73 63 72  |data jd-tagdescr|
00000130  22 3e 3c 70 3e 52 65 74  75 72 6e 73 20 61 6e 20  |"><p>Returns an |
00000140  61 72 72 61 79 20 6f 66  20 61 6c 6c 20 70 72 65  |array of all pre|
00000150  66 65 72 65 6e 63 65 20  6b 65 79 73 20 6f 66 20  |ference keys of |
00000160  74 68 69 73 20 6e 6f 64  65 20 6f 72 20 61 6e 20  |this node or an |
00000170  65 6d 70 74 79 20 61 72  72 61 79 20 69 66 0a 20  |empty array if. |
00000180  6e 6f 20 70 72 65 66 65  72 65 6e 63 65 73 20 68  |no preferences h|
00000190  61 76 65 20 62 65 65 6e  20 66 6f 75 6e 64 2e 20  |ave been found. |
000001a0  54 68 65 20 63 61 6c 6c  65 72 20 6f 66 20 74 68  |The caller of th|
000001b0  69 73 20 6d 65 74 68 6f  64 20 73 68 6f 75 6c 64  |is method should|
000001c0  20 65 6e 73 75 72 65 20  74 68 61 74 0a 20 74 68  | ensure that. th|
000001d0  69 73 20 6e 6f 64 65 20  68 61 73 20 6e 6f 74 20  |is node has not |
000001e0  62 65 65 6e 20 72 65 6d  6f 76 65 64 2e 3c 2f 70  |been removed.</p|
000001f0  3e 3c 2f 64 69 76 3e 0a  20 20 3c 64 69 76 20 63  |></div>.  <div c|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdg
```

At this point I have attempted a boot repair via the Windows disk which apparently did not overwrite grub, so at present when I boot from sda I get a grub console with no error messages. I might be able to boot an OS from there but I don't know the commands anymore :P

EDIT: I can boot my Windows partition fine (not sure about Ubuntu). If there were some way I could understand the cryptic grub.cnf file I think I could manually hack in the info it needs.

---

### Post by oldfred on 2010-10-28
Even though you have grub in sda & sdb neither point to a partition with a grub.cfg file, so grub did not install correctly.

When you have a separate /boot partition you have to find instructions that include mounting that partition as part of the reinstall of grub2. Since you are missing grub.cfg I think you also need to reinstall grub2. I would suggest then installing the kernels to your / (root) partition eliminating the /boot partition.

You will have to use a liveCD and chroot into your system, then you can reinstall grub & kernels. Or you can copy kernels back from /boot to / partition in to /boot.

kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

kansasnoob's change sda5 to correct partition (needs change if separate /boot)
sudo mount /dev/sdb6 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

Once chrooted:

Commands once in chroot:
#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories & 
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

I prefer to have grub in the same drive as the install so you may want to change to sdb:
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda
update-grub
sudo grub-mkconfig -o /boot/grub/grub.cfg

sudo dpkg-reconfigure grub-pc

Good example of chroot and grub reinstall by drs305
[http://ubuntuforums.org/showthread.php?t=1573100](http://ubuntuforums.org/showthread.php?t=1573100)

---

### Post by OEP on 2010-11-01
I followed drs345's guide and it proved to be quite helpful to get grub in a more working state!

However, apparently grub is not finding Ubuntu as a bootable item so it is not listed in the menu. :(

I saw that the SATA port my Ubuntu disk was on was not enabled in BIOS, which I thought might have had something to do with it. This went unnoticed for some time because I was able to see my Ubuntu disk just fine from inside the LiveCD, and I assume previously I was able to boot to it.

Anyway, after enabling the correct SATA port and repeating drs345's method, Windows 7 is the only bootable item in grub.

---

### Post by oldfred on 2010-11-01
Have you set BIOS this way?
The BIOS mode for the disc was set to AUTO. Changed it to LBA. Then it worked.

Rerun boot script so we can see what updates are there. Are you booting windows thru the grub menu?

---

### Post by OEP on 2010-11-01
Ah, I have not thought to change the disk mode yet. I am in class for the remainder of the day so I cannot try it just yet. Given that I could dual boot just fine upon initial install, would changing the disk mode help? I will try this regardless and let you know the result. As well, I will post the results of the boot script.

I am able to boot Windows 7 via the menu that grub presents to me. I suspect I could use the grub console to boot Ubuntu as well if I knew how.

---

### Post by oldfred on 2010-11-01
If we get the grub menu, we are probably beyond boot issues and into system booting issues. Teh most common issue is video related, and adding parameters on the boot line in the grub menu often help.

On first boot after install, press e on getting the GRUB bootloader menu. (hold shift key from BIOS if not shown)
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

[http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/](http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/)
[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

(from Fedora)
All drivers: nomodeset - this will disable the kernel modesetting feature and drop the user back to the old X.org infrastructure and behaviour. 
nouveau.modeset=1

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset 
    * Generic: xforcevesa or nouveau.modeset=0
    * Radeon: radeon.modeset=0

The nVidia nForce is not a graphical chip, but a chipset, so using the fix for the nvidia graphics card did not work.
The generic one did.

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

---

