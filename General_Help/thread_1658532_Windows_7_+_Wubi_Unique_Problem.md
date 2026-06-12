---
title: "Windows 7 + Wubi Unique Problem"
date: 2011-01-02
forum: General Help
---

### Post by jordan912003 on 2011-01-02
Hi, I have this rather unique problem regarding Wubi. I had it installed on my Windows 7 machine a while back, but decided to uninstall it. From that point on, I've only been using Windows 7 on that machine and it auto-booted it without a problem. Months later (today), I turned on my computer only to find that it redirects me to an old-fashioned Ubuntu install (with the blue background), mentioning Wubi on some places, such as in the GRUB loader that appears if I quickly press escape before the installation process begins. On the GRUB loader, there is only the Ubuntu option possible. I click "e" to edit the boot option and it gives me the following list:

find --set-root /wubi/linux
kernel /wubi/linux find=/wubi/linux quiet ro
initrd /wubi/initrd.gz
boot

If I let the installer proceed, however, it gives me the option to download the install files for Ubuntu from one of the mirrors in its source list. All the sources are something like: us.archive.ubuntu.com (for USA), ca.archive.ubuntu.com (for Canada), etc. However, the installer tells me that the mirror is not active if I try to select any mirror. Also, it does not let me edit neither the mirror location immediately nor to edit sources.list (since I cannot access sources.list for some reason).

So basically I cannot log in Windows AND Ubuntu in order to change the bootloader. The GRUB menu only shows Ubuntu and does not let me add another boot location.

Additional details:
- No one else has access to my computer, so no one could mess up the bootloader.
- I use antivirus on Windows 7 and only visit safe sites (Facebook, Youtube, etc.), always update Windows  and don't download potentially harmful content, so I don't believe anyone has hacked me and played around with the bootloader.
- I don't have backup for my OS (yeah, I know, silly me).
- Windows was on partition C:\ and Wubi was on partition D:\ of the same hard disk.

If anyone thinks they can help me, please do, I have important files on that PC that I need to use ASAP.
Thank you.

---

### Post by drs305 on 2011-01-02
If you have an Ubuntu installation CD/LiveCD, you can boot to the Desktop, open the Nautilus file browser in Places click on the Windows partition to mount it. From there you should be able to look at your c:\boot.ini file to see what is in it. You should also be able to  access your other files.

If you can't view the Windows files in that manner, you can also mount the Windows partition via the command line:
Open a terminal (Applications, Accessories, Terminal), and run these commands to mount your Windows partition, assuming sda1 is your Windows partition:
```
sudo mkdir /media/win 
sudo mount /dev/sda1 /media/win
nautilus /media/win &
```

If you can't figure out where to go next, download and run the boot info script and post the RESULTS.txt:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

It would be best to wait until we see the RESULTS.txt before you take any further action, but if you really want to try to get Windows back immediately and you think the Windows menu is being completely bypassed, you can use the lilo bootloader to point to your Windows boot files:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
Don't run any of the other commands which may be suggested by lilo during the installation.

---

### Post by jordan912003 on 2011-01-02
Alright, I ran Ubuntu Live CD as well as the script and here is RESULTS.txt:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /menu.lst /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   409,602,047   409,600,000   7 HPFS/NTFS
/dev/sda2         409,602,048   976,771,071   567,169,024   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        66608AED608AC2F3                       ntfs                                     
/dev/sda2        F2A8757EA87541E1                       ntfs       Multimedia                    
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/win               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sr0         /media/apt               iso9660    (ro)


================================ sda1/menu.lst: ================================

## default num 
# Set the default entry to the entry number NUM. Numbering starts from 0, and 
# the entry number 0 is the default if the command is not used. 
# 
# You can specify 'saved' instead of a number. In this case, the default entry 
# is the entry saved with the command 'savedefault'. 
# WARNING: If you are using dmraid do not change this entry to 'saved' or your 
# array will desync and will not let you boot your system. 
default        0 
 
## timeout sec 
# Set a timeout, in SEC seconds, before automatically booting the default entry 
# (normally the first entry defined). 
timeout        1 
 
## hiddenmenu 
# Hides the menu by default (press ESC to see the menu) 
hiddenmenu 
 
## Pretty colours 
#color cyan/blue white/blue 
 
#### KERNEL PARAMETERS #### 
 
# the /folder/path paramater must be matched in the following 3 lines: 
# 
#find --set-root /folder/path/linux 
#kernel /folder/path/linux find=/folder/path/linux 
#initrd /folder/path/linux 
# 
#you must replace /folder/path with the path where the files where installed 
#do not use the same folder name on different partitions 
 
## To specify the ISO (otherwise the first one in the folder will be used) 
#setup_iso=setup.iso 
 
## To specify the root harddisk image(otherwise root.img is assumed) 
#root_img=root.img 
 
## To specify the home harddisk image (otherwise home.img is assumed) 
#home_img=home.img 
 
## To specify the swap harddisk image (otherwise swap.img is assumed) 
#home_img=swap.img 
 
## To specify extra harddisk image (otherwise extra.img is assumed) 
#extra_img=extra.img 
 
## Debug 
#pause_for_debug debug 
 
#### MENU ITEMS BELOW HERE #### 
 
title Ubuntu 
find --set-root /wubi/linux 
kernel /wubi/linux find=/wubi/linux quiet ro 
initrd /wubi/initrd.gz 
boot 

================================ sda1/boot.ini: ================================

[operating systems] 
c:\grldr="Ubuntu" 
[boot loader] 
timeout=15 

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: menu.lst

```

---

### Post by drs305 on 2011-01-02
Windows is still your bootloader but for some reason Windows has been eliminated from your boot.ini file. Here is its current content, which only provides the Wubi option:
> 
[operating systems] 
c:\grldr="Ubuntu" 
[boot loader] 
timeout=15 


There should be a Windows entry before the Wubi entry. I don't have a good example of the Windows entry, but someone will hopefully provide one for you or you can find an example of the boot.ini file for your version of Windows.

Note: If you edit the boot.ini file from Ubuntu, you might want to use nano instead of gedit. I believe gedit can leave 'end of line' markers which may not be compatible with Windows. Again, a Windows user can tell you  if it is a concern or not. Use nano with "nano /mnt/win/boot.ini" if you mounted the Windows partition as I previously described. Make the changes. When you are ready to save, CTRL-x then Y to save.

---

### Post by jordan912003 on 2011-01-02
Yeah, I noticed that too. After some Googling, it appears that Windows 7 does not use boot.ini anymore. I think it was created there because I used the EasyBCD program a while back. Windows 7 now uses bootmgr.dll and I can't modify that any other way. However, EasyBCD apparently created 1. grub.exe, 2. the updated version of grub (whose name I don't remember at the moment), and 3. the Ubuntu bootloader file (whose name also eludes my mind). I simply deleted them after mounting my C:\ drive and I could login back to my Windows 7 again.

Thank you for helping me.

Solved.

---

### Post by drs305 on 2011-01-02
Glad it's working. I didn't pick up on the boot.ini/Win7 relationship but then I've forgotten most of my Windows knowledge and never used W7. 

You can mark a thread solved via the 'Thread Tools' link near the top right of the original post.

Happy Ubuntu-ing!

---

