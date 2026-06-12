---
title: "dual booting problem"
date: 2011-06-01
forum: General Help
---

### Post by paradive on 2011-06-01
ok, i want grub to default to Windows.
every resource i can find tells me to edit the default in /boot/grub/menu.lst, but, as you can see, there ISN'T one:
mdraid09.mod        udf.mod
efiemu.mod                   mdraid1x.mod        ufs1.mod
elf.mod                      memdisk.mod         ufs2.mod
example_functional_test.mod  memrw.mod           uhci.mod
ext2.mod                     minicmd.mod         usb_keyboard.mod
extcmd.mod                   minix2.mod          usb.mod
fat.mod                      minix.mod           usbms.mod
font.mod                     mmap.mod            usbserial_common.mod
fshelp.mod                   moddep.lst          usbserial_ftdi.mod
fs.lst                       msdospart.mod       usbserial_pl2303.mod
functional_test.mod          multiboot2.mod      usbtest.mod
g2hdr.img                    multiboot.mod 

and i tried editing /etc/defaults/grub but that didn't work.

any ideas?

---

### Post by oldfred on 2011-06-02
You have grub2. Menu.lst is from grub legacy, old grub, or grub 0.97.  Grub2 is not yet at version 2 but is just the name for the second version of grub. Current version with Natty is 1.99.

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Older manual way:
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by paradive on 2011-06-02
> **oldfred said:**
> You have grub2. Menu.lst is from grub legacy, old grub, or grub 0.97.  Grub2 is not yet at version 2 but is just the name for the second version of grub. Current version with Natty is 1.99.

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Older manual way:
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

General info:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

D'OH!
i forgot about that.
thanks. good info.
after editing /boot/grub/grub.cfg it spit out: 

(gedit:4185): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.M05LWV': No such file or directory

seems innocent enough, but i'll see if it worked.
now to get mp3s playing... WHY THE HELL doesn't in come with an encoder?! and now Banshee isn't prompting me to download one. :icon_frown:

it's gonna be a long *** night.

---

