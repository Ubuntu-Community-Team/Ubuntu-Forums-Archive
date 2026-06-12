---
title: "How to revert to kernel 2.6.36"
date: 2011-07-23
forum: General Help
---

### Post by Toske on 2011-07-23
Hello!

I'm a newbie user of Ubuntu Natty, having this wifi wireless dongle that seems to work best with kernel 2.6.36. Is there a way to get it from repos through Synaptic or apt and how, or do I have to compile it myself?

---

### Post by thefasterblueone on 2011-07-23
Post the output of:

```
cat /boot/grub/grub.cfg

```

---

### Post by Toske on 2011-07-23
Here goes:
```
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
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 16ae0e17-b019-4cfc-b5f5-57ce8b96fd4d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 16ae0e17-b019-4cfc-b5f5-57ce8b96fd4d
set locale_dir=($root)/boot/grub/locale
set lang=sr_RS
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
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
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos5)'
    search --no-floppy --fs-uuid --set=root 16ae0e17-b019-4cfc-b5f5-57ce8b96fd4d
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=16ae0e17-b019-4cfc-b5f5-57ce8b96fd4d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}

```

---

### Post by thefasterblueone on 2011-07-23
Run this to find available kernels:

```
apt-cache search linux-image
```

After finding a kernel run this to install it

```
sudo apt-get install linux-image-x.x.x-xx
```

replacing the " x.x.x-xx " with the version number from your search.

Then run:

```
sudo update-grub
```

then:

```
sudo reboot
```

---

### Post by Toske on 2011-07-23
I have already checked apt that way but there is nothing non 2.6.38.x. Was hoping that as a newbie I have not set all repos aright. So, will have to roll my own kernel than, tnx thefasterblueone! :)

---

