---
title: "Is GRUB necessary on a Xubuntu-only machine?"
date: 2009-09-30
forum: General Help
---

### Post by djmoore85 on 2009-09-30
Hey yall. I am trying to clean up my Xubuntu install on my laptop. Since it is the only OS on the machine, is GRUB even a necessary component? Is there a way to possibly get rid of GRUB so I can streamline and optimize the boot process? I have set the menu.lst delay to 0s. I am hopin that maybe GRUB can be skipped altogether at boot. Also, as a side note, is there a way to go through my installation to ensure that all files, folders and directories (hidden or otherwise) from previous applications are removed and gone?

---

### Post by earthpigg on 2009-09-30
hi,

something needs to start Xubuntu. all operating systems need and use a bootloader, though [some hide that from you until something breaks]("http://www.withinwindows.com/wp-content/uploads/2008/12/menu3.png").

if you aren't happy with grub, you could look at [LILO]("http://en.wikipedia.org/wiki/LILO_%28boot_loader%29").

---

### Post by djmoore85 on 2009-10-02
Thats fine. I was just checking to see if it was necessary to the boot-up process or just an "aftermarket" setup for dual-booting. Would LILO be any faster? Also, does anyone have thoughts or suggestions on streamlining and optimizing Xubuntu for faster speeds? I have an older laptop, and it certainly runs much more efficiently than with XP, I am however always looking to squeeze every bit out of :guitar: it before I go to upgrading hardware.

---

### Post by anonymous_user on 2009-10-02
Rather than use the bloated Xubuntu, you could install a minimal Ubuntu + Xfce. It would be lighter.

If you want something even lighter, then maybe consider Openbox or Fluxbox instead of Xfce.

---

### Post by earthpigg on 2009-10-02
no, i dont think lilo would be any faster.

if you install the startup-manager package, you can reduce that 1.5 second delay to 0 seconds.

---

### Post by djmoore85 on 2009-10-05
Sounds interesting. Anonymous, how would I go about installing "minimal" Ubuntu? Are we talking CLI Ubuntu only and then Xfce on top of that? Does sound very nice how would I go about accomplishing this? And pigg, thank you for the suggestion I'll give that package a shot

---

### Post by orange-wedge on 2009-10-05
You can modify the number if seconds for grub to wait before loading the default entry.  I think the default time to wait is 3 seconds so you could probably reduce that to 1 second if you want to speed up the boot time.  To change this modify the 'timeout' value from your /boot/grub/menu.lst file

Also getting rid of the Ubuntu splash screen has been found to speed up boot time as well, so again within the /boot/grub/menu.lst on the line for your kernel remove the words 'quiet splash'.

---

### Post by djmoore85 on 2009-10-05
Thank you orange-wedge. I took the menu.lst and made the delay seconds "0" the first time around trying to make the boot-time faster. I will see about removing that splash screen as well

---

