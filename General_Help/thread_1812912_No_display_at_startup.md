---
title: "No display at startup"
date: 2011-07-27
forum: General Help
---

### Post by editheraven on 2011-07-27
I have installed ubuntu 11 (doesn't really matter) and in grub and loading screen of ubuntu (neither at the verbrose shutting down screen) i have no display. It only says that the resolution cannot be displayed. I tryied editing from grub config, even downloading tools for editing the bootmanager. Nothing works.......

---

### Post by wildmanne39 on 2011-07-27
Hi, when you start your system just leave it a lone for a minute and see if it boots,if it does then we can fix that issue once you are booted.

---

### Post by editheraven on 2011-07-27
I can boot. In fact i use the OS right now with no problem whatsoever.

---

### Post by wildmanne39 on 2011-07-27
Hi, try this
```
gksudo gedit /etc/default/grub
```
and change this line:

#GRUB_GFXMODE=640x480

to this:

GRUB_GFXMODE=640x480
Then save and exit the document.
Then do:
```
sudo update-grub
```

Also you can set the 640x480 to 1024x768 and you will have better boot resolution but you do not want to go higher then that.

---

### Post by editheraven on 2011-07-27
Someone recommend me to add this line too
```
GRUB_GFXPAYLOAD_LINUX=1024x768
```What it does?


le : as long as i remember i tryied with that resolution too, and the same thing happens. The thing is that the loading and shutting down screen is not shown either.

---

### Post by wildmanne39 on 2011-07-27
Hi, I you do not need the linux in that line. It sets the resolution for the boot screen and when it shouts down.

---

### Post by editheraven on 2011-07-27
So it should help with both......... One thing. I can set somewhere the bit depth?

---

### Post by wildmanne39 on 2011-07-27
Hi, yes it should fix your problem and no you can not set the depth.

---

### Post by editheraven on 2011-07-27
Well, the same thing............ I'm trying with full hd resolution (my default resolution). Until then, this ```
GRUB_CMDLINE_LINUX=" quiet vga=773"
``` has something to do with video/vga mode?

---

### Post by editheraven on 2011-07-28
I found the fix. Maybe there is a bug somewhere, but after installing grub-pc, the problem is fixed. Consider this thread closed and solved. Thanx :)


ps : a more in-depth fix if grub menu is not shown even if the resolution problem is gone. Just comment out the lines hiddenmenu and hiddenmenu timeout in "/boot/grub/menu.lst". After that sudo update-grub, of course.

---

### Post by wildmanne39 on 2011-07-28
Hi, your welcome! I am glad you got it fixed,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

