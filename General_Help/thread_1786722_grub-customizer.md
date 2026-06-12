---
title: "grub-customizer"
date: 2011-06-20
forum: General Help
---

### Post by ishuA on 2011-06-20
i have ubuntu 11.04 natty OS running on my laptop.i customize splash images using grub customizer but now its not working with error "grub-mkconfig not successfully completed..login as root"..
plzz help

---

### Post by nzjethro on 2011-06-20
To enable root priveledges, type

```
sudo
```
 before your command.

To log in as root, type

```
sudo su root
```

Then your password, then your commands.

Is this what you were meaning?

---

### Post by ishuA on 2011-06-21
i logged in as root and after running grub-customizer i got the following error 

> 
ishu@ishu-Inspiron-N5010:~$ sudo su root
root@ishu-Inspiron-N5010:/home/ishu# grub-customizer
checking for the burg-mkconfig command… 
checking for the grub-mkconfig command… 
/usr/sbin/grub-mkconfig
checking for the update-grub command… 
/usr/sbin/update-grub
checking for the grub-install command… 
/usr/sbin/grub-install
checking for the grub-mkconfig command… 
/usr/sbin/grub-mkconfig
checking for the update-grub command… 
/usr/sbin/update-grub
checking for the grub-install command… 
/usr/sbin/grub-install
process 3692: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
running grub-mkconfig
/etc/default/grub: 34: Syntax error: word unexpected (expecting ")")


---

### Post by nzjethro on 2011-06-23
Good-oh, we've progressed with the problem. By the looks of that exception, something wrong with the grub-customizer file. I've never used grub-customizer, so I'm not qualified to comment on it. I'm sure someone here will have encountered the same error, else if you feel up to it you could try to find the elusive missing ")". If you'd like, copy your /etc/default/grub file here (inside [Code] tags, by clicking the ***#*** in the reply toolbar), and we can take a look at it and see what's wrong.

If you'd like a graphical Grub loader, perhaps look at Burg. I use Burg, and I think it's awesome!

---

### Post by ishuA on 2011-06-23
> 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

export GRUB_MENU_PICTURE="!B)gK6lg!2k~$(KGrHqEOKicEwOSs(TRQBMN)RcCfL!~~_3.JPG"
export GRUB_COLOR_NORMAL="black/black"
export GRUB_COLOR_HIGHLIGHT="magenta/black"
#UNNAMED_OPTION=""
#UNNAMED_OPTION=""
#UNNAMED_OPTION=""

here is the code

---

### Post by nzjethro on 2011-06-23
Fantastic. And if you look at line 34 (from the error message), you'll see this ungodly behemoth:

```
export GRUB_MENU_PICTURE="!B)gK6lg!2k~$(KGrHqEOKicEwOSs(T RQBMN)RcCfL!~~_3.JPG"
```

As you can see, the file name has some pretty ugly unbalanced brackets in there, which I guess the terminal is having problems with.

To sort this out, I would suggest one of two options:

1) Try using the "literal" operator (\) before those brackets. This works for me when shell scripts throw exceptions to spaces in file names. For example, open the file in gedit, using

```
sudo gedit /etc/default/grub
```

Then add \ before the brackets, so you end up with:

```

export GRUB_MENU_PICTURE="!B**\**)gK6lg!2k~$**\**(KGrHqEOKicEwOSs**\**(T RQBMN**\**)RcCfL!~~_3.JPG"

```

Then run

```
sudo update-grub
```

and try again with grub-customiser.

2)
I've not used grub-customiser, so this is just me conjecturing about how you interface with it, but is this jpg a picture that you've selected (maybe through a GUI) to be your grub picture? If yes, locate that picture in your drive, and change it's name to something simple like grubpicture.jpg.

Then either select grubpicture.jpg where you previously selected that massive file name, or change that file name to grubpicture.jpg in the file. You should end up a line like

```
export GRUB_MENU_PICTURE="grubpicture.jpg"
```

Then run

```
sudo update-grub
```


Having never used grub-customiser, this is just me giving advice based on programming knowledge and your exception, so if these don't work note any exceptions it throws, and post back here. I'm sure if I can't figure it out then someone else here will be able to.

---

### Post by ishuA on 2011-06-28
grub customizer is loading but i am not able to customize the grub....i customized the way i wanted but nothing happens....i reinstalled the grub as well as grub customizer but in vain....
when i run sudo update-grub......it reads the image but no grub background display...

---

### Post by ishuA on 2011-07-03
grub customizer is loading but i am not able to customize the grub....i customized the way i wanted but nothing happens....i reinstalled the grub as well as grub customizer but in vain....
when i run sudo update-grub......it reads the image but no grub background display...

---

### Post by oldos2er on 2011-07-03
Have you tried looking for help here: [https://answers.launchpad.net/grub-customizer/+addquestion](https://answers.launchpad.net/grub-customizer/+addquestion)

---

### Post by drs305 on 2011-07-03
I think I'd start by getting rid of the grub picture. As was pointed out earlier, what is currently designated is very odd. Either in Grub Customizer or by directly editing the /etc/default/grub file (unless GC has proxified it and is using an alternate file), I would remove any reference to a picture and see if GC then works.

It's possible the format of the Grub image designation is throwing an error and not allowing GC to save the file. Once you get it working again, try adding the image back in. (And as *nzjethro* suggested, keep the image name you are trying to add simple to help troubleshooting).

---

### Post by ishuA on 2011-07-05
i did the task u asked me to .....but still the image does not show up as grub background....

---

### Post by drs305 on 2011-07-05
> **ishuA said:**
> i did the task u asked me to .....but still the image does not show up as grub background....

If you attach the image you are trying to use we can see if the image is usable to Grub. If you post the contents of your /boot/grub/grub.cfg file we may be able to figure it out.

---

### Post by wildmanne39 on 2011-07-05
Hi, I had a lot of trouble with setting an image in grub customizer, it idid not want to take background images, I had to change the name of the file to .jpg on the end of the name, I believe before it would take it.

---

### Post by deserthowler on 2011-07-06
I don't understand what grub-customizer is but this is how I did it.

```
sudo gedit /etc/grub/05_debian_theme 
```

Then I changed these lines near the beginning of the script to read:

```
 else
  WALLPAPER="/usr/share/images/grub/grubpicture.png"
  COLOR_NORMAL="green/black"
  COLOR_HIGHLIGHT="magenta/black"
fi 
```

I recommend you start with a simple picture to make sure it will work.  It also doesn't hurt to set the picture to the screen size in grub.

Enjoy your picture while you figure out grub-customizer.

Earl

---

### Post by ishuA on 2011-07-06
```

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
set root='(hd0,msdos)'
search --no-floppy --fs-uuid --set=root 127ed892-f2b3-4c11-bf67-41df054a449e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=800x600x24
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos)'
search --no-floppy --fs-uuid --set=root 127ed892-f2b3-4c11-bf67-41df054a449e
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod part_msdos
insmod ext2
set root='(hd0,msdos)'
search --no-floppy --fs-uuid --set=root 127ed892-f2b3-4c11-bf67-41df054a449e
insmod jpeg
if background_image /boot/grub/megan.JPG; then
  true
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
  if background_color 44,0,30; then
    clear
  fi
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos)'
    search --no-floppy --fs-uuid --set=root 127ed892-f2b3-4c11-bf67-41df054a449e
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=127ed892-f2b3-4c11-bf67-41df054a449e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos)'
    search --no-floppy --fs-uuid --set=root 127ed892-f2b3-4c11-bf67-41df054a449e
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=127ed892-f2b3-4c11-bf67-41df054a449e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos)'
    search --no-floppy --fs-uuid --set=root 127ed892-f2b3-4c11-bf67-41df054a449e
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=127ed892-f2b3-4c11-bf67-41df054a449e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos)'
    search --no-floppy --fs-uuid --set=root 127ed892-f2b3-4c11-bf67-41df054a449e
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=127ed892-f2b3-4c11-bf67-41df054a449e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos)'
    search --no-floppy --fs-uuid --set=root 127ed892-f2b3-4c11-bf67-41df054a449e
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=127ed892-f2b3-4c11-bf67-41df054a449e ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos)'
    search --no-floppy --fs-uuid --set=root 127ed892-f2b3-4c11-bf67-41df054a449e
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=127ed892-f2b3-4c11-bf67-41df054a449e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos)'
    search --no-floppy --fs-uuid --set=root 127ed892-f2b3-4c11-bf67-41df054a449e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos)'
    search --no-floppy --fs-uuid --set=root 127ed892-f2b3-4c11-bf67-41df054a449e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root C2461793461786F7
    chainloader +1
}
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

```this is it

---

### Post by drs305 on 2011-07-06
The image is correctly located in grub.cfg. I note it is a JPG image. There are certain limitations to JPG images, so I would recommend that you convert it to a PNG format and then try to use the PNG image.

You can convert jpg images to png images with GIMP or another similar app. In GIMP, you would open the PNG image file ( gksu gedit /boot/grub/megan.JPG ) , then select File, Save As and add a .png extension to the name. 

If GIMP isn't installed and you want to use it, use the Software Center or :
```
sudo apt-get install gimp
```

After saving the file, use Grub Customizer to select the new file, or simply remove the older image (megan.JPG - or whatever GC calls it in /boot/grub) from /boot/grub. Save the Grub Customizer settings or run "sudo update-grub" and watch the terminal to make sure 'megan.png' is located.

Some other suggestions have also been made, such as renaming the .JPG to .jpg (for GC, which made a difference for a poster) or trying a .png image. Again, you could also post your current JPG so we can inspect it.

---

### Post by ishuA on 2011-07-08
i tried this....but the grub background is just as same as before....:(

---

### Post by drs305 on 2011-07-08
> **ishuA said:**
> i tried this....but the grub background is just as same as before....:(

If you run the boot info script and also attach a copy of the image you are trying to use perhaps we can get this figured out. Click the "BIS" link in my signature line, then post the contents of the RESULTS.txt file it generates.

---

### Post by ishuA on 2011-07-11
> 
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for [noparse](,msdos8)[/noparse]/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848    64,514,047    64,307,200   7 NTFS / exFAT / HPFS
/dev/sda3          64,514,048   310,274,047   245,760,000   7 NTFS / exFAT / HPFS
/dev/sda4         310,276,094   625,141,759   314,865,666   f W95 Extended (LBA)
/dev/sda5         310,276,096   474,116,095   163,840,000   7 NTFS / exFAT / HPFS
/dev/sda6         474,118,144   494,598,143    20,480,000   7 NTFS / exFAT / HPFS
/dev/sda7         494,600,192   510,222,335    15,622,144  82 Linux swap / Solaris
/dev/sda8         510,224,384   539,518,975    29,294,592  83 Linux
/dev/sda9         539,521,024   625,141,759    85,620,736  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        C2461793461786F7                       ntfs       System Reserved
/dev/sda2        46B61DC7B61DB87F                       ntfs       Windows7
/dev/sda3        CE96ECE496ECCDD1                       ntfs       Entertainment
/dev/sda5        5CE8B079E8B052CE                       ntfs       Documents
/dev/sda7        337dfc04-cb6a-4d62-ad57-36c128975040   swap       
/dev/sda8        127ed892-f2b3-4c11-bf67-41df054a449e   ext3       
/dev/sda9        cb6cdbae-5771-41ec-ad75-63384232d764   ext3       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /tmp/BootInfo0/sda1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda8        /                        ext3       (rw,errors=remount-ro,commit=0)
/dev/sda9        /home                    ext3       (rw,commit=0)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ishu/Desktop/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")


boot info script

---

### Post by ishuA on 2011-07-11
files attached

---

### Post by drs305 on 2011-07-11
The full contents of RESULTS.txt didn't appear in your last post, but I took your inspire*.png file and placed it in my /boot/grub folder and ran update-grub. It appeared as the Grub background (although a bit fuzzy).

Based on your earlier RESULTS.txt, it should work if you place it in your sda8's /boot/grub folder and have no other .jpg or .png images in that folder and do not have a "GRUB_BACKGROUND" setting in /etc/default/grub. 

This also assumes that there are no Grub Customizer files taking priority. You could look in /etc/grub.d and make sure there are no Grub Customizer scripts overriding the Grub 2 normal setttings.

If you are still having no success, please post the entire contents of your new RESULTS.txt after placing the inspire image in /boot/grub and running update-grub.

---

### Post by NITROCARIO on 2012-05-26
I encountered this error after following the howtoubuntu guide ... I solved it by doing the following:

open terminal and type:

sudo gedit '/etc/default/burg'

Add # before this command GRUB_CMDLINE_LINUX="sudo burg-install "(hd0)" and save the file.

Now type this in terminal:

sudo burg-install "(hd0)"

and now open grub-customizer

problem solved

---

### Post by lisati on 2012-05-26
Back to sleep, old thread!

---

