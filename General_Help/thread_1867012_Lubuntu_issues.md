---
title: "Lubuntu issues"
date: 2011-10-22
forum: General Help
---

### Post by kakashi_12 on 2011-10-22
To start off...

It does not show me the correct amount of space being used. Think I solved that....

kakashi12@Sentia:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             26764348   3330240  22074544  14% /

So, only 14% of the partition is used so far?


---
Secondly, can not set AbiWord default Save As to .doc extension. Looked this up and found a command to do this, but it says command not found.

---

### Post by amjjawad on 2011-10-22
> **kakashi_12 said:**
> To start off...

It does not show me the correct amount of space being used. Think I solved that....

kakashi12@Sentia:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3             26764348   3330240  22074544  14% /

So, only 14% of the partition is used so far?


---
Secondly, can not set AbiWord default Save As to .doc extension. Looked this up and found a command to do this, but it says command not found.

You need to explain more. People who never saw your other thread, will understand nothing from what you posted here :)

---

### Post by kakashi_12 on 2011-10-22
i know. my mistake.

When going to Places, Computer, and then looking at properties of Filesystem. It does not show the amount used or the capactity of the partition. i solved that problem with using the command above.

I am still having the problem with AbiWord. I would also like to change the default in the spreadsheet to of course to xls.

Third problem, Can't change the system time preferences to non-military time (show PM or AM)

Forth, any way that I can display "Computer" icon and "Trash" on desktop?

---

### Post by kakashi_12 on 2011-10-22
Two more problems....

Can't set keyboard shortcuts or turn touchpad 'tap to click' off/disable

ScreenSavers don't work. Says that there are packages missing and they can't be set. I installed one package but can't find the other in synapitcs. xscreensaver-extra is the one still missing.

---

### Post by amjjawad on 2011-10-22
> **kakashi_12 said:**
> I am still having the problem with AbiWord. I would also like to change the default in the spreadsheet to of course to xls.


[http://www.abisource.com/wiki/FAQ/Always_save_as_Word](http://www.abisource.com/wiki/FAQ/Always_save_as_Word)

I'll get back to you for the other issues soon ;)

---

### Post by kakashi_12 on 2011-10-22
Ok, solved the screensaver problem.

---

### Post by amjjawad on 2011-10-22
> **kakashi_12 said:**
> Third problem, Can't change the system time preferences to non-military time (show PM or AM)


[https://help.ubuntu.com/community/Lubuntu/Documentation/CustomizingTheClock](https://help.ubuntu.com/community/Lubuntu/Documentation/CustomizingTheClock)

---

### Post by kakashi_12 on 2011-10-22
Like I said, i tried that and it said command not found. NOW that I read closer it says "Gedit command not found".
Well, duh. It would help if gedit was installed! lol. That's kind of essential.

---

### Post by kakashi_12 on 2011-10-22
Ok. I've installed gedit from Synaptics. Now the file opens, but it is a blank file and i get errors. Almost like I don't have permissions or something.

sudo gedit /usr/share/abiword-2.6/system.profile

(gedit:9188): Gtk-WARNING **: Theme parsing error: gtk-buttons.css:159:10: Expected valid border

(gedit:9188): Gtk-WARNING **: Theme parsing error: gtk-bars.css:102:16: Themeing engine 'adwaita' not found

(gedit:9188): Gtk-WARNING **: Theme parsing error: gtk-bars.css:117:16: Themeing engine 'adwaita' not found

(gedit:9188): Gtk-WARNING **: Theme parsing error: gtk-bars.css:134:16: Themeing engine 'adwaita' not found

(gedit:9188): Gtk-WARNING **: Theme parsing error: gtk-bars.css:153:16: Themeing engine 'adwaita' not found

(gedit:9188): Gtk-WARNING **: Theme parsing error: gtk-bars.css:165:16: Themeing engine 'adwaita' not found

(gedit:9188): Gtk-WARNING **: Theme parsing error: gtk-bars.css:175:16: Themeing engine 'adwaita' not found

(gedit:9188): Gtk-WARNING **: Theme parsing error: gtk-bars.css:186:16: Themeing engine 'adwaita' not found

(gedit:9188): Gtk-WARNING **: Theme parsing error: gtk-bars.css:198:16: Themeing engine 'adwaita' not found

(gedit:9188): Gtk-WARNING **: Theme parsing error: gtk-bars.css:208:16: Themeing engine 'adwaita' not found

(gedit:9188): Gtk-WARNING **: Theme parsing error: gtk-bars.css:218:16: Themeing engine 'adwaita' not found

(gedit:9188): Gtk-WARNING **: Theme parsing error: gtk-bars.css:223:16: Themeing engine 'adwaita' not found

(gedit:9188): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.E22U3V': No such file or directory

(gedit:9188): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:9188): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.DBQ83V': No such file or directory

(gedit:9188): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by kakashi_12 on 2011-10-22
Clock fixed, thanks.

---

### Post by amjjawad on 2011-10-22
> **kakashi_12 said:**
> Like I said, i tried that and it said command not found. NOW that I read closer it says "Gedit command not found".
Well, duh. It would help if gedit was installed! lol. That's kind of essential.

Sorry, I should have noticed that.
Replace "gedit" with "leafpad". Leafpad is the default text editor in Lubuntu.

I have never used AbiWord, I don't need it as I'm not editing or writing any document.
I searched on google and found that link.

---

### Post by amjjawad on 2011-10-22
[https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/348071](https://bugs.launchpad.net/ubuntu/+source/abiword/+bug/348071)

Looks like one is blaming the other :)
Not sure how to fix that. I have a strong headache and can't open my eyes but I'll do my best to help you with the other questions before I log off.

---

### Post by kakashi_12 on 2011-10-22
This is really weird! But after installing that one package that fixed the screensaver, I now have a new item under Preferences called System Settings. This allows me to set keyboard shortcuts. But it only shows common shortucts like cut and paste. None for like terminal or anything. This one is too complicated. nvm

---

### Post by amjjawad on 2011-10-22
> **kakashi_12 said:**
> Forth, any way that I can display "Computer" icon and "Trash" on desktop?

[http://forum.lxde.org/viewtopic.php?f=8&t=2018](http://forum.lxde.org/viewtopic.php?f=8&t=2018)

---

### Post by amjjawad on 2011-10-22
> **kakashi_12 said:**
> This is really weird! But after installing that one package that fixed the screensaver, I now have a new item under Preferences called System Settings. This allows me to set keyboard shortcuts. But it only shows common shortucts like cut and paste. None for like terminal or anything. This one is too complicated. nvm

I must go now, I'm so sorry but I can't take the headache any more.

On my signature, there is Mega Thread for Lubuntu. Bookmark it for future reference and I'm sure it will come in handy.

Try to use Google or [www.googlubuntu.com](www.googlubuntu.com).

LXDE Forum is a good place too for many tips and stuff.

I'll have some rest and get back to you. I slept 9am this morning and woke up 2pm. I must take it easy before I'll fade away :)

---

### Post by kakashi_12 on 2011-10-22
no problem. thanks.

--- Ok, I'm summarized... this is all that's left now......

- keyboard shortcuts
- display items on desktop (computer and trash)
- AbiWord and (spreadsheet) default save as .doc and .xls ext
- Disable veritcal scroll and touchpad tap to click

---

### Post by kakashi_12 on 2011-10-23
My GRUB loader is slow now that I have Lubuntu. It takes about 15 secs for it even to load, 5 secs for the timer to start, and then when choosing the OS it also takes about 5-10 secs for the OS to switch between GRUB and OS.

Now that I have downloaded and installed Grub Customizer, I have added a background and that slowed it down to an extra minute or two of even loading GRUB. It looks awesome though. How can I make GRUB faster... with or without the picture? Here is my output...


                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 63.4 GB, 63350767616 bytes
255 heads, 63 sectors/track, 7701 cylinders, total 123731968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    63,488,879    63,488,817   7 NTFS / exFAT / HPFS
/dev/sda2          63,490,046    69,347,327     5,857,282   5 Extended
/dev/sda5          63,490,048    69,347,327     5,857,280  82 Linux swap / Solaris
/dev/sda3          69,347,328   123,729,919    54,382,592  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        88C45D98C45D8978                       ntfs       
/dev/sda3        d0a14e42-2a4f-491a-abf1-60a295d50dc6   ext4       
/dev/sda5        e41b8e63-11f9-4043-ab91-48a4d6324897   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=========================== sda3/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root d0a14e42-2a4f-491a-abf1-60a295d50dc6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos3)'
  search --no-floppy --fs-uuid --set=root d0a14e42-2a4f-491a-abf1-60a295d50dc6
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set=root d0a14e42-2a4f-491a-abf1-60a295d50dc6
insmod jpeg
if background_image /home/kakashi12/Pictures/alienware.jpg; then
  set color_normal=green/black
  set color_highlight=yellow/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux_proxy ###
menuentry "Linux Lubuntu 11.10" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root d0a14e42-2a4f-491a-abf1-60a295d50dc6
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=d0a14e42-2a4f-491a-abf1-60a295d50dc6 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux_proxy ###

### BEGIN /etc/grub.d/30_os-prober_proxy ###
menuentry "Windows eXPerience Professional" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 88C45D98C45D8978
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober_proxy ###
--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=d0a14e42-2a4f-491a-abf1-60a295d50dc6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e41b8e63-11f9-4043-ab91-48a4d6324897 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               3
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     3
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
00000010  20 20 20 20 20 20 20 20  3c 65 6e 74 72 79 20 6e  |        <entry n|
00000020  61 6d 65 3d 22 76 6f 6c  22 3e 0a 20 20 20 20 20  |ame="vol">.     |
00000030  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
00000050  20 20 20 20 20 20 20 20  20 20 20 3c 6c 6f 63 61  |           <loca|
00000060  6c 5f 73 63 68 65 6d 61  20 73 68 6f 72 74 5f 64  |l_schema short_d|
00000070  65 73 63 3d 22 56 6f 6c  75 6d 65 6e 20 67 75 61  |esc="Volumen gua|
00000080  72 64 61 64 6f 20 70 61  72 61 20 72 65 73 74 61  |rdado para resta|
00000090  75 72 61 72 20 64 75 72  61 6e 74 65 20 65 6c 20  |urar durante el |
000000a0  69 6e 69 63 69 6f 22 3e  0a 20 20 20 20 20 20 20  |inicio">.       |
000000b0  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
000000d0  20 20 20 20 20 20 20 20  20 3c 2f 6c 6f 63 61 6c  |         </local|
000000e0  5f 73 63 68 65 6d 61 3e  0a 20 20 20 20 20 20 20  |_schema>.       |
000000f0  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
00000110  20 3c 2f 65 6e 74 72 79  3e 0a 20 20 20 20 20 20  | </entry>.      |
00000120  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
00000140  20 20 3c 65 6e 74 72 79  20 6e 61 6d 65 3d 22 6d  |  <entry name="m|
00000150  75 74 65 22 3e 0a 20 20  20 20 20 20 20 20 20 20  |ute">.          |
00000160  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
00000180  20 20 20 20 20 20 3c 6c  6f 63 61 6c 5f 73 63 68  |      <local_sch|
00000190  65 6d 61 20 73 68 6f 72  74 5f 64 65 73 63 3d 22  |ema short_desc="|
000001a0  45 73 74 61 64 6f 20 64  65 20 73 69 6c 65 6e 63  |Estado de silenc|
000001b0  69 6f 20 67 75 61 72 64  61 64 6f 22 3e 0a 00 fe  |io guardado">...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 60 59 00 00 00  |...........`Y...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

---

### Post by amjjawad on 2011-10-23
Hi again,

You need to follow the instructions given in that link as you read them :)
Please, wrap up the text with "CODE" tag.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

> If you came here from a Linux forum, paste the content of RESULTS.txt  into your next post. Make sure to use the appropriate formating.  For example in the Ubuntu forums click on the code tags (the symbol #)  before pasting RESULTS.txt.

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]


Thank you :)

---

### Post by kakashi_12 on 2011-10-23
I did follow them. Do you have everything you need now?

It looks like I have an extra unneeded partition. I think that happened during installation of Lubuntu.

The first installation crashed. So I wiped it and reloaded again. Successful the second time around, but must not have wiped it entirely. Is that slowing grub down?

---

### Post by amjjawad on 2011-10-23
> **kakashi_12 said:**
> I did follow them. Do you have everything you need now?

It looks like I have an extra unneeded partition. I think that happened during installation of Lubuntu.

The first installation crashed. So I wiped it and reloaded again. Successful the second time around, but must not have wiped it entirely. Is that slowing grub down?

Yes, thanks :)

I'll have a look and get back to you :)

---

### Post by amjjawad on 2011-10-23
> **kakashi_12 said:**
> 

                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

**[COLOR=Red]sda3[/COLOR]**: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
**[COLOR=Red]     Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img[/COLOR]**

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 63.4 GB, 63350767616 bytes
255 heads, 63 sectors/track, 7701 cylinders, total 123731968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    63,488,879    63,488,817   7 NTFS / exFAT / HPFS
/dev/sda2          63,490,046    69,347,327     5,857,282   5 Extended
/dev/sda5          63,490,048    69,347,327     5,857,280  82 Linux swap / Solaris
/dev/sda3          69,347,328   123,729,919    54,382,592  83 Linux


======================== Unknown MBRs/Boot Sectors/etc: ========================

**[COLOR=Red] Unknown BootLoader on sda2[/COLOR]**

00000000  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
00000010  20 20 20 20 20 20 20 20  3c 65 6e 74 72 79 20 6e  |        <entry n|
00000020  61 6d 65 3d 22 76 6f 6c  22 3e 0a 20 20 20 20 20  |ame="vol">.     |
00000030  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
00000050  20 20 20 20 20 20 20 20  20 20 20 3c 6c 6f 63 61  |           <loca|
00000060  6c 5f 73 63 68 65 6d 61  20 73 68 6f 72 74 5f 64  |l_schema short_d|
00000070  65 73 63 3d 22 56 6f 6c  75 6d 65 6e 20 67 75 61  |esc="Volumen gua|
00000080  72 64 61 64 6f 20 70 61  72 61 20 72 65 73 74 61  |rdado para resta|
00000090  75 72 61 72 20 64 75 72  61 6e 74 65 20 65 6c 20  |urar durante el |
000000a0  69 6e 69 63 69 6f 22 3e  0a 20 20 20 20 20 20 20  |inicio">.       |
000000b0  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
000000d0  20 20 20 20 20 20 20 20  20 3c 2f 6c 6f 63 61 6c  |         </local|
000000e0  5f 73 63 68 65 6d 61 3e  0a 20 20 20 20 20 20 20  |_schema>.       |
000000f0  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
00000110  20 3c 2f 65 6e 74 72 79  3e 0a 20 20 20 20 20 20  | </entry>.      |
00000120  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
00000140  20 20 3c 65 6e 74 72 79  20 6e 61 6d 65 3d 22 6d  |  <entry name="m|
00000150  75 74 65 22 3e 0a 20 20  20 20 20 20 20 20 20 20  |ute">.          |
00000160  20 20 20 20 20 20 20 20  20 20 20 20 20 20 20 20  |                |
*
00000180  20 20 20 20 20 20 3c 6c  6f 63 61 6c 5f 73 63 68  |      <local_sch|
00000190  65 6d 61 20 73 68 6f 72  74 5f 64 65 73 63 3d 22  |ema short_desc="|
000001a0  45 73 74 61 64 6f 20 64  65 20 73 69 6c 65 6e 63  |Estado de silenc|
000001b0  69 6f 20 67 75 61 72 64  61 64 6f 22 3e 0a 00 fe  |io guardado">...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 60 59 00 00 00  |...........`Y...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

There is no unneeded partition but I suspect something else.
I did some search. GRUB2 is probably two years old now and there were some bugs when users reported that GRUB2 loads slow. However, I don't think that applies to your case. I must do another deeper search though but before that, I have two questions:

1- Is your HDD IDE?
2- Is it Master or Slave?

I think we can re-install GRUB to the MBR (sda) and see if that will make any difference but I need the answers of the above two Qs to rule out some possible points.

Thanks!

---

### Post by kakashi_12 on 2011-10-23
So if that's not an unneeded partition, what is it? sda2

Yes I use IDE and Yes it's Master. It couldn't possibly be slave, because there is only one HDD in the laptop.Maybe if I take the jumper off it be then be Cable Select... which would still technically be Master.

---

### Post by amjjawad on 2011-10-24
> **kakashi_12 said:**
> So if that's not an unneeded partition, what is it? sda2

sda2 is the Extended Partition. Extended Partition is treated as Primary Partition. Linux gives sda1, sda2, sda3 and sda4 to Primary Partitions. Logical Partitions start from sda5.

Windows on [COLOR=Red]sda1[/COLOR] which is Primary Partition
Extended Partition on [COLOR=Red]sda2[/COLOR]
Swap is Logical Partition on [COLOR=Red]sda5[/COLOR]
Linux on [COLOR=Red]sda3[/COLOR] which is Primary Partition

If I were you, I would do the partitions this way:

sda1 - Primary - Windows
sda2 - Primary - Linux
sda3 - Primary - Swap

OR

sda1 - Primary - Windows 
sda2 - Primary - Linux
sda3 - Extended
sda5 - Logical - /home (for Linux)
sda6 - Logical - Swap

Very helpful link: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)


> Yes I use IDE and Yes it's Master. It couldn't possibly be slave, because there is only one HDD in the laptop.Maybe if I take the jumper off it be then be Cable Select... which would still technically be Master.
I'm sorry, I keep forgetting it's a laptop not a PC. Perhaps because I have two PCs which I'm using all the time.
No need to change anything. I suggest to try re-installing GRUB2 and see if that will make any difference.

I was travelling and just came home. I'll have some rest (slept 3 hours only) and will see what is our next step :)

---

### Post by kakashi_12 on 2011-10-24
Well I don't remember putting that partition there and am not sure what it is for. I only have two OS's and know that there is one swap. A logical with nothing on it?
 
Now that I think of it I'm wondering if I did something wrong during installation. Please tell me...
I choose 'sda' as the install point for boot loader and not 'sda1' or sda5'. Therefore it was at the Drive, not at a particular partition. Should it have been... like on Linux or Windows?
Also, I made the mounting point for ext4 'linux' at '/'. Should it have been mounted at '/home' or '/root'? I always forget the difference between those three.
 
How do I reinstall grub 2?

---

### Post by amjjawad on 2011-10-25
> **kakashi_12 said:**
> Well I don't remember putting that partition there and am not sure what it is for. I only have two OS's and know that there is one swap. A logical with nothing on it?
 
I have already explained that to you. Please re-read my previous post. 

> Now that I think of it I'm wondering if I did something wrong during installation. Please tell me...
I choose 'sda' as the install point for boot loader and not 'sda1' or sda5'. Therefore it was at the Drive, not at a particular partition. Should it have been... like on Linux or Windows?

There is NOTHING wrong :)
And you did the right thing by installing GRUB2 (Boot Loader) to sda which is the MBR of your HDD.

A basic knowledge of Partitions, GRUB2 and MBR is required.
I already posted the links for you.

> Also, I made the mounting point for ext4 'linux' at '/'. Should it have been mounted at '/home' or '/root'? I always forget the difference between those three.
/home is recommended but NOT a must.
there is no /root, "/" = root.
 
> How do I reinstall grub 2?
[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by kakashi_12 on 2011-10-25
Ok, I re-installed GRUB2. Same result. Still slow.
I have also removed the background from GRUB2 until we get this figured out.

---

### Post by amjjawad on 2011-10-25
While I was searching for a solution to your problem, I found this:

[http://wiki.debian.org/BootProcessSpeedup](http://wiki.debian.org/BootProcessSpeedup)

It's very interesting and I know it looks a bit complicated.
Perhaps you could install bootchart (available in repositories) because that will give you a better idea of the whole time for your booting process.
For example, it's 70 seconds on my system because it's old ( 5+ years) and I'm using Test IDE HDD.

And I'll keep searching and will let you know :)

_**Edit:**_
Another link: [http://www.techtipsgeek.com/speed-up-boot-up-process-ubuntu-10-04-lucid-lynx/9496/](http://www.techtipsgeek.com/speed-up-boot-up-process-ubuntu-10-04-lucid-lynx/9496/)

---

### Post by kakashi_12 on 2011-10-26
Actually....
Do you know how to install Lilo? 'cause I'm already half way with that. If that doesn't work, I may just use ntldr.

---

### Post by amjjawad on 2011-10-26
> **kakashi_12 said:**
> Actually....
Do you know how to install Lilo? 'cause I'm already half way with that. If that doesn't work, I may just use ntldr.

I don't recommend that. While I was searching and reading different threads/topics, I noticed that the users who installed Lilo, the booting process became much slower. Let's wait for now.
Have another look at my previous post :)

I'll ask some of my friends who are experienced in GRUB2 and Booting. I've been searching for few days now and I didn't find any similar issue to your case.

---

### Post by drs305 on 2011-10-26
I don't know why you have long delays during boot. You could try to make the following changes to /etc/default/grub just to see if these settings are causing a delay. The changes just remove any possible Grub graphics issues.

Removing 'quiet splash' should allow you to see any long delays once control has been passed to the kernel. Regarding Grub, remember that shortly after the Grub menu disappears any delays are associated with the kernel (and the kernel options set in the 'linux' line of the Grub menuentry).

```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
**#**GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="[s]**quiet splash**[/s]"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
**GRUB_TERMINAL=console**

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
**GRUB_GFXMODE=640x480**

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

**GRUB_GFXPAYLOAD_LINUX=text**

```

Save the file and update grub.

---

### Post by kakashi_12 on 2011-10-26
Interesting! That did the trick :)
Thank you.
 
Here's what I still need help with....
[LIST=1]
[*]keyboard shortcuts
[*]abiword save as default
[*]disable tap to click and vertical scrolling both on touchpad
[/LIST]

---

### Post by drs305 on 2011-10-26
> **kakashi_12 said:**
> Interesting! That did the trick :)
Thank you.

:-)

You could try changing some of the things back to regain some of the functionality. If you made all the bold changes, I'd probably reverse them in this order. Update grub each time and see what happens the next time you boot.

Add the # symbol back to *GRUB_TERMINAL=console* 
[LIST]
[*]This will return the display control to gfxterm, rather than like a normal terminal window.
[/LIST]
Change *GRUB_GFXMODE=640x480* if desired.

---

### Post by amjjawad on 2011-10-26
> **kakashi_12 said:**
> Interesting! That did the trick :)
Thank you.
 
Glad it works now :)

THANK YOU, drs305 :D

> 
Here's what I still need help with....
[LIST=1]
[*]keyboard shortcuts
[*]abiword save as default
[*]disable tap to click and vertical scrolling both on touchpad
[/LIST]


For keyboard shortcuts, please check the Lubuntu Documentation/Wiki (check my signature - Lubuntu one stop thread).

For Abiword, I already posted some information for you previously. 

As for disabling the touchpad, I think there are some topics on LXDE Forum but the site is down for 2 days now.
Try to search here on the forum, perhaps you'll find something. You could also use

[www.googlubuntu.com](www.googlubuntu.com)

---

### Post by drs305 on 2011-10-26
> **kakashi_12 said:**
> Interesting! That did the trick :)
Thank you.

:-)

You could try changing some of the things back to regain some of the functionality. If you made all the bold changes, I'd probably reverse them in this order. Update grub each time and see what happens the next time you boot.
[LIST=1]
[*]Add the # symbol back to *GRUB_TERMINAL=console* 
[LIST]
[*]This will return the display control to gfxterm, rather than like a normal terminal window. 
[/LIST]
[*]Change *GRUB_GFXMODE=640x480* if desired.
[LIST]
[*]You can use a higher resolution (smaller text) if you wish. You can find the resolutions available by typing "vbeinfo" in the Grub terminal (CTRL-c from the Grub menu).
[/LIST]
[*]Remove GRUB_GFXPAYLOAD_LINUX=text
[LIST]
[*]This will let Grub determine which mode to use (text or not)
[/LIST]
[*]Add back "quiet splash".
[LIST]
[*]You can do this at any step...
[/LIST]
[/LIST]

---

### Post by kakashi_12 on 2011-10-26
> 
For keyboard shortcuts, please check the Lubuntu Documentation/Wiki (check my signature - Lubuntu one stop thread).
 
For Abiword, I already posted some information for you previously. 
 
 
Sorry, but none of those worked. When I open that file (abiword) to edit, it is a blank file
 
And for that wiki site, there is nothing there about keyboard shortcuts.

---

### Post by kakashi_12 on 2011-10-26
Ok, so far.... I've found this [http://ubuntuforums.org/showthread.php?p=10124399](http://ubuntuforums.org/showthread.php?p=10124399) for editting keyboard shortcuts. Seems to help
 
Ok. I've solved this issue. Only two more to go.
 
What I had to do was edit this file
/home/user/.config/openbox/lubuntu-rc.xml
 
Don't even have to be root to edit it.
After making changes, must run this cmd
openbox --reconfigure

---

### Post by amjjawad on 2011-10-26
You need to learn to be patient and stop opening new threads and asking the same questions :)
You already asked here and I already gave you a reply. If that didn't work, either to wait for another one to jump in or you do some search.

The key binding in the wiki should help you, just change the keys you want to add. Again, LXDE Forum is down so I can't really find those threads.

Good night!

Edit:
My deepest apology, I saw your post on the other thread and I thought it's your thread. My bad.

---

### Post by kakashi_12 on 2011-10-26
[http://ubuntuforums.org/showthread.php?t=1457053](http://ubuntuforums.org/showthread.php?t=1457053)
 
When installing gpointing device settings, i cant find it. It's not in system or preferences or on the menu at all.

---

### Post by amjjawad on 2011-10-26
For Keyboard:

```
sudo leafpad ~/.config/openbox/lubuntu-rc.xml
```

Locate the <keyboard> section and add following lines. 

```
<keyboard>
    <chainQuitKey>C-g</chainQuitKey>
    <!-- Keybindings for desktop switching -->
    <keybind key="C-A-Left">
      <action name="DesktopLeft">
        <dialog>no</dialog>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="C-A-Right">
      <action name="DesktopRight">
        <dialog>no</dialog>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="C-A-Up">
      <action name="DesktopUp">
        <dialog>no</dialog>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="C-A-Down">
      <action name="DesktopDown">
        <dialog>no</dialog>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="S-A-Left">
      <action name="SendToDesktopLeft">
        <dialog>no</dialog>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="S-A-Right">
      <action name="SendToDesktopRight">
        <dialog>no</dialog>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="S-A-Up">
      <action name="SendToDesktopUp">
        <dialog>no</dialog>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="S-A-Down">
      <action name="SendToDesktopDown">
        <dialog>no</dialog>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="W-F1">
      <action name="Desktop">
        <desktop>1</desktop>
      </action>
    </keybind>
    <keybind key="W-F2">
      <action name="Desktop">
        <desktop>2</desktop>
      </action>
    </keybind>
    <keybind key="W-F3">
      <action name="Desktop">
        <desktop>3</desktop>
      </action>
    </keybind>
    <keybind key="W-F4">
      <action name="Desktop">
        <desktop>4</desktop>
      </action>
    </keybind>
    <keybind key="W-d">
      <action name="ToggleShowDesktop"/>
    </keybind>
    <!-- Keybindings for windows -->
    <keybind key="A-F4">
      <action name="Close"/>
    </keybind>
    <keybind key="A-Escape">
      <action name="Lower"/>
      <action name="FocusToBottom"/>
      <action name="Unfocus"/>
    </keybind>
    <keybind key="A-space">
      <action name="ShowMenu">
        <menu>client-menu</menu>
      </action>
    </keybind>
    <!-- Keybindings for window switching -->
    <keybind key="A-Tab">
      <action name="NextWindow"/>
    </keybind>
    <keybind key="A-S-Tab">
      <action name="PreviousWindow"/>
    </keybind>
    <keybind key="C-A-Tab">
      <action name="NextWindow">
        <panels>yes</panels>
        <desktop>yes</desktop>
      </action>
    </keybind>
    <!-- Keybindings for running applications -->
    <keybind key="W-e">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>PCManFM</name>
        </startupnotify>
        <command>pcmanfm</command>
      </action>
    </keybind>
    <!--keybindings for LXPanel -->
    <keybind key="W-r">
      <action name="Execute">
        <command>lxpanelctl run</command>
      </action>
    </keybind>
    <keybind key="A-F2">
      <action name="Execute">
        <command>lxpanelctl run</command>
      </action>
    </keybind>
    <keybind key="C-Escape">
      <action name="Execute">
        <command>lxpanelctl menu</command>
      </action>
    </keybind>
    <keybind key="F11">
      <action name="ToggleFullscreen"/>
    </keybind>
    <!-- Launch Task Manager with Ctrl+Alt+Del -->
    <keybind key="A-C-Delete">
      <action name="Execute">
        <command>lxtask</command>
      </action>
    </keybind>
    <!-- Fast access to Terminal -->
    <keybind key="C-A-T">
      <action name="Execute">
        <command>lxterminal</command>
      </action>
    </keybind>
    <!-- Fast access to filemanager -->
    <keybind key="C-A-D">
      <action name="Execute">
        <startupnotify>
          <enabled>true</enabled>
          <name>PCManFM</name>
        </startupnotify>
        <command>pcmanfm</command>
      </action>
    </keybind>
    <!-- Keybinding for PrintScreen Key -->
    <keybind key="Print">
      <action name="Execute">
        <execute>scrot</execute>
      </action>
    </keybind>
    <keybind key="A-Print">
      <action name="Execute">
        <execute>scrot -s</execute>
      </action>
    </keybind>
    <!-- Keybinding for Volume management -->
    <keybind key="XF86AudioRaiseVolume">
      <action name="Execute">
        <command>amixer -q sset Master 3%+</command>
      </action>
    </keybind>
    <keybind key="XF86AudioLowerVolume">
      <action name="Execute">
        <command>amixer -q sset Master 3%-</command>
      </action>
    </keybind>
    <keybind key="XF86AudioMute">
      <action name="Execute">
        <command>amixer -q sset Master toggle</command>
      </action>
    </keybind>
    <keybind key="XF86WWW">
      <action name="Execute">
        <command>x-terminal-emulator</command>
      </action>
    </keybind>
    <keybind key="XF86Calculator">
      <action name="Execute">
        <command>galculator</command>
      </action>
    </keybind>
    <keybind key="XF86MyComputer">
      <action name="Execute">
        <command>pcmanfm</command>
      </action>
    </keybind>
    <keybind key="XF86Terminal">
      <action name="Execute">
        <command>x-terminal-emulator</command>
      </action>
    </keybind>
    <keybind key="A-m">
      <action name="Execute">
        <command>lxpanelctl menu</command>
      </action>
    </keybind>
    <keybind key="C-l">
      <action name="Execute">
        <command>xscreensaver-command -lock</command>
      </action>
    </keybind>
    <!-- Keybindings for Multimedia Keys and LCD Backlight (alternative when not using gnome-power-manager or xfce4-volumed)
         <keybind key="C-F7">
          <action name="Execute">
            <execute>sleep 2;xset dpms force off</execute>
          </action>
        </keybind>
         <keybind key="C-F10">
          <action name="Execute">
            <execute>xbacklight -dec 10</execute>
          </action>
        </keybind>
         <keybind key="C-F11">
          <action name="Execute">
            <execute>xbacklight -inc 10</execute>
          </action>
        </keybind> -->
  </keyboard>
```

This is the keyboard section.
Now, what exactly you want to add?

---

### Post by amjjawad on 2011-10-26
> **kakashi_12 said:**
> [http://ubuntuforums.org/showthread.php?t=1457053](http://ubuntuforums.org/showthread.php?t=1457053)
 
When installing gpointing device settings, i cant find it. It's not in system or preferences or on the menu at all.

```
sudo leafpad /usr/share/applications/gpointing-device-settings.desktop
```

```
[Desktop Entry]
Name=Pointing devices
Comment=Set your mouse and touchpad preferences
Exec=gpointing-device-settings
Icon=input-mouse
Terminal=false
Type=Application
StartupNotify=true
Categories=GNOME;GTK;Settings;HardwareSettings;
**[COLOR=Red]#[/COLOR]**OnlyShowIn=GNOME;

```

Add **[COLOR=Red]# [/COLOR]**[COLOR=Red][COLOR=Black]and Save the file.
You'll find it Menu > Preferences 
[/COLOR][/COLOR]

---

### Post by kakashi_12 on 2011-10-27
Thank you. I figured out how to edit the keyboard shortcuts for desktop switching and terminal. But for some reason it won't let me set it for Volume. :confused:
 
<keybing key="XF86AudioRaise Volume">
<action name="Execute">
<command>amixer -q sset Master 3%-</command>
</action>
<keybind>
 
Which line do I edit? I tried editting the top line and that did not work.
I even ran the cmd openbox --reconfigure afterwards

The only other shortcut I'd like to set is Lock Screen and i don't see that listed.

Whatever I did wrong before with AbiWord is now fixed. I was able to finally change the default save as.

---

