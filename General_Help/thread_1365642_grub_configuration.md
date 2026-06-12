---
title: "grub configuration"
date: 2009-12-27
forum: General Help
---

### Post by gomango on 2009-12-27
I read a bit on grub, but mostly what I find are no good for grub2.

How does one go about setting up boot options?  My family is complaining about the boot-up screen requiring them to arrow down to select windows 7.

I would like to configure windows 7 as the default.

/boot/grub/grub.cfg
```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="5"
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

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
```

And the grub.cfg...
```
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
search --no-floppy --fs-uuid --set 7b4afbe0-28fe-4403-bd86-c4364bf10f98
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
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 7b4afbe0-28fe-4403-bd86-c4364bf10f98
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=7b4afbe0-28fe-4403-bd86-c4364bf10f98 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 7b4afbe0-28fe-4403-bd86-c4364bf10f98
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=7b4afbe0-28fe-4403-bd86-c4364bf10f98 ro single 
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 7b4afbe0-28fe-4403-bd86-c4364bf10f98
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=7b4afbe0-28fe-4403-bd86-c4364bf10f98 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 7b4afbe0-28fe-4403-bd86-c4364bf10f98
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=7b4afbe0-28fe-4403-bd86-c4364bf10f98 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 6c0ea0f30ea0b80a
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```

I would like to make this so that when sudo update-grub does not overwrite any changes in the grub.cfg file when a package is updated.  I am not sure if this happens, but the way I understand is that update-grub creates the grub.cfg from the variables entered in default/grub.

Thanks in advance.

Dave

---

### Post by gomango on 2009-12-27
I think I found the answer here [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Mahngiel on 2009-12-27
Yes, check out that link, but i'll help you to think about something, first.

Follow the directions on the Grub2 doc and edit 40_custom to put windows first on the list.
'sudo gedit /etc/default/grub' and change GRUB_DEFAULT=0 to GRUB_DEFAULT=1.

That will place and highlight Win7 at the top of the list, and let it be autoloaded after the timeout.

---

### Post by oldfred on 2009-12-27
You can also do this from the link you posted:

GRUB_DEFAULT="Ubuntu, Linux 2.6.31-9-generic"

If you refer to Windows by its number, you will have to edit on every update. But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find windows entry in this and copy to
gedit /boot/grub/grub.cfg
and copy here
gksudo gedit /etc/default/grub
GRUB_DEFAULT="Windows Vista (on /dev/sda1)

You can follow Mahngiel but you need to copy 40_custom to 06_custom so it is first then the number will not change.


**[FONT=Arial][/FONT]**

---

