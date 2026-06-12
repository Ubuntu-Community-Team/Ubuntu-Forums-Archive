---
title: "Grub 2 Themes and Boot Stanzas"
date: 2010-10-22
forum: General Help
---

### Post by hal8000 on 2010-10-22
Just installed Ubuntu 10.10 Maverick Meerkat (clean install).
All has gone well, except that on my multi boot linux system
grub2 has identified my other linux systems but fails to boot them.

More specificly, any linux that uses grub2 e.g. Mint is correctly identified
and boots, but any system using legacy grub fails to boot and results in a
kernel panic.

Here's one detected linux system extracted from /boot/grub/grub.cfg that does not boot:

menuentry "PCLinuxOS 2010.7 (on /dev/sda10)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos10)'
        search --no-floppy --fs-uuid --set df52e007-dc91-44b5-8c8b-c8da84397ba8
        linux /boot/vmlinuz BOOT_IMAGE=PCLinuxOS_2010.7 root=UUID=df52e007-dc91-44b5-8c8b-c8da84397ba8 vmalloc=256M splash=silent init=/sbin/bootchartd vga=794
        initrd (hd0,9)/boot/initrd.img

This looks ok, in fact the UUID is ok:
ls /dev/disk/by-uuid/ -l | grep sda10
lrwxrwxrwx 1 root root 11 2010-10-22 13:14 df52e007-dc91-44b5-8c8b-c8da84397ba8 -> ../../sda10

Grub2 starts counting from 1 so should the line starting initrd
be (hd0,10) and not (hd0,9) ?

Also if I edit this does Ubuntu run update-grub and will any changes be overwritten?

Also the community page:

[https://help.ubuntu.com/community/Grub2#Themes](https://help.ubuntu.com/community/Grub2#Themes)

Does anyone know when the themes will be working, the screenshot looks
brilliant.
Thanks in advance.

---

### Post by drs305 on 2010-10-22
Yes, try changing the initrd line to 10. The easiest way to check is to boot to the Grub menu, press "e", then manually make the change and press CTRL-X.

If it works, run "update-grub" and then open grub.cfg to see if it updated it to the correct partition.

If it didn't, the easiest way to solve it would be to add the entry as it appears in grub.cfg to /etc/grub.d/40_custom and make the same change there. Save the file and update-grub.

Note: As you indicated, any change you make directly to grub.cfg will be overwritten anytime update-grub is run.

Added: I haven't seen much discussion on theme enhancements in Grub 2, although they may be happening. Adding a background image to G2 is very easy, but if you want icons and themes then for now you should look into "burg".

---

### Post by hal8000 on 2010-10-22
Thanks very much for a quick reply. 
And special thanks for taking time to post all the other grub2 how-to's. I see I have some reading to catch up on :)

---

