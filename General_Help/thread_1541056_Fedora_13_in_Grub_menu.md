---
title: "Fedora 13 in Grub menu"
date: 2010-07-28
forum: General Help
---

### Post by ubudog on 2010-07-28
Hi, during the fedora install, I told it to resize my Ubuntu install.  This worked without a problem.  After that, I booted up into Fedora and finished the install.  I reinstalled Grub2 via live cd (usb), and booted back up to Ubuntu.  Now, I ran ```
sudo update-grub && sudo update-grub2
``` 
and rebooted.  Fedora 13 wasn't in the menu, so should I manually add it?  If so, how?  Thanks.

---

### Post by theozzlives on 2010-07-28
Restoring GRUB2 and running update-grub should've done it. You sure you did it all right?

---

### Post by oldfred on 2010-07-28
To see where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.


sudo update-grub2 actually just calls update-grub so they are the same.

---

### Post by ubudog on 2010-07-28
Yeah, I did it like it said to do.  How do I add it manually?

---

### Post by oldfred on 2010-07-28
You will have to edit this to be correct for your version and drive/partition. Paste into 40_custom

 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)
See posts 26 & 27
[http://ubuntuforums.org/showthread.php?t=1388777](http://ubuntuforums.org/showthread.php?t=1388777)
menuentry "Fedora 2.6.31.5 on sda7" {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set a2cb340e-b3df-44e3-a602-52d0cb1201c5
    linux /boot/vmlinuz-2.6.31.5-127.fc12.x86_64 root=UUID=a2cb340e-b3df-44e3-a602-52d0cb1201c5 ro         quiet splash
    initrd /boot/initramfs-2.6.31.5-127.fc12.x86_64.img
}

---

### Post by ubudog on 2010-08-04
Thanks for the help, got it fixed.

---

