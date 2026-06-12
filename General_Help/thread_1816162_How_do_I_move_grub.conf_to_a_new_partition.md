---
title: "How do I move grub.conf to a new partition?"
date: 2011-08-01
forum: General Help
---

### Post by cjack2964 on 2011-08-01
Hi, at the moment I am trying to create a script on the Win7 partition of my dual booted laptop that will allow me to change the default of Grub2 OS to ubuntu.  To do this I need to transfer the grub configuration files to a small partition which windows can access.

There are several tutorials online that show me how to do this with grub legacy, but these are not very clear on how to set the new configuration location in grub, and I am a little wary about touching my boot loader without knowing for sure what I am doing.

Another option I have come across is to chainload grub legacy with grub2 so I can make changes to grub legacy (which I've heard is generally easier to get along with) and test my configuration before I change loaders.

Which of these would you suggest? And if I should just make the changes to grub2 then what will be the difference between this and the process of grub legacy?

---

### Post by ajgreeny on 2011-08-01
I'm not quite sure what you're trying to do, but it sounds as if you don't want Ubuntu to be the OS to which grub boots by default.  If that is right, you don't need to mess around with the strange, circuitous route you are suggesting; just install startup-manager from the repos.

I am not certain about this, but I don't think you can put the grub configuration files on a partition that is readable by windows, as all the linux permissions, which could be essential for the correct working of grub, can only be enabled on a linux filesystem, which windows can not read.

---

### Post by cjack2964 on 2011-08-01
Hi, thank you for the reply, I think I might not have been clear.

I want to edit the configuration file from windows only temporarily, so that I can choose which os it will boot from inside win7 or ubuntu. I need to do this so I can use both OSes from a VNC environment.

There is a program for windows called ext2ifs that will let me edit files on ext type partitions, like the small one i have set aside for grub. There are also text editors for windows that can preserve the line endings used in the Linux filesystem which I can use to edit the configuration file.

Right now the only issue I am having I how to move the grub files successfully to the new partition.

---

### Post by ajgreeny on 2011-08-01
> **cjack2964 said:**
> Hi, thank you for the reply, I think I might not have been clear.

I want to edit the configuration file from windows only temporarily, so that I can choose which os it will boot from inside win7 or ubuntu. I need to do this so I can use both OSes from a VNC environment.

There is a program for windows called ext2ifs that will let me edit files on ext type partitions, like the small one i have set aside for grub. There are also text editors for windows that can preserve the line endings used in the Linux filesystem which I can use to edit the configuration file.

Right now the only issue I am having I how to move the grub files successfully to the new partition.
OK, I think I understand, but having got shot of windows a long while ago, I'm not the right person to try and help you any more.  I do recall ext2ifs not working very well when I did try it a long time ago, and certainly not finding ext4 partitions when they first appeared, but things may have changed by now.

---

### Post by cjack2964 on 2011-08-01
Then I guess the more simplistic version of my question for now is how do I move /boot to another partition and inform grub (and burg) of the change? Thank you for the help though.

---

### Post by oldfred on 2011-08-01
The only way that might work is to install a small grub legacy or grub2 only boot on FAT32 or NTFS. Then you can use scripts to edit menu.lst or grub.cfg on which to boot.

I have installed grub2 in both FAT32 & NTFS on my flash drives. But I have to manual edit grub.cfg. I use it to boot ISO and a windows repair flash.

My windows recovery grub.cfg
```
menuentry "Microsoft Windows Recovery" {
      set root=(hd0,1)
      chainloader --force +1
}


menuentry " " {
set root= 
}

menuentry "ubuntu-9.10-desktop-i386.iso" {
    set isofile="/ISO/ubuntu-9.10-desktop-i386.iso"
    insmod ext2
    loopback loop (hd0,2)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.gz
}

```

On my other grub.cfg I have these as options:

set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

So "all" you have to do is in windows edit set default line and with bash in Linux edit set default line. I do not know how to do either.

---

### Post by cjack2964 on 2011-08-02
Old red, thank you so much for that solution, I have it saved so I can try it in the near future, but I'm afraid I got impatient and attempted to move my entire boot directory based on some instructions I found in the forum.

I failed to configure grub right, (I forgot to account for burg which I use for theming) and entered grub rescue, and double fail, I can't find the paper where I wrote down my ubuntu menu entry name.  Essentially I'm completely lost on what to do next, but I've booted a live cd and am looking for my best option.

In this process I began to wonder if I couldnt simply have used to live cd to install grub in the first place, and it turns out I can, so thank you both for the help, I'm going to mark this thread as solved because I can't go any farther with it, but I've learned a valuable lesson about backups and safety precautions lol.

---

### Post by oldfred on 2011-08-02
Whenever you get into the inner workings of grub, multiple systems, and/or mutliple drives you should run this script. It documents your system and shows where grub is installed which is difficult to see any other way.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by cjack2964 on 2011-08-02
I'm working on it as we speak and I will post the results later this evening, I've made a few small breakthroughs but I still can't load my ubuntu partition at all.

Thanks again oldfred.

---

### Post by oldfred on 2011-08-02
Ubuntu and I think Debian has links to the most current installed kernel in / (root). You can then manual create a boot to the most current kernel without having to edit on every kernel update.

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

### Post by cjack2964 on 2011-08-02
Here is the output from running th bash script

```
    Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos4)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048     2,459,647     2,457,600   7 NTFS / exFAT / HPFS
/dev/sda2           2,459,648   529,457,151   526,997,504   7 NTFS / exFAT / HPFS
/dev/sda3         529,459,198   604,942,335    75,483,138   f W95 Extended (LBA)
/dev/sda5         529,459,200   575,825,919    46,366,720  83 Linux
/dev/sda6         575,827,968   604,942,335    29,114,368  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        006478CB6478C4C6                       ntfs       SYSTEM_DRV
/dev/sda2        663C7B443C7B0E75                       ntfs       Windows7_OS
/dev/sda5        7e130884-a636-4dce-a8a6-5808e56073db   ext4       
/dev/sda6        e47c8d57-3341-4ebb-a008-0738aed98ac9   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set default="${saved_entry}"
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
  insmod video_bochs
  insmod video_cirrus
}

terminal_input console
terminal_output console
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=30
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 006478CB6478C4C6
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 663C7B443C7B0E75
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
set gfxmode="640x480"
set gfxfont="Unifont Regular 16"
loadfont /boot/burg/fonts/unifont.pf2
loadfont /boot/burg/fonts/aqui.pf2
loadfont /boot/burg/fonts/edges.pf2
loadfont /boot/burg/fonts/lime.pf2
loadfont /boot/burg/fonts/7x13B.pf2
loadfont /boot/burg/fonts/smoothansi.pf2
loadfont /boot/burg/fonts/Helvetica-Bold-14.pf2
insmod vbe
insmod png
insmod coreui
load_config /boot/burg/themes/winter/sora_clean.txt
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
UUID=006478CB6478C4C6                      /media/SYSTEM_DRV                 ntfs-3g  defaults  0  0  
UUID=170bd668-eb42-4510-828e-86db8a732827  /media/boot                     ext3     ro        0  0  
UUID=7e130884-a636-4dce-a8a6-5808e56073db  /                                 ext4     defaults  0  1  
UUID=e47c8d57-3341-4ebb-a008-0738aed98ac9  swap                              swap     sw        0  0  
UUID=663C7B443C7B0E75                      /media/Windows7_OS/Users/Coleman  ntfs-3g  defaults  0  0  
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 260.603633881 = 279.821021184  boot/grub/core.img                             1
 260.603637695 = 279.821025280  boot/grub/grub.cfg                             1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```


sda5 is the one i need to boot, it contains my old ubuntu partition.

---

### Post by oldfred on 2011-08-02
Your grub2 boot loader in the MBR is looking for files in sda4. You do not have a sda4.

Also some computers have a BIOS that will not let you boot at all unless you have a boot flag on a primary partition. Windows needs a boot flag, grub does not use one. So I would add a boot flag to sda1 as that looks like your windows boot partition. It only is otherwise important if you add the windows boot loader or want to repair windows.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)


If you have not made a windows repair CD I would also do that.
Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by cjack2964 on 2011-08-02
Thank you so much oldfred! That did the trick, and I am back with my original configuration. I have been so impressed by the quick answers and good advice I have found on ubuntu forums.  This is exactly the reason I switched to ubuntu in the first place, for better or worse I am in control of my system and fixing it teaches some of the most important lessons.

If you don't mind, I do have another question, before you helped me repair my boot loader you posted this in response to my original question

> The only way that might work is to install a small grub legacy or grub2 only boot on FAT32 or NTFS. Then you can use scripts to edit menu.lst or grub.cfg on which to boot.

Can you please explain this to me in a little more detail? I'm curious, do you mean I should chain load my OSes so I can have access from windows, I have already figured out a script for both windows and ubuntu, so if I can successfully put a configuration file on my spare partition this will work wonderfully I am almost sure of it.

Another thought I had during this process is that I might be able to set grub2 to set a default as a function of the one I loaded last, so if I load win7, next will be ubuntu and vice versa. I wonder if you have any insight on this, it probably requires some creative scripting

---

### Post by oldfred on 2011-08-02
You are not chainloading, but using grub or grub2 as the boot loader and manually maintaining the menu. It is more work, since grub2's os-prober has become very good at finding other systems and creating grub entries for all systems you have installed.

I still have my old grub legacy boot partition as I used it for chainloading. With grub2, it does not like to be installed to a partition. Of course the boot of windows is chainloading. Grub has some commands for reboots on errors or other settings, but I do not know them or use them. 

Herman has info on grub2 & grub legacy partiitons.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition)
old grub partition
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition)
Grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_)

Some other settings and see all the links in drs305's signature on grub2 info:
Discussion of timeouts issue & recordfail:
[http://ubuntuforums.org/showthread.php?t=1717700](http://ubuntuforums.org/showthread.php?t=1717700)
drs305's hack to get hidden timeout to work:
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)

---

### Post by cjack2964 on 2011-08-02
Thank you again, I am going to mark this thread solved because I guess I have an answer to my question. I will keep searching for the solution I need, but I am glad for this experience, I feel a lot more confident about fiddling with my boot loader now anyway..

---

### Post by oldfred on 2011-08-03
Just make sure you have a repairCd or USB for every system you have installed. I used to burn a bunch of CDs for every Ubuntu install as I also updated my gparted, Supergrub and maybe a rescueCD or two. Now I just have them all on a Flash drive as ISO and loopmount boot them driectly with grub2 and I can easily update the flash drive.

After reinstalling grub a few times or booting from other devices it becomes a lot easier. Learn enough about boot script to know what is installed where and run it before & after any system change.

---

### Post by dcstar on 2011-08-03
> **cjack2964 said:**
> Hi, at the moment I am trying to create a script on the Win7 partition of my dual booted laptop **that will allow me to change the default of Grub2 OS** to ubuntu.
.........

Hun?, why do you need a script for something that is **built into** Grub2 and only needs to be enabled?

---

### Post by cjack2964 on 2011-08-03
No, you see my intention is to create a scripting both windows and ubuntu that change to default and reboots the computer, creating a "link" to the other desktop which I can use with my vnc client. That way I can always use one os or the other without needing to be there to manually select it in grub

---

