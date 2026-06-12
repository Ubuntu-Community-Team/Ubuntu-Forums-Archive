---
title: "fails to boot either Vista or Ubuntu 10."
date: 2010-07-13
forum: General Help
---

### Post by so_utah_nube on 2010-07-13
new user:

I powered up laptop and got error message prompt. Something about ? rescue.
At prompt, I entered sudo fdisk -l. Came back with disk partitions.

How do I recover back to Vista and Ubuntu choice?

---

### Post by oldfred on 2010-07-14
Welcome to the forums.

If you got a list of partitions you must have booted to a command line.

This will find other systems. (but if windows is not working it may not)
sudo update-grub

If you want to start gui
sudo service gdm start

If you are getting only to a command line are you having video card issues? What video card do you have?

---

### Post by so_utah_nube on 2010-07-14
Did get a command line.
Tried sudo update-grub and it could not find /boot/grub/menu.lst.
And message Would you like /boot/grub/menu.lst generated?
Splash image not found. Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ..done

---

### Post by oldfred on 2010-07-14
Even though you are getting to a command line, you grub should be ok, but just to see your configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

