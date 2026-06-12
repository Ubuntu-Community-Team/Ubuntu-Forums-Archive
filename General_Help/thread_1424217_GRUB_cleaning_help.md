---
title: "GRUB cleaning help"
date: 2010-03-07
forum: General Help
---

### Post by yomnym on 2010-03-07
Im trying to remove some old kernels that i have showing up on my GRUB and cant seem to remove them, i used synaptic manager and removed my old kernels and now i only have a green square next to my current one, but the problem is that at the Boot screen it still shows the old ones. I'm attaching a few pics of my grub menu list and my synaptic manager linux-image list.  The one im currently using is 2.6.31-20-generic and the problem is that at the GRUB loading screen i show a 2.6.31-14 kernel. Thanks for any help you guys could provide me with.

---

### Post by Pollox on 2010-03-07
Did you also remove old linux-headers?  What version of Ubuntu are you running?  Are you using grub or grub2?  That entry about chainloading into grub2 makes me think your issue might be with that.  Also, you can try running "sudo update-grub" in terminal to update your entries, although if you removed kernels through Synaptic it should do that automatically.

---

### Post by yomnym on 2010-03-08
byt the old linux-headers do you mean if i went to synaptic manager and removed the old kernels?  If not then most probably i haven't removed the old headers, how would i go about doing that?  I did the 'sudo update-grub" a few times but still remains.  Im not sure which GRUB i have, how i can i find this out?  Thanks alot for your help, im very new to linux and every help i could get is a new skill i learn.  Sorry by the way i have 9.10 version of ubuntu.

---

### Post by steviefordi on 2010-03-08
This may not be what you're after but you can just comment out the grub menu options by putting a # at the start of the line.

Here I have commented out the menu options related to 2.6.27.16 and left two options for 2.6.27.17:

```
title		Ubuntu 8.10, kernel 2.6.27-17-generic
uuid		d6e0e481-95e7-48d6-a9cf-b96f0d38f5e8
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=d6e0e481-95e7-48d6-a9cf-b96f0d38f5e8 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-17-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-17-generic (recovery mode)
uuid		d6e0e481-95e7-48d6-a9cf-b96f0d38f5e8
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=d6e0e481-95e7-48d6-a9cf-b96f0d38f5e8 ro  single
initrd		/boot/initrd.img-2.6.27-17-generic

#title		Ubuntu 8.10, kernel 2.6.27-16-generic
#uuid		d6e0e481-95e7-48d6-a9cf-b96f0d38f5e8
#kernel		/boot/vmlinuz-2.6.27-16-generic #root=UUID=d6e0e481-95e7-48d6-a9cf-b96f0d38f5e8 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-16-generic
#quiet

#title		Ubuntu 8.10, kernel 2.6.27-16-generic (recovery mode)
#uuid		d6e0e481-95e7-48d6-a9cf-b96f0d38f5e8
#kernel		/boot/vmlinuz-2.6.27-16-generic #root=UUID=d6e0e481-95e7-48d6-a9cf-b96f0d38f5e8 ro  single
#initrd		/boot/initrd.img-2.6.27-16-generic

```

This means I will only have two options on my menu. You can of course remove the lines as well, but safer to comment them out.

---

### Post by oldfred on 2010-03-08
You still are using grub legacy to chainload into grub2. Grub2 is updated with the sudo update-grub not the menu.lst that you are using to chainload with into grub. Until you want to install grub2 to the MBR you will have to manually edit menu.lst.

---

### Post by 2hot6ft2 on 2010-03-08
> **yomnym said:**
> byt the old linux-headers do you mean if i went to synaptic manager and removed the old kernels?  If not then most probably i haven't removed the old headers, how would i go about doing that?  I did the 'sudo update-grub" a few times but still remains.  Im not sure which GRUB i have, how i can i find this out?  Thanks alot for your help, im very new to linux and every help i could get is a new skill i learn.  Sorry by the way i have 9.10 version of ubuntu.
The same way you did for the image there are 2 files for each that need to be marked for removal like this
linux-image-2.6.31-20-generic
and
linux-headers-2.6.31-20

It will update grub for you if you are using 9.10 which I see you said you are.
If not run
```
sudo update-grub
```
In a terminal
Applications > Accessories > Terminal

I only see 1 kernel in your pics. So are you referring to the memtest or the chainloader?

If you don't want the memtest to show up:
> # Omitting memtest86+: To prevent "memtest86+" entries in your Grub 2 menu, remove the "executable" bit from /etc/grub.d/20_memtest86+. You can do this via a file browser by selecting "Properties (right click), Permissions", or via the command line:
```
sudo chmod -x /etc/grub.d/20_memtest86+
```

From the Grub 2 Guide in my sig. below

---

### Post by yomnym on 2010-03-08
In the pics you only see one, the current kernel, but on the boot screen (black screen after i turn on pc) i still get the old kernel listed. 
 
(2hot) I see, i still have to remove the old linux-header for 2.6.31-14 kernel, is probably what im missing, thanks a lot for your posts.
 
Steviefordi.. on my boot menu.lst the old kernal doesn't show.. I know i could comment it out but is already erased from the list.
 
Im not sure what GRUB i have, it i have GRUB, how can i replace it with GRUB2? thanks a lot for your replies guys, you've been most helpful.

---

### Post by scouser73 on 2010-03-08
Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don’t need anymore.

The old kernels are deliberately left installed and on the menu so you can boot a previous kernel if you have trouble with a new one. But if the new one works, you can safely uninstall the old kernel, which will also result in the Grub menu being cleaned up.

Follow these steps to identify and remove any old kernels.

**1** - Go to **Terminal** and paste the following command: **uname -r**
It will print the version of the Linux kernel you are running, this is the one you want to keep. It should look something like this: ***2.6.20-16-generic***

**2** - Go to **Synaptic Package Manager** via the **System > Administration** menus

**3** - Paste this: **linux-image-2** into the search box of **Synaptic Package Manager**

**4** - Once you have located the old kernels, **hightlight** them and **right-click** then select **Mark For Complete Removal** then click **Mark** and then click **Apply**

The results should show every available and installed kernel. A green box on the left indicates that the package is installed. The only linux-image you want installed is the latest one.

[COLOR="Red"]**Be careful of what you remove. Ensure that you don’t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.**[/COLOR]

Your computer and Grub menu should now be free of old kernels.

---

### Post by yomnym on 2010-03-08
Thanks alot scouser, i appreicate your detail explenation..  i need that sort of thing since im new to unbuntu and linux for that mater.  Reps for you.

---

### Post by drs305 on 2010-03-08
As a newbie, another method that is really easy is to install an app called ubuntu-tweak. It's a very easy to use app that can tweak some of ubuntu's settings, including removing older kernels. It won't display the current kernel so it's pretty straightforward.

You can download it from:
[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

Once installed, you open it via Applications, System Tools, Ubuntu-Tweak.
Then select Package Cleaner from the left pane and "Clean Kernels" from the far right pane.

---

### Post by yomnym on 2010-03-08
Thanks for the tip drs, thats not a bad idea, since new kernels are going to be coming along all the time, is easier to have such a app.

---

### Post by yomnym on 2010-03-08
Man i still cant get the boot screen cleaned up, something has to be wrong... Here's a shot of my synaptic manager, i updated the GRUB via terminal, nothing.  I still have the old one showing up on the main booting black screen.  I took some screen shots of my synaptic.. can you please tell me why i still show a 2.6.31-14

---

### Post by drs305 on 2010-03-09
If you run the following script and post the results we can see what is on your system, including which versions of Grub you are using and what Grub configuration files it might be referencing.

Download and run meierfra.'s [boot info script]("http://bootinfoscript.sourceforge.net/"). Please post the results between code tags, which you can insert in your reply by clicking the **#** icon in the post's menu.

---

### Post by yomnym on 2010-03-09
I think i got it.  Thanks for your help, hopefully we could figure this out.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1681656b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   108,828,491   108,621,644   7 HPFS/NTFS
/dev/sda3         108,829,980   156,301,109    47,471,130   5 Extended
/dev/sda5         108,829,994   154,241,009    45,411,016  83 Linux
/dev/sda6         154,241,024   156,301,109     2,060,086  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7CA0F207A0F1C822                       ntfs       System Reserved               
/dev/sda2        1284FCE384FCCA6D                       ntfs                                     
/dev/sda5        63f96e36-6f93-437a-a8b3-552613ff1609   ext4                                     
/dev/sda6        868dbd9a-28e7-461f-8cf7-81f5ec5b71ec   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=63f96e36-6f93-437a-a8b3-552613ff1609 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=63f96e36-6f93-437a-a8b3-552613ff1609

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        63f96e36-6f93-437a-a8b3-552613ff1609
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=63f96e36-6f93-437a-a8b3-552613ff1609 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        63f96e36-6f93-437a-a8b3-552613ff1609
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=63f96e36-6f93-437a-a8b3-552613ff1609 ro  single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Chainload into GRUB 2
root        63f96e36-6f93-437a-a8b3-552613ff1609
kernel        /boot/grub/core.img

title        Ubuntu 9.10, memtest86+
uuid        63f96e36-6f93-437a-a8b3-552613ff1609
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 63f96e36-6f93-437a-a8b3-552613ff1609
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 63f96e36-6f93-437a-a8b3-552613ff1609
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=63f96e36-6f93-437a-a8b3-552613ff1609 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 63f96e36-6f93-437a-a8b3-552613ff1609
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=63f96e36-6f93-437a-a8b3-552613ff1609 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 63f96e36-6f93-437a-a8b3-552613ff1609
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=63f96e36-6f93-437a-a8b3-552613ff1609 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 63f96e36-6f93-437a-a8b3-552613ff1609
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=63f96e36-6f93-437a-a8b3-552613ff1609 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7ca0f207a0f1c822
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
UUID=63f96e36-6f93-437a-a8b3-552613ff1609 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=868dbd9a-28e7-461f-8cf7-81f5ec5b71ec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  56.7GB: boot/grub/core.img
  59.2GB: boot/grub/grub.cfg
  59.4GB: boot/grub/menu.lst
  56.7GB: boot/initrd.img-2.6.31-20-generic
  56.0GB: boot/vmlinuz-2.6.31-20-generic
  56.7GB: initrd.img
  56.0GB: vmlinuz
```

---

### Post by drs305 on 2010-03-09
Thanks for posting the boot info results. I half-expected to find a reference to the -14 kernel in an old menu.lst, since Grub 2 gets its information from existing kernels and grub menus (grub.cfg's and menu.lst's).

However, there isn't any reference to -14 in your old menu.lst. Looking at the grub.cfg file (from which the menu is generated), the reference to the -14 kernel exists in the 10_linux section of the file. This means Grub 2 is finding the -14 kernel (or remnants) in the root partition (as verified by the UUID of the menuentry).

First, you can verify the kernel you are currently using with:
```
uname -r
```
The next step is to verify that the -14 file(s) still reside in your root partition:
```
ls /boot/*2.6.31-14*
```
If you get returns, you need to delete the files. You can do it via the command line, but a safer method is probably to open your file browser as root (disregard the error messages in the terminal window as it opens):
```
gksu nautilus /boot
```
You can delete any of the files referencing the -14 kernel (linux-image-xxx, initrd.img-xxx, etc). Using SHIFT-DEL will bypass the root trash bin.

Run the following to update the grub menu after deleting the files:
```
sudo update-grub
```
Watch the terminal as Grub 2 finds existing kernels. You should not see any reference to the -14 kernel in the results as the command runs.

---

### Post by yomnym on 2010-03-09
This is a little frustrating, and weird.  Where can that -14 be at, i did it all, and nothing shows a 2.6.31-14 kernel anywhere.  I uploaded the pics of when i opened the browser nautilus via command line and also when i checked my kernel (uname -r) and nothing, after updating the grub (sudo update-grub) it looks like its suppose to be a clean boot screen but nothing.  I really appreciate your help, im going to take a pic of my boot screen so you see what im talking about.  Thanks

PS- Sorry the last pic is upside down, it looked normal in my pictures folder.

---

### Post by drs305 on 2010-03-09
There was a case in the early stages of Grub 2 where update-grub and grub-mkconfig produced different results. I would not expect a different result, but you could try it anyway. 
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

If you are done with Grub legacy, you can also rename, move or remove the /boot/grub/menu.lst file. I'd probably rename it to prevent G2 from trying to mine data from it.

---

### Post by yomnym on 2010-03-09
i'll try that command once im home
To rename it i just open it via command line and rename it?  menu**.lst anyhting like this?  It appears that my GRUB isn't using the menu.lst because no matter what changes i make to it, they wont reflect on the actual boot screen.
So do i have GRUB or GRUB2?  Can i remove GRUB?  Thanks for your help DRS, im checking out those guides you have in your signature to see if i learn something from it.

---

### Post by drs305 on 2010-03-09
> **yomnym said:**
> i'll try that command once im home
To rename it i just open it via command line and rename it?  menu**.lst anyhting like this?  It appears that my GRUB isn't using the menu.lst because no matter what changes i make to it, they wont reflect on the actual boot screen.
So do i have GRUB or GRUB2?  Can i remove GRUB?  Thanks for your help DRS, im checking out those guides you have in your signature to see if i learn something from it.

Since it's a system file owned by root, the way to rename it (for example to menu.lst.bak) would be:
```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

Yes, you are running Grub 2. You can see it listed in the first section of the boot info results. You will also see the version listed above the Grub 2 menu during boot if the menu is visible. Versions 1.96 or later are "Grub 2". You can also check after you've booted with the command:
```
grub-install -v
```

You can remove "grub" if you are using Grub 2 and not seeing the "Chainload to Grub 2" on the menu. Make sure you keep grub-pc (grub 2) and grub-common. After removing "grub", I'd just do a quick check to make sure /boot/grub/grub.cfg still exists before rebooting. It's easier to correct mistakes from a running system than trying to figure out why it won't boot.  ;-)

---

### Post by yomnym on 2010-03-09
Well before i go any further i ran the grub-install -v command and got a version 0.97 which i believe is still GRUB and not 2?  I though it was suppose to be grub 2?  Somethings wrong here.  Maybe this is why i still show this old kernel on my boot screen.

---

### Post by drs305 on 2010-03-10
> **yomnym said:**
> Well before i go any further i ran the grub-install -v command and got a version 0.97 which i believe is still GRUB and not 2?  I though it was suppose to be grub 2?  Somethings wrong here.  Maybe this is why i still show this old kernel on my boot screen.

Interesting. For now, don't uninstall grub since you have a working boot process. I am going to contact meierfra., who wrote and maintains the boot info script. There is an obvious discrepancy here and he is great at analyzing these situations. He can probably figure out why the script is reporting something different that "grub-install -v".

If he doesn't respond I can give you the instructions on how to remove/replace grub with grub2 if that is what you want to do, but we aren't at that point yet.

---

### Post by meierfra. on 2010-03-10
You are definitely using Grub2 for booting, but the Grub Legacy  programs are still on you  computer  (I'm not quite sure how that happens, maybe something went wrong when you upgraded from Grub Legacy to Grub2)

So I suggest to remove Legacy Grub and install Grub 2:

```
sudo apt-get purge grub
sudo apt-get install grub-pc
```

This should also update  "grub.cfg" and the old kernel should no longer appear on the Grub Menu.

---

### Post by yomnym on 2010-03-10
Well i could officially declare this problems SOLVED, i really want to express my appreciation, thank you guys for keep the Linux community progressing.  I hope one day i could be as much help to someone as you all have been to me.

---

### Post by drs305 on 2010-03-10
> **yomnym said:**
> Well i could officially declare this problems SOLVED

Glad it's finally fixed. I haven't seen the issue where grub incorrectly reported the version it was using.

You can mark the thread solved via the Thread Tools link at the top right of the original post.

> **yomnym said:**
> I hope one day i could be as much help to someone as you all have been to me.

That's how it generally works here, which is why this is such a great place to both learn and help.

---

### Post by yomnym on 2010-03-10
i agree one hundred percent, thanks again to all.

---

