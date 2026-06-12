---
title: "Ubuntu/Win7 Dual boot issues with Grub2"
date: 2010-06-05
forum: General Help
---

### Post by Axel482 on 2010-06-05
I have Windows 7 and Ubuntu 10.04 set up in dual-boot on my laptop.
Since I am giving this laptop to someone who has no need for Ubuntu at the end of the summer, I wanted to change the Grub boot menu so that Win7 will load immediately and skip the menu.  However, I still want Ubuntu to remain on the computer.  I read that holding shift during or after the boot splash would force the menu to load, but that doesn't seem to be working for me.  
I *could *fix this if I had access to the Ubuntu side, but alas, I don't.
I just tried loading up a Live CD and editing the /etc/default/grub file, but I can't run *update-grub *afterwards.
Any ideas of how to fix it from within Windows or a Live CD?

---

### Post by yetiman64 on 2010-06-05
1st question: is your ubuntu a "wubi" install? 
If NOT, and you can't boot ubuntu: from a live cd use this link _[Boot_info_script]("http://ubuntuforums.org/showthread.php?t=1291280")_
and follow the instructions to download and use the script. Copy the Results and post them back here (between code tags please).

Edit: if it is a "wubi" install - ignore the Boot_info_script.

---

### Post by Axel482 on 2010-06-05
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
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda4: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,074,048   285,693,899   282,619,852   7 HPFS/NTFS
/dev/sda3         471,314,432   488,396,799    17,082,368  17 Hidden HPFS/NTFS
/dev/sda4         285,693,950   471,314,431   185,620,482   5 Extended
/dev/sda5         285,693,952   463,673,343   177,979,392  83 Linux
/dev/sda6         463,675,392   471,314,431     7,639,040  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        126A64206A6402B9                       ntfs       System                        
/dev/sda2        A2D08A00D089DAC5                       ntfs       TI102605W0F                   
/dev/sda3        DA9AAF919AAF6929                       ntfs       HDDRECOVERY                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        5f8cbbd9-fab5-44c4-a62f-23278eb37419   ext4                                     
/dev/sda6        75dd5aee-b249-4f99-8bbe-c5b439c2fdeb   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
set default="6"
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
search --no-floppy --fs-uuid --set 5f8cbbd9-fab5-44c4-a62f-23278eb37419
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 5f8cbbd9-fab5-44c4-a62f-23278eb37419
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=0
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
    search --no-floppy --fs-uuid --set 5f8cbbd9-fab5-44c4-a62f-23278eb37419
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5f8cbbd9-fab5-44c4-a62f-23278eb37419 ro  splash vga=758  quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5f8cbbd9-fab5-44c4-a62f-23278eb37419
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=5f8cbbd9-fab5-44c4-a62f-23278eb37419 ro single  splash vga=758
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5f8cbbd9-fab5-44c4-a62f-23278eb37419
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5f8cbbd9-fab5-44c4-a62f-23278eb37419 ro  splash vga=758  quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5f8cbbd9-fab5-44c4-a62f-23278eb37419
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5f8cbbd9-fab5-44c4-a62f-23278eb37419 ro single  splash vga=758
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5f8cbbd9-fab5-44c4-a62f-23278eb37419
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5f8cbbd9-fab5-44c4-a62f-23278eb37419
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 126a64206a6402b9
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set a2d08a00d089dac5
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set da9aaf919aaf6929
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
# / was on /dev/sda5 during installation
UUID=5f8cbbd9-fab5-44c4-a62f-23278eb37419 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=75dd5aee-b249-4f99-8bbe-c5b439c2fdeb none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 200.1GB: boot/grub/core.img
 200.4GB: boot/grub/grub.cfg
 200.3GB: boot/initrd.img-2.6.32-21-generic
 200.5GB: boot/initrd.img-2.6.32-22-generic
 200.2GB: boot/vmlinuz-2.6.32-21-generic
 200.5GB: boot/vmlinuz-2.6.32-22-generic
 200.5GB: initrd.img
 200.3GB: initrd.img.old
 200.5GB: vmlinuz
 200.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 c0 9b 0a 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 c0  9b 0a 00 98 74 00 00 00  |............t...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```I installed from Live CD

---

### Post by oldfred on 2010-06-05
Are you saying you cannot boot?

Did you set windows as the default and menu hidden and now you cannot get to Ubuntu or did Ubuntu not work? I do not see anything in the script that looks wrong.

I did find that as grub loads it remembers the key entries and was able to count down arrows and change boot before menu came up. If you have set windows as default you could try up arrow to count to top of menu entry.

Otherwise you would have to chroot into your system to update it.

I am no expert on /etc/default/grub  but if you post it someone may be able to help.

---

### Post by yetiman64 on 2010-06-05
Some ideas on the subject,

1.Try oldfred's up arrow suggestion during the boot process, may be an easy fix, I also can't see anything wrong with the script info.

2.Again agree with oldfred re posting the /etc/default/grub file, will be usefull to see how you set it up.

Here's a couple of more info links,

1. The Grub 2 guide, I think you'll need to particularly note section 5 with regard to what you're trying to do (This is just in case you haven't already been using it). [Link here.]("http://ubuntuforums.org/showthread.php?t=1195275") 

2. If the above don't work and your boot problem persists, this is the link for howto chroot and reinstall grub (though you'll probably need it, only as far as the updating grub step - step 8 -after 1st correcting /etc/default/grub settings.). Look for "METHOD 3 - CHROOT" very near to the bottom of the page.  [COLOR=Black][Link here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")_[.]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")_[/COLOR]
[U][COLOR=Red][COLOR=Black] 
[/COLOR][/COLOR][/U][COLOR=Red][COLOR=Black]Edit2: Take [/COLOR][/COLOR][COLOR=Red][COLOR=Black]not[/COLOR][/COLOR][COLOR=Red][COLOR=Black]e to follow later steps of unmounting the chroot properly,[/COLOR][/COLOR][COLOR=Red][COLOR=Black] even if you don't do the reinstall steps for grub 2 but just use it for updating, before you reboot.
[/COLOR][/COLOR][U][COLOR=Red]
[/COLOR][/U]

---

### Post by Axel482 on 2010-06-05
Sorry, I keep getting interrupted from replying.

I can boot and  nothing with Grub2 is broken, if there was any confusion on that.   Everything that's gone 
wrong was entirely my fault.  
 
I set  Windows 7 as the default OS to boot using Startup Manager on Ubuntu.  I  changed the timeout to zero so that anyone else using this wouldn't be  confused by the Grub menu.  I had read that holding shift after the boot  splash would get the menu to show up.  A little too late I read that  shift sometimes will not work. 
 
If I hold shift after the boot splash disappears, I get a "GRUB  Loading" message at the top of the screen.  Then, it stops and just  loads straight to Windows.  

/etc/default/grub

```
# If  you change this file, run 'update-grub' afterwards to update
#  /boot/grub/grub.cfg.

GRUB_DEFAULT=6
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release  -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet  splash"
GRUB_CMDLINE_LINUX=" splash vga=758"

# Uncomment to  disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

#  The resolution used on graphical terminal
# note that you can use  only modes which your graphic card supports via VBE
# you can see  them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

#  Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to  Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable  generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

#  Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440  1"
```I can edit this file through the Live CD.  The *update-grub  *does not work from the CD though.  

I know it says not to,  but could I edit the contents of /boot/grub/grub.cfg?

Up arrow  didn't work for me either.

---

### Post by yetiman64 on 2010-06-05
Ok got you now, oldfred may have the answer to stoping the automatic loading of windows by using the up arrows.

Give it a try 1st. 

You'll have to be quick on the draw to beat grub set to a timeout of 0 :) , but it should be do-able.

Yes, your default boot is set to line 6 and you have to take it up to 0 in no time flat or you may even accidently boot a recovery mode (from which you can continue into a normal boot and redo /etc/defaults/grub settings and update-grub to make the settings hold). 

Then you can re-attack your first ideas slightly differently.

As a Windows user think of "tapping" F8 to go into "Safe Mode" but with the up arrow instead :).  Good luck

---

### Post by Axel482 on 2010-06-05
I'll try it some more then.   Man, that's gonna be weird when someone walks in on me furiously tapping "up" while my computer boots.  :)

And wouldn't moving it up once stop the timer?  It always did before.  Also, I believe there are Memtests in the way, so hopefully the timer does stop...

---

### Post by yetiman64 on 2010-06-05
Hopefully, just 1 tap at the right time will stop booting, but not sure how oldfred meant it to be used. 

Certainly conjures up a funny image though, alright. 

I'm definitely interested to see how this works for you. Hope it does. 

Suggestions - Rather than setting a default of 6 to boot Win first (this can change position as new linux kernels are added - moving windows down the positions) maybe you should consider having grub move the Win entry to the top of the list by processing 30_os-prober 1st (by renaming it to say 08_os-prober -between the debian_theme entry and the linux entry in /etc/grub.d).  
Wait for further opinion on this idea though as I'm not entirely sure of it, haven't done it in practice myself but think it can be done.

Set the default entry at 0 (Windows). Set the timeout to say 2 or 3 seconds (for future Ubuntu access) and hide the menu (all do-able in /etc/default/grub).

This will all depend on booting into ubuntu to do the set-up.

---

### Post by Axel482 on 2010-06-05
That's something like what my plan was yetiman, but I still need to get into Ubuntu...

So far, no luck with the up arrow.  Win7 every time, though I have gotten the Windows Boot Manager twice.  I looked through it, but I don't think I can do anything from there.

Any ideas on running *update-grub *from Live CD?  Or somehow messing with the /boot/grub/grub.cfg file?

And what's this chroot of which oldfred speaks?


Edit:  While furiously tapping after the boot splash, there is an underscore that flashes in the top left corner.  I've noticed it before and it's normal, but as long as I'm tapping, the underscores stays there flashing.  Once I stop tapping, it goes away and Windows boots.  Any ideas on why that is?  (May or may not be relevant to my current dilemma)

---

### Post by yetiman64 on 2010-06-05
Just 1 more try with the esc key (not shift) during boot as I think oldfred was on the mark re having to chroot in to update grub from a live cd.

 Complex and messy imo - but may be necessary (link to instructions for chroot is in post #5).  

Worth trying out esc first - Can't remember if I've used it with grub or grub2 though, it may be an older method.

If you have to go the live-cd and chroot method read all the instructions very carefully. First edit /etc/default/grub to workable values, from the live-cd. 
"Grub 2 guide" link in post #5 (Section 5 of the guide is the good info for these settings and what they do).

Then also off the live-cd follow the instrucitions for the chroot method up to the updating stage, don't do the reinstalling steps, but be sure to continue through with the correct folder and chroot unmounting before you reboot. Definitely read up heaps and take care while doing this as going too quick and missing a step can botch a system up even worse. Good luck.

NB:
Just caught your edit before posting this Try the esc key while the cursor is blinking. Don't know if it'll work - hope you can avoid the chroot method.

Edit re: > ...  Or somehow  messing with the /boot/grub/grub.cfg file?  Don't think so, that file is in the boot_info_script output and unless I've missed something appears OK.

---

### Post by Teracis on 2010-06-05
> GRUB_HIDDEN_TIMEOUT=0

    *

      The hidden timeout option is available to single-OS computers - if multiple OS's are known to Grub 2, this option is bypassed.
    *

      On single-OS systems, the menu will be hidden unless a # symbol is present at the beginning of this line. ( # GRUB_HIDDEN_TIMEOUT=0 )
    * The default setting initially depends on the presence of other operating systems.
          o Another OS Detected: The menu will be displayed. ( The line will begin with a # symbol. )
          o No other OS Detected: This setting is not used, as determined by the 
    * For integers greater than 0, the system will pause, but not display the menu, for the entered number of seconds.
    *

      0 The menu will not be displayed. There will be no delay.
          o The user may force displaying the menu as the computer boots by holding down the SHIFT key (single-OS computers only).
                + During boot, the system will check the SHIFT key status. If it cannot determine the key status, a short delay will enable the user to display the menu by pressing the ESC key. 
                + If enabled, the splash screen designated in 05_debian_theme will be displayed even if the hidden menu feature is selected. 


This says to me try holding shift when you boot (you already knew that) and failing that, try pressing ESC (you already knew that)

The only other thing I can suggest is a reinstall but not formatting anything. I.E. only do the reinstall of grub using the live CD.

You could just tell the installer to manually partition but not delete any partitions? Maybe this is a bit of a long fix, but it's better than a broken system?

---

### Post by Axel482 on 2010-06-06
Shift and up arrow aren't working at all.  And ESC is for the old Grub

I did find this:

[https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode)

It's telling me that if Grub can't find the /boot/grub/grub.cfg file, then it will go to "rescue mode."

Could I use a Live CD to move grub.cfg so that it can't find it and force the rescue mode prompt where I could use some sort of CL magic to fix this?

Of course, if it failed I would move the .cfg back with the Live CD.

---

### Post by yetiman64 on 2010-06-06
> **Rescue Mode**

 The *rescue* mode is a  major GRUB 2 enhancement. If GRUB 2 fails to find a useable *grub.cfg*  and is unable to transfer control to a kernel it will drop to a *grub-rescue>*  prompt.You have a use-able grub.cfg and it appears perfect in the boot_info script output.  

From oldfred, who's quite experienced with this in my opinion,
> I do not see anything in the script that looks wrong. The problem is windows is set as default, from your /etc/default/grub file posted with a timeout of 0.

> It's telling me that if Grub can't find the /boot/grub/grub.cfg file,  then it will go to "rescue mode."
 It is finding the grub.cfg file as that is how windows is being loaded and is NOT going to rescue mode. Also the fact that it isn't dropping to a rescue mode would indicate to me what you suggested earlier that neither grub or Ubuntu are "broken" is correct.

> Could I use a Live CD to move grub.cfg so that it can't find it and  force the rescue mode prompt where I could use some sort of CL magic to  fix this?
IMO no, it appears as if its time to go to a live cd, change the offending /etc/default/grub settings previously mentioned. Rather than going for more "nuclear" options of re-installing grub or even worse the whole system, just go the chroot method and update-grub with the new settings, exit the chroot properly and reboot. You should then be back as good as new. The info needed is all linked in post 5.  Note the chroot method is towards the bottom of the page linked.

I've got to go offline for a bit -need to catch some ZZZZ's- will look back in later. If in any doubt wait for someone like oldfred to come back online. Note: if you aren't aware of it yet, in the bottom left of every post window is an icon you can glance at or hover your cursor over to see if a person is online.  Suggest you research doing the chroot, make a list of commands from the guide and if in doubt about them post back here for someone to check them out for you. Be back later on.

---

### Post by oldfred on 2010-06-06
I was hoping up arrow might work but timeout at 0 must override the entry of keys. Are you holding shift down the entire time from BIOS, you cannot just tap it.

kansasnoob combined all the chroot commands on one line with &&. You just have to change the drive,partition to be correct and paste one line instead of many.

kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

kansasnoob's - change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

grub-install /dev/sda
grub-install --recheck /dev/sda
update-grub
#other commands if needed to update system

---

### Post by Axel482 on 2010-06-06
Ok, so I'm gonna give this chroot method a go and see what happens.

Just to be sure, I want to go up to number 8, skip 9 & 10, then continue from there?

And then I won't have to run any of the post-restoration commands, will I?  Except for running *update-grub *to make me feel better about it.

---

### Post by yetiman64 on 2010-06-06
> kansasnoob combined all the chroot commands on one line with &&. You just have to change the drive,partition to be correct and paste one line instead of many.

kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php...2&postcount=10]("http://ubuntuforums.org/showpost.php?p=8068512&postcount=10")
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

kansasnoob's - change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

grub-install /dev/sda
grub-install --recheck /dev/sda
update-grub
#other commands if needed to update systemFollow these instructions (an all in 1 command) to setup the chroot. Just checked boot_info_script output, you do want it as sda5 - even easier than the link I'd posted (forget about that link & thanks to oldfred here - just made life much easier for you).

If you noted my previous edit in post #14 - I pulled it too as there's easier method than scripts for adjusting the windows menu position, a 06_Custom entry in /etc/grub.d will do.

---

### Post by Axel482 on 2010-06-06
Woo!

The chroot method was successful!  I fixed the /etc/default/grub file, ran kansasnoob's commands, and it found my linux install.

Grub was reset to an appropriate timer, but it didn't find Windows.  Easy fix though, I ran *update-grub *after getting back on Ubuntu and it's all working again.

Thanks for the help!  I won't be changing any timers to zero again  ;)

Also could someone point me to a thread about /home/alex/.ICEauthority?

I've had a dialog pop up at start up saying that the file can't be located.  It's been happening for a while and I don't remember why it started.  There haven't been any other adverse effects from it, it's just annoying.

---

### Post by yetiman64 on 2010-06-06
=D>Great to hear.

for   .ICEauthority check the thread    [http://ubuntuforums.org/showthread.php?t=949750](http://ubuntuforums.org/showthread.php?t=949750)  and see if it helps.

As for your original intent try looking up using 06_custom entry in /etc/grub.d with a windows boot entry placed in it.

---

### Post by oldfred on 2010-06-06
I think yetiman64's link should suffice, but here is another. Also has commands to set ownership & permissions for all of /home.

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

