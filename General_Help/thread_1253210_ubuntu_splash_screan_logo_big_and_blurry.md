---
title: "ubuntu splash screan logo big and blurry"
date: 2009-08-29
forum: General Help
---

### Post by toejamfootball on 2009-08-29
this isn't a big issue, but it is getting to me. I messed around with Startup Manager not long ago, as I wanted an image displayed at the grub menu.

Since then I have decided no to have that image displayed, so I returned all the setting to default and removed startup manager. Now though when the boot reaches the ubuntu splash screen with the loading line underneath it is bigger than it should be and because of this it is blurry.

Any ideas?

Cheers.

---

### Post by SteveDee on 2009-08-30
I wonder if your initial display resolution needs changing. You can do this by editing /boot/grub/menu.lst. Set the kernel "vga" value as required (e.g. "vga=771") from this table:-

```
VESA modes
Colors (depth) 	640x480 	800x600 	1024x768 	1280x1024 	1600x1200
256 ( 8 bit) 	   769 	        771 	    773 	    775 	    796
32,768 (15 bit)    784 	        787 	    790 	    793 	    797
65,536 (16 bit)    785 	        788 	    791 	    794 	    798
16.8M (24 bit) 	    786 	789 	    792 	    795 	    799
```

I would recommend you re-install Startup-Manager as this is a very useful app. You can set the initial display resolution from the Boot Options tab. I suggest you use a safe value like 640x480 or 800x600 (remember that this is just the boot resolution, not the final gui resolution).

---

### Post by toejamfootball on 2009-08-30
I reinstalled Startupmanager and changed the settings and nothing happened. I tried once more and it is normal again. Thanks mate.

---

