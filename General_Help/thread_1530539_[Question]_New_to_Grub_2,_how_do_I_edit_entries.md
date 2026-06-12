---
title: "[Question] New to Grub 2, how do I edit entries?"
date: 2010-07-13
forum: General Help
---

### Post by iammeagain on 2010-07-13
I used Ubuntu a few years back. I simply was not able to make it my main OS since I couldn't get video calling to work reliably enough. Anyways I just installed and noticed my grub menu had many more entries then I have operating systems on my computer. Some reason they came up as duplicates. I have so far gathered they took away my menu.lst, they replaced it with something like etc/general/grub. It appears editing this file doesn't give me the ability to change entries. There are a few I would like to rename, and a few I want to get rid of. There is also some other file that is not supposed to be edited, will I need to edit this or is there another way around it?

I found info like this, but it is only adding not removing. 

> **Brandon Williams said:**
> Assuming that you already looked at the grub2 documentation and had trouble figuring out what to do, try this ...

Use sudo to edit /etc/grub.d/40_custom. It will look like this:
```
#!/bin/sh 
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Supergamer" {
    set root=(hd0,3)
    linux /boot/vmlinuz root=/dev/sda3 ro quiet splash
    initrd /boot/initrd
}
menuentry "Supergamer (recovery)" {
    set root=(hd0,3)
    linux /boot/vmlinuz root=/dev/sda3 ro single
    initrd /boot/initrd
}
```

After making the change, run 'sudo update-grub' to apply the change to your grub config.

TLDR: Grub 2 added extra entries, how do I remove and rename some?

---

### Post by drs305 on 2010-07-13
The added entries are:
1. Linux kernels. Each time the kernel updated, the new kernel is added to the Grub 2 menu. Older kernels remain so the list grows.

The easiest way to remove the older kernels is to install and use Ubuntu Tweak. It's advised to keep at least one older kernel that you know works.
Here is a link on how to use Ubuntu Tweak, as well as other ways to remove older kernels. Look about 2/3 down the first post:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

2. Memtest
If you don't want this to be displayed on the menu, run this command to remove the executable bit from the script that normally adds it:
```
sudo chmod -x /etc/grub.d/20_memtest86+
```

3. Recovery Mode
Normally this is a good option to retain for newbies. It allows you to boot into the recovery mode from the main Grub 2 menu. If you don't want it, open the following file as root:
```
gksu gedit /etc/default/grub
```
Remove the **#** symbol from the start of this line:
> #GRUB_DISABLE_LINUX_RECOVERY="true"

After any of these changes, you must update grub:
```
sudo update-grub
```

For tweaking titles, etc, take a look at the "G2 Title Tweaks" link in my signature line - but be warned - it's pretty geeky stuff!  ;-)

You may want to build/edit a custom menu. A template is already provided at /etc/grub.d/40_custom. Here is one link on how to build one:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu")

---

### Post by iammeagain on 2010-07-13
Oh sorry I didn't explain enough I guess, I have multiple Windows entries. I have selected two different ones that take me to the same Operating System. There is also a recovery partition that came with the computer that it thinks is Window Vista, so I would like to rename that one.  

I plan on leaving the recovery mode, and I only have one kernel installed so far. From what I read I believe I can't hide the grub menu when I have multiple OS's installed. I think the old grub gave me an option like press esc to view entries or it would boot to default. I'm more wanting to remove the multiple windows entries. 

Thanks for the fast reply. :)

---

### Post by drs305 on 2010-07-13
You can copy the entries you want to the 40_custom file, and then disable /etc/grub.d/30_os-prober file completly. Then when you update grub it won't look on other partitions for your Windows installs and will use only your custom file for other OS's. 

This would be your easiest solution by far. The advantage is you can put only the Windows entries you want, you can name them what you want, and won't be bothered by all the geek stuff.

If you need help, just provide the Windows menuentries from /boot/grub/grub.cfg and we can help you build a custom menu.

If you want to get into the nuts & bolts, the things you want to to are covered in the Title Tweaks thread, linked to in my signature line.

---

### Post by iammeagain on 2010-07-13
I think I can get it from there. Thats the info I was looking for. If not I can go through those links as you said. Thanks a bunch :D

---

### Post by iammeagain on 2010-07-14
So I got it pretty much as I wanted. I left the original setup that I can get to by using the Shift key. I was going to try and add a count down to it now. I'll post what my files looked like if anyone wants for reference, I had to use the original kernel because the updated one brings me to a command line interface and no gui. I think it has something to do with my video card (Nvidia gt240m), thats for a different thread though I think.

grub.cfg
```
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
set default="Custom Menu"
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 1daadbbd-7b01-486b-9794-7a2aeecac7ae
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 1daadbbd-7b01-486b-9794-7a2aeecac7ae
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=3
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 1daadbbd-7b01-486b-9794-7a2aeecac7ae
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=1daadbbd-7b01-486b-9794-7a2aeecac7ae ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 1daadbbd-7b01-486b-9794-7a2aeecac7ae
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=1daadbbd-7b01-486b-9794-7a2aeecac7ae ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 1daadbbd-7b01-486b-9794-7a2aeecac7ae
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=1daadbbd-7b01-486b-9794-7a2aeecac7ae ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 1daadbbd-7b01-486b-9794-7a2aeecac7ae
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=1daadbbd-7b01-486b-9794-7a2aeecac7ae ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 1daadbbd-7b01-486b-9794-7a2aeecac7ae
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 1daadbbd-7b01-486b-9794-7a2aeecac7ae
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fcc456cbc45687b2
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set daa41c49a41c2b11
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb2)" {
	insmod ntfs
	set root='(hd1,2)'
	search --no-floppy --fs-uuid --set 921c18621c18441f
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb3)" {
	insmod ntfs
	set root='(hd1,3)'
	search --no-floppy --fs-uuid --set c68e93c18e93a907
	chainloader +1
}
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

        menuentry "Custom Menu"{
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 1daadbbd-7b01-486b-9794-7a2aeecac7ae
        configfile /boot/grub/custom_menu.cfg
        }
        ### END /etc/grub.d/40_custom ###

```
custom_menu.cfg
```
### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###
### BEGIN /etc/grub.d/10_linux ###
menuentry 'Kubuntu, v10.04 k2.6.32-21' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 1daadbbd-7b01-486b-9794-7a2aeecac7ae
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=1daadbbd-7b01-486b-9794-7a2aeecac7ae ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set fcc456cbc45687b2
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

```

etc/default/grub
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT="Custom Menu"
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

40_custom
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

        menuentry "Custom Menu"{
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set 1daadbbd-7b01-486b-9794-7a2aeecac7ae
        configfile /boot/grub/custom_menu.cfg
        }
        
```

---

