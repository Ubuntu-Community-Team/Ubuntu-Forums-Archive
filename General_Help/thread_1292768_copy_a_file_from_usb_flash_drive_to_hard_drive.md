---
title: "copy a file from usb flash drive to hard drive?"
date: 2009-10-16
forum: General Help
---

### Post by s9032g@comcast.net on 2009-10-16
I am very new to Ubuntu. I have a file on a usb flash drive that I want to copy to my hard drive (Dell Mini 9). How do I go about this? How do I find (point to) the file after putting it on the hard drive?

What I am trying to do here is update my bios to A05 from an active flasher.img file present on my flash drive.

Thanks

STEVEG

---

### Post by falconindy on 2009-10-16
It should pop up under 'Places' on the main menu and you can browse it via Nautilus. If you'd like to find it on the command line, removable media will be mounted in a directory under /media.

---

### Post by Niko Johnson on 2009-10-16
if you want to do it the hard way ( the fun way) you can go in the terminal and copy your file from the /media directory to your /home directory (or any directory you want or have permissions to) ```
 cp -fr /media/flashdrive/file /home/user 
```

---

### Post by s9032g@comcast.net on 2009-10-17
How about if use Ubuntu Tweak to show my home file on the desktop, then I copy my flasher.img file (the one with the A05 Bios) to that home file; then umount the flash drive in terminal. Then use a command like this: sudo dd if=flasher.img of=/dev/sdb. I can copy/paste the proper path from the home file. I am not at ease with this, so any suggestions are welcome.

Thanks

SteveG

---

