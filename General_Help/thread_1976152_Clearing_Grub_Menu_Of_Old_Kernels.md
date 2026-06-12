---
title: "Clearing Grub Menu Of Old Kernels"
date: 2012-05-08
forum: General Help
---

### Post by loukingjr on 2012-05-08
I have Ubuntu 12.04 installed as a guest in VirtualBox and it works fine but, there are two kernels in the grub menu that are no longer installed, (* -18 & *-17) and I can't seem to be able to get rid of them. 

any ideas? I thought I read somewhere it was a known bug but I can't find it now.

---

### Post by searchfgold6789 on 2012-05-08
You can actually use the Software Center to do this by looking up "kernel" and removing the necessary kernel packages. Also, there is a tool called [Ubuntu Tweak]("http://ubuntu-tweak.com/") that can do this easily and automatically for you.

---

### Post by Cavsfan on 2012-05-08
I am not sure about using VirtualBox but, the How to in my signature may help.
Have you tried entering in a terminal **sudo update-grub**?

---

### Post by loukingjr on 2012-05-08
> **Cavsfan said:**
> I am not sure about using VirtualBox but, the How to in my signature may help.
Have you tried entering in a terminal **sudo update-grub**?
yes, I've tried that.

---

### Post by loukingjr on 2012-05-08
> **searchfgold6789 said:**
> You can actually use the Software Center to do this by looking up "kernel" and removing the necessary kernel packages. Also, there is a tool called [Ubuntu Tweak]("http://ubuntu-tweak.com/") that can do this easily and automatically for you.
the kernels are no longer installed but I will see if there is anything left over it may be seeing.

---

### Post by Cavsfan on 2012-05-08
A kernel is comprised of three parts (except the most current one):

linux-headers-2.6.32-40 
linux-headers-2.6.32-40-generic 
linux-image-2.6.32-40-generic

In the case of my backup kernel, those are the parts.

In Synaptic Package Manager, if you query "linux-headers" and "linux-image", it should show you if there are any files left over from older kernels.

---

### Post by philinux on 2012-05-08
> **loukingjr said:**
> the kernels are no longer installed but I will see if there is anything left over it may be seeing.

See step 5. Do a dry run first.

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

### Post by Cavsfan on 2012-05-08
> **philinux said:**
> See step 5. Do a dry run first.

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)


Obviously a better way. Thanks! I bookmarked this myself! :)

---

### Post by loukingjr on 2012-05-08
what is interesting I suppose is the kernels that are showing in the grub menu are not installed, don't show up as installed and don't show in synaptic at all. they are listed in grub.cfg. can I just remove the entries in grub.cfg?

---

### Post by philinux on 2012-05-08
> **loukingjr said:**
> what is interesting I suppose is the kernels that are showing in the grub menu are not installed, don't show up as installed and don't show in synaptic at all. they are listed in grub.cfg. can I just remove the entries in grub.cfg?

grub.cfg gets generated from update-grub so no.

See post 7

---

### Post by loukingjr on 2012-05-08
> **philinux said:**
> grub.cfg gets generated from update-grub so no.

See post 7
I saw post 7. I ran the commands up to the dry run. the offending kernels do not show up.

the two kernels in question are...
Linux 3.2.0-18-generic-pae
Linux 3.2.0-17-generic-pae

they are in my grub.cfg file but not installed and not listed in synaptic.

---

### Post by Cavsfan on 2012-05-08
Post the results of 
```
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
```

and the output of **sudo grub-mkconfig**

---

### Post by philinux on 2012-05-08
+1 ^^ also post the output of sudo update-grub

Lets see what it's finding.

---

### Post by loukingjr on 2012-05-08
> **Cavsfan said:**
> Post the results of 
```
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
```and the output of **sudo grub-mkconfig**
louis@louis-VirtualBox:~$ grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
     0    Ubuntu, with Linux 3.2.0-24-generic-pae
     1    Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode)
     2    Ubuntu, with Linux 3.2.0-23-generic-pae
     3    Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)
     4    Memory test (memtest86+)
     5    Memory test (memtest86+, serial console 115200)
     6    Ubuntu, with Linux 3.2.0-18-generic-pae (on /dev/sda1)
     7    Ubuntu, with Linux 3.2.0-18-generic-pae (recovery mode) (on /dev/sda1)
     8    Ubuntu, with Linux 3.2.0-17-generic-pae (on /dev/sda1)
     9    Ubuntu, with Linux 3.2.0-17-generic-pae (recovery mode) (on /dev/sda1)
louis@louis-VirtualBox:~$

---

### Post by loukingjr on 2012-05-08
didn't see the other command...
```
louis@louis-VirtualBox:~$ sudo grub-mkconfig
[sudo] password for louis: 
Generating grub.cfg ...
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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set=root 25da6b6b-e6a8-4fa0-9d8b-949a19a7c249
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos6)'
  search --no-floppy --fs-uuid --set=root 25da6b6b-e6a8-4fa0-9d8b-949a19a7c249
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
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
function gfxmode {
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
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
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 25da6b6b-e6a8-4fa0-9d8b-949a19a7c249
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=25da6b6b-e6a8-4fa0-9d8b-949a19a7c249 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 25da6b6b-e6a8-4fa0-9d8b-949a19a7c249
    echo    'Loading Linux 3.2.0-24-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-24-generic-pae root=UUID=25da6b6b-e6a8-4fa0-9d8b-949a19a7c249 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-24-generic-pae
}
submenu "Previous Linux versions" {
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 25da6b6b-e6a8-4fa0-9d8b-949a19a7c249
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=25da6b6b-e6a8-4fa0-9d8b-949a19a7c249 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 25da6b6b-e6a8-4fa0-9d8b-949a19a7c249
    echo    'Loading Linux 3.2.0-23-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-23-generic-pae root=UUID=25da6b6b-e6a8-4fa0-9d8b-949a19a7c249 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic-pae
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 25da6b6b-e6a8-4fa0-9d8b-949a19a7c249
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set=root 25da6b6b-e6a8-4fa0-9d8b-949a19a7c249
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
Found Ubuntu precise (development branch) (12.04) on /dev/sda1
menuentry "Ubuntu, with Linux 3.2.0-18-generic-pae (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 536e78db-dcdb-43ad-9b56-4b72d5044067
    linux /boot/vmlinuz-3.2.0-18-generic-pae root=UUID=536e78db-dcdb-43ad-9b56-4b72d5044067 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.2.0-18-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-18-generic-pae (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 536e78db-dcdb-43ad-9b56-4b72d5044067
    linux /boot/vmlinuz-3.2.0-18-generic-pae root=UUID=536e78db-dcdb-43ad-9b56-4b72d5044067 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-18-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-17-generic-pae (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 536e78db-dcdb-43ad-9b56-4b72d5044067
    linux /boot/vmlinuz-3.2.0-17-generic-pae root=UUID=536e78db-dcdb-43ad-9b56-4b72d5044067 ro quiet splash vt.handoff=7
    initrd /boot/initrd.img-3.2.0-17-generic-pae
}
menuentry "Ubuntu, with Linux 3.2.0-17-generic-pae (recovery mode) (on /dev/sda1)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 536e78db-dcdb-43ad-9b56-4b72d5044067
    linux /boot/vmlinuz-3.2.0-17-generic-pae root=UUID=536e78db-dcdb-43ad-9b56-4b72d5044067 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-17-generic-pae
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

```

---

### Post by philinux on 2012-05-08
> Ubuntu, with Linux 3.2.0-18-generic-pae (on /dev/sda1)

What you got on /dev/sda1 ?

---

### Post by loukingjr on 2012-05-08
hmmm, I installed gparted and I seem to have two partitions with ubuntu installed. however, if I try to start the sda1 partition I get nothing.

---

### Post by philinux on 2012-05-08
> **loukingjr said:**
> hmmm, I installed gparted and I seem to have two partitions with ubuntu installed. however, if I try to start the sd1 partition I get nothing.

Run

```
sudo update-grub
```

To see where it's getting these from. It should show the full path.

---

### Post by drs305 on 2012-05-08
I have an ulterior reason for posting here, but I can also give you a workaround if I understand your situation.

If what you are posting is in your VB, since the extra kernels (and only the extra kernels) are in the 30_os-prober section of your menu, you could simply turn off that Grub script. [You could do this in a real installation as well, but this would not allow the system to find newly introduced OS's, which might be more important in an actual OS/] The simple way of doing this is making the script unexecutable within VB:
```
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
```

Now for the second part (the ulterior motive):
Before you fix things, could you take screenshot of your Grub menu with the current setup and attach it to a post? (A pic of the Grub menu before it boots. If you don't normally see it, hold down the SHIFT key just as the VB splash screen disappears .)

I am about to post a community doc on Grub submenus, but the only way I can get boot pics is via VB. My VB installs never pick up real drive installations, so I never get any to take pics of Grub menus with entries in the 30_os-prober section.

Thanks.

---

### Post by loukingjr on 2012-05-08
> **philinux said:**
> Run

```
sudo update-grub
```To see where it's getting these from. It should show the full path.
I think I know what happened. I had the beta releases in sda1 and when the release came out I must of installed it to a second partition. sda6. don't ask me why lol. 

for whatever reason sda1 will no longer boot. I can just delete sda1 and resize sda6.
```
louis@louis-VirtualBox:~$ sudo update-grub
[sudo] password for louis: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu precise (development branch) (12.04) on /dev/sda1
done

```

---

### Post by Cavsfan on 2012-05-08
See post #19 please.

---

### Post by loukingjr on 2012-05-08
> **Cavsfan said:**
> See post #19 please.
that was sort of a pain...lol
[IMG]https://lh4.googleusercontent.com/-OUKBewcdOfI/T6lDUNrC-9I/AAAAAAAAMUc/N8wCcJmfd5A/s640/screenshot_115.jpg[/IMG]

---

### Post by drs305 on 2012-05-08
> **loukingjr said:**
> that was sort of a pain...lol


Thank you !

---

### Post by loukingjr on 2012-05-08
you're welcome :mad:

---

### Post by loukingjr on 2012-05-08
thanks for the help everyone. sorry I forgot I had a second partition :rolleyes:

everything is fine now that I deleted it. :lolflag:

---

