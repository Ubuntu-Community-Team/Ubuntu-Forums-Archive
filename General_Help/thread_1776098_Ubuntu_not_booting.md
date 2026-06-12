---
title: "Ubuntu not booting"
date: 2011-06-05
forum: General Help
---

### Post by Thisisnotanid on 2011-06-05
Hi everyone,

          I recently upgraded to 11.04 on my WUBI and after a while the OS just stopped booting. Every time I try to boot it drops to the grub command line. I can't boot manually because it says file not found when I enter "linux /boot/vmlinuz-2.6.38-8-generic" And I can't repair the installation through the LiveCD as it gives the error message:

"(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs"

Can anyone help with restoring the OS? At least, I would like to be able to recover the files I had there. Thanks in advance!

---

### Post by Rubi1200 on 2011-06-05
Hi and welcome to the forums :-)

That error probably means it was a bad burn or corrupted image on the CD.

One option, if your BIOS allows it, is to create a bootable USB stick with UNetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Alternatively, create another LiveCD since we may be able to help you fix this.

If you do this, please then do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

If you want to access and copy data from the root.disk you can use [ext2read]("http://ext2read.blogspot.com/") to recover any important data.

---

