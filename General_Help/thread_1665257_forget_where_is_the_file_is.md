---
title: "forget where is the file is"
date: 2011-01-12
forum: General Help
---

### Post by crownclown on 2011-01-12
Before this i've edit my grub. for boot ..
but then now i want to re-edit...but i forget where the file is...
but the inner file got things like this

>  menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set c94e5706-5044-4e8a-84d7-f63ccb2ffb4a
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=c94e5706-5044-4e8a-84d7-f63ccb2ffb4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}




---------------------------------------------------------------------------
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set c94e5706-5044-4e8a-84d7-f63ccb2ffb4a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c94e5706-5044-4e8a-84d7-f63ccb2ffb4a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set c94e5706-5044-4e8a-84d7-f63ccb2ffb4a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c94e5706-5044-4e8a-84d7-f63ccb2ffb4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}


-------------------------------------------------------------------------

menuentry "Memory test (memtest86+) " {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set c94e5706-5044-4e8a-84d7-f63ccb2ffb4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200) " {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set c94e5706-5044-4e8a-84d7-f63ccb2ffb4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}



--------------------------------------------------------------------------

This on same partition as windows 7

menuentry "Windows Vista (loader) (on /dev/sda1) " {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 3e5f-3a2b
    chainloader +1
}

win 7 (loader) (on /dev/sda2)


can someone help me with this..

---

### Post by sikander3786 on 2011-01-12
Why do you want to edit it? The most common options can be edited  in /etc/default/grub and then you need to run *sudo update-grub *for those changes to take effect.

Don't ever directly edit grub.cfg.

If you could tell us what you want to achieve by editing, we might be able to give some specific answers.

---

### Post by crownclown on 2011-01-12
> **sikander3786 said:**
> Why do you want to edit it? The most common options can be edited  in /etc/default/grub and then you need to run *sudo update-grub *for those changes to take effect.

Don't ever directly edit grub.cfg.

If you could tell us what you want to achieve by editing, we might be able to give some specific answers.

thx for the info ...
so the file that i was looking for is the grub.cfg ?
well i dint edit any part of the grub.cfg...
it just i have edited a file got that following of notes...
but i try to find it....
is there any way that i could find the inner note of the file that i was searching by using terminal ?

---

### Post by sikander3786 on 2011-01-12
Is this what you are looking for?

```
grep menuentry /boot/grub/grub.cfg
```

It would find and list all the lines with the word 'menuentry'.

---

### Post by crownclown on 2011-01-12
> **sikander3786 said:**
> Is this what you are looking for?

```
grep menuentry /boot/grub/grub.cfg
```It would find and list all the lines with the word 'menuentry'.


yahh..i was looking for this...find it already..oppps
thx man....:D

---

### Post by amsterdamharu on 2011-01-12
User specific menu entries go in /etc/grub.d/40_custom 
for example:
```
menuentry "DOS with ghost and gdisk to repair windows (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 103268b7-c693-4695-ace0-a1c080bee43e
    linux16 /boot/grub/memdisk 
    initrd16 /boot/grub/dos.img
}
```

Changing defaults is done in /etc/default/grub 
For example:
```
GRUB_DEFAULT="Microsoft Windows XP Professional (on /dev/sda1)"
```
to have a menu entry titled "Microsoft Windows XP Professional (on /dev/sda1)" start by default.
or
```
GRUB_CMDLINE_LINUX_DEFAULT="noapic noapci nosplash irqpoll nomodeset xforcevesa"
```
If you're having trouble booting up.

After you've made the changes you have to run:
```
sudo update-grub
```

That will update your /boot/grub/grub.cfg, you are not supposed to directly edit this file.

---

### Post by crownclown on 2011-01-19
> **amsterdamharu said:**
> User specific menu entries go in /etc/grub.d/40_custom 
for example:
```
menuentry "DOS with ghost and gdisk to repair windows (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 103268b7-c693-4695-ace0-a1c080bee43e
    linux16 /boot/grub/memdisk 
    initrd16 /boot/grub/dos.img
}
```Changing defaults is done in /etc/default/grub 
For example:
```
GRUB_DEFAULT="Microsoft Windows XP Professional (on /dev/sda1)"
```to have a menu entry titled "Microsoft Windows XP Professional (on /dev/sda1)" start by default.
or
```
GRUB_CMDLINE_LINUX_DEFAULT="noapic noapci nosplash irqpoll nomodeset xforcevesa"
```If you're having trouble booting up.

After you've made the changes you have to run:
```
sudo update-grub
```That will update your /boot/grub/grub.cfg, you are not supposed to directly edit this file.




so my bios need to be update?
i also try to update my bios for the a42j... but it goes to error...
maybe i should go to  the asus to..thx.... =))

---

### Post by amsterdamharu on 2011-01-19
Grub comes after bios, when you see the grub menu you can assume the bios is working.

---

### Post by crownclown on 2011-02-03
well as what u have said where should i edit my grub..
at the early boot screen 

The boot menu to messy , i just want to make it a simple look
its too long ....
after i update my grub it goes back as usual..
is there any way?

---

### Post by amsterdamharu on 2011-02-03
To prevent "memtest86+" entries in your Grub 2 menu, remove the  "executable" bit from /etc/grub.d/20_memtest86+. Do this by executing the following command:
```
sudo chmod -x /etc/grub.d/20_memtest86+ 
```
To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.


To remove the older kernel entries look here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
under "Removing Entries from Grub 2"

After disabling memtest and uninstalling older kernels you can run
```
sudo update-grub
```

---

