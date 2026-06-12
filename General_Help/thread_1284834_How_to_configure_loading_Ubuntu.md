---
title: "How to configure loading Ubuntu"
date: 2009-10-07
forum: General Help
---

### Post by mr.suchy on 2009-10-07
Hi,

I search this in forum but I can't find any results what I want. Afert GRUB menu, ubuntu display logo (ubuntu logo). In other OS is a black screen with white text. OS display modules and check status OK or FAILED. How can I change ubuntu logo to this black and white screen ? and how can I change resolution of my scrren in this windows ?

Best regards!

---

### Post by plucky on 2009-10-07
> **mr.suchy said:**
> Hi,

I search this in forum but I can't find any results what I want. Afert GRUB menu, ubuntu display logo (ubuntu logo). In other OS is a black screen with white text. OS display modules and check status OK or FAILED. How can I change ubuntu logo to this black and white screen ? and how can I change resolution of my scrren in this windows ?

Best regards!

So you want to have the text on startup.

Use ```
gksudo gedit /boot/grub/menu.lst
``` and remove the **quiet** and **splash** from the kernel line. > title		Ubuntu 9.04, kernel 2.6.28-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=03aa7483-5b8f-4c1e-bd09-5db055ead5eb ro [color=red]quiet splash[/color] 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet


Good Luck

---

### Post by mr.suchy on 2009-10-07
Thanks. One question, where can I change the resolution ? in grub menu ?:confused:

---

### Post by plucky on 2009-10-07
> **mr.suchy said:**
> Thanks. One question, where can I change the resolution ? in grub menu ?:confused:

You can add the **vga=???** and substitute ??? according to this table in the kernel line that you removed quiet and splash from.
 ```
 
Screen  640x480  800x600 1024x768 1280x1024 1600x1200
Colors 					
256        769 	  771      773 	    775 	796
32,768 	   784 	  787 	   790 	    793         797
65,536 	   785 	  788 	   791 	    794 	798
16.8M 	   786 	  789 	   792 	    795 	799

```

As long as your video card supports the resolution without the normal driver loaded.Not all resolutions are supported with the splash screen.


Good Luck

---

