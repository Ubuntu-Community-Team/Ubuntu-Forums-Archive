---
title: "Second HD added share rights"
date: 2010-11-19
forum: General Help
---

### Post by georgemcbaingage on 2010-11-19
This probably something simple but it's got me foxed. I have a desktop and a laptop both running 10.04 great no issues, I have my music and movies on the desktop and stream wirelessly  to my laptop.

All worked great until I started to run out of space on the base units hard drive, no problem I added a second 500gig sata drive internally and moved the music and movie folders across.
Now although I have marked them as shares I access them remotely, the second drive has to be mounted and appears almost like a external drive.
What have I done wrong?

Thanks in advance

---

### Post by searchfgold6789 on 2010-11-19
Well you have to add it to your fstab.
You can do that like this:

[LIST=1]
[*]From the terminal, type ```
sudo blkid
``` and make note of your filesystem's UUID.
[*]Also from the terminal, type ```
sudo mkdir /media/<mountpoint>
```
[*]When it finishes, type ```
sudo gedit /etc/fstab
```
[*]A file will come up that has the UUID's and options for all of your files. At the bottom of the file, type: UUID=your-uuid-from-step-one /media/<mountpoint> ext4 auto,rw,user,exec 0 2
[*]Make sure there is a blank line at the end of the file.
[*]Press Ctrl+S to save.
[*]Reboot.
[/LIST]
You have to do this often with file systems, particularly if you did not have them configured when you first installed Ubuntu.
In step 3 there is a line of code, and in that line is "ext4". If you formatted your drive with something other than ext4, for example ntfs, replace it with that file system type.

---

