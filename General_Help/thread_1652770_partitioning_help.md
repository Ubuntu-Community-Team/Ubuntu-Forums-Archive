---
title: "partitioning help"
date: 2010-12-25
forum: General Help
---

### Post by gt8ost4l on 2010-12-25
in windows 7 i extended the partitioning to remove ubuntu but now when i try to log on i get an error and the grub rescue shows up  can anybody help me

---

### Post by Rubi1200 on 2010-12-25
Hi,
did you completely remove the Ubuntu partition?

you need to restore the Windows bootloader to fix this:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Post a screenshot of your setup from Disk Management if you want to make sure.

Thanks.

---

### Post by gt8ost4l on 2010-12-25
im not sure if i completely deleted it and that link didnt help i tried using the terminal and none worked do you know the grub rescue command line

---

### Post by Rubi1200 on 2010-12-26
If you removed Ubuntu from the computer, it is gone.

What happens sometimes is that GRUB leaves vestiges of its bootloader in the MBR.

Using the grub rescue prompt won't help you because there is nothing to get into.

Here is what I suggest:

1. boot a LiveCD and run the boot info script linked at the bottom of my post. Get the results back here so we can be sure.

2. if I am right, and Ubuntu is gone, there are 2 options; a) run the Windows repair 3 times to get the bootloader back, b) use the LiveCD to install a Windows-like bootloader called lilo.

---

