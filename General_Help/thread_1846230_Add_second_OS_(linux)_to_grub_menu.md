---
title: "Add second OS (linux) to grub menu"
date: 2011-09-18
forum: General Help
---

### Post by utnubuuser on 2011-09-18
Hello,

I decided to try Lubuntu on a bit of unused hdd space and installed it.
Because I've had a bit of time with grub before, and because my main Ubuntu install is important to me, I opted NOT to install grub during the final step of the install, thinking that it should be fairly easy to add the new OS to the existing grub menu afterwards.

When the install finished, I rebooted into my main Ubuntu install and ran the update-grub command which located and identified Lubuntu as Ubuntu 10.04 and provided a menu entry for it in grub.

When I try to boot it however, I  get the error message of:
error: cannot read the linux header
error: you need to load the kernel first - press any key to continue  
which returns me to the grub-menu.  
My original main Ubuntu installation boots ok, so I'm hoping someone knows how to identify and add the kernel of the new OS to the grub menu.

My Ubuntu installation is 10.04, and the Lubuntu version is also 10.04

Thanks

the relevant grub-menu entry (no mention of any header...)

> ### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 10.04 LTS (10.04) (on /dev/sda7)" {
        insmod ext2
        set root='(hd0,7)'
        search --no-floppy --fs-uuid --set 616aeaad-da42-417a-aaa4-17bdee5c4ec7
        linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda7
        initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
(END) 


---

### Post by foureyesboy on 2011-09-18
Have you tried changing:
linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda7

to:
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=616aeaad-da42-417a-aaa4-17bdee5c4ec7

---

### Post by garvinrick4 on 2011-09-18
If post 2 fails run this in your bootable install:
[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/") 
If you need help just say so.

---

### Post by utnubuuser on 2011-09-18
thanks 

I cheaped-out and re-installed and it's booting ok.

suppose I was being uncommonly paranoid about messing with my grub because I'd tried installing another linux distro last month and it wreaked havoc with grub and I had to manually load the ubuntu kernel and fix everything... 

thanks for the help..

---

### Post by garvinrick4 on 2011-09-18
> suppose I was being uncommonly paranoid about messing with my grub  because I'd tried installing another linux distro last month and it  wreaked havoc with grubThat is when you install grub-legacy with a install of a grub2 they do not play together well.
I think post2 would have worked but you got er going so its moot.

I have installed many a grub-legacy flavor of linux and choose not to install grub at install usually using anaconder installer and then updated the grub2 install and it put it in as menuentry
and in config and booted fine. 
I was really interested in seeing what your boot_info_script looked like to see what choosing in Ubiquity of not installing grub at the end of install process looked like.
Will have to try it once to see I imagine when feel like doing it. Have a nice day.

---

