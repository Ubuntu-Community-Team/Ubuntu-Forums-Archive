---
title: "New problem with GRUB2"
date: 2010-07-09
forum: General Help
---

### Post by Mark Phelps on 2010-07-09
Been using GRUB2 for some time now, ever since it came out in beta form in the Karmic days, and until now, have had no problems with it.

But recently, I decided to do the following:
1) Move my Clonezilla live installation from my Karmic drive to my Lucid drive
2) Change from booting Clonezilla live install to booting from the Clonezilla live ISO

Short version, it now works OK.

Longer version ... GRUB does add the boot stanza to its menu list but it doesn't eacho that fact when I run update-grub.

I followed the instructions from the Clonezilla site when modifying the 40_custom file and it is as follows:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Clonezilla Live" >&2
cat << EOF
menuentry "Clonezilla Live" {
set isofile="/boot/isos/clonezilla-live-1.2.5-32-i686.iso"
loopback loop $isofile
linux (loop)/live/vmlinuz boot=live union=aufs nolocales noprompt vga=791 ip=frommedia toram=filesystem.squashfs findiso=$isofile
initrd (loop)/live/initrd.img
}
EOF
```

To simplify testing, I disconnected all my other drives so that only the Lucid drive is connected.  Did that to prevent GRUB 2 getting confused by finding stuff on other drives.

Problem is, when I run sudo update-grub, I get the following:

```
Generating grub.cfg ...
Found Debian background: linuxugos.png
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

And, yes, the 40_custom file is marked as being executable.

You'll notice that there is no mention of the 40_custom file, and the "echo" line is NOT getting echoed.

The following is the segment from the grub.cfg file:

```
### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Clonezilla Live" >&2
cat << EOF
menuentry "Clonezilla Live" {
set isofile="/boot/isos/clonezilla-live-1.2.5-32-i686.iso"
loopback loop $isofile
linux (loop)/live/vmlinuz boot=live union=aufs nolocales noprompt vga=791 ip=frommedia toram=filesystem.squashfs findiso=$isofile
initrd (loop)/live/initrd.img
}
EOF
### END /etc/grub.d/40_custom ###

```
What minor thing am I missing?

UPDATE:  Wow -- must be a really tough problem!! Two days now -- and not a single response from anyone!

---

