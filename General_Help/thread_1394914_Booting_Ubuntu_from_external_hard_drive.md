---
title: "Booting Ubuntu from external hard drive"
date: 2010-01-31
forum: General Help
---

### Post by Melonking on 2010-01-31
Hello there, I am away for two weeks and so I have an install of Ubuntu on an external hd. I installed it on my home computer and it ran fine.
 
But now when I try to boot it from the computer where I am staying the computer will not recignise it as a boot drive. Though it does seem to support usb boot.
 
Both my computer and this one have windows 7 installed and I dont want to affect the windows 7 install or any of its files by booting from my hd.
 
I tryed booting from the ubuntu install disk and my hd showed up fine in that but when I went to set it as the boot disk but it did not have it as an option.

---

### Post by john newbuntu on 2010-01-31
It is possible that when you first installed Ubuntu on your external hard drive, GRUB got into the MBR of your internal HD.  Using your liveCD, open up a terminal, type the following and post the output of meierfra's script.  The output will be a file called RESULTS.txt in the Desktop directory:

```
cd ~/Desktop \
&& wget 'http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.41/boot_info_script041.sh/download' \
&& chmod 755 boot_info_script041.sh \
&& sudo ./boot_info_script041.sh

```

---

