---
title: "Changing boot options for live CD"
date: 2010-07-01
forum: General Help
---

### Post by danja1 on 2010-07-01
Quick question, which I can't seem to find an answer to..

I am running Lubuntu 10 from a USB drive. Despite this, I believe this question pertains to any other variant as well. Running from the USB drive with a persistent directory, there is no boot options file that I can locate. As an example, for an installed version, the file /boot/grub/menu.lst can be changed to make boot options permanent. 

Is there any way I can do something similar when booting from a USB live version? Specifically, I want to add "vga=799" to the options without typing it in at every launch.

Or is the only option for something like this actually installing to a USB drive instead of just running the live version?

Thank you.

---

### Post by Rubi1200 on 2010-07-01
> **danja1 said:**
> Quick question, which I can't seem to find an answer to..

I am running Lubuntu 10 from a USB drive. Despite this, I believe this question pertains to any other variant as well. Running from the USB drive with a persistent directory, there is no boot options file that I can locate. As an example, for an installed version, the file /boot/grub/menu.lst can be changed to make boot options permanent. 

Is there any way I can do something similar when booting from a USB live version? Specifically, I want to add "vga=799" to the options without typing it in at every launch.

Or is the only option for something like this actually installing to a USB drive instead of just running the live version?

Thank you.

How did you put it on the USB, with UNetbootin?

If yes, open the USB drive and look for syslinux.cfg (if I am not mistaken) and edit the parameters there. Save and you should be good to go.

Edit: if you used the USB Startup Creator in Ubuntu then I don't know the answer for that only for UNetbootin; sorry.

---

### Post by danja1 on 2010-07-01
> **Rubi1200 said:**
> How did you put it on the USB, with UNetbootin?

If yes, open the USB drive and look for syslinux.cfg (if I am not mistaken) and edit the parameters there. Save and you should be good to go.

Edit: if you used the USB Startup Creator in Ubuntu then I don't know the answer for that only for UNetbootin; sorry.

Actually, I used the Universal USB Installer. Really amazingly simple. I might have been better off with an actual install though.
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Anyways, syslinux.cfg is still used, but adding the line did not seem to change anything. However, by adding the line into another .cfg called text.cfg (found in the same syslinux directory) I was able to make it work. The text.cfg contains the command line options for each of the menu choices, so I simply inserted the vga=37D just after 'splash' on the live launch option. 

It works, although the video mode appears to be 1600x1200 instead of 1900x1200. 37D should be 1920x1200, and if I do it manually the resolution comes out that way. Not a huge deal, maybe I'll play with it more tomorrow. It apparently doesn't accept the normal vga numbers and needs hex codes (hence the 37D).

---

### Post by Rubi1200 on 2010-07-01
> **danja1 said:**
> Actually, I used the Universal USB Installer. Really amazingly simple. I might have been better off with an actual install though.
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Anyways, syslinux.cfg is still used, but adding the line did not seem to change anything. However, by adding the line into another .cfg called text.cfg (found in the same syslinux directory) I was able to make it work. The text.cfg contains the command line options for each of the menu choices, so I simply inserted the vga=37D just after 'splash' on the live launch option. 

It works, although the video mode appears to be 1600x1200 instead of 1900x1200. 37D should be 1920x1200, and if I do it manually the resolution comes out that way. Not a huge deal, maybe I'll play with it more tomorrow. It apparently doesn't accept the normal vga numbers and needs hex codes (hence the 37D).

Any progress is good progress :-)

---

### Post by danja1 on 2010-07-02
I found the answer. I'm not sure why, but changing the mode to "39D" instead of "37D" allows it to boot at 1920x1200 resolution. This is odd, because if you change it to "vga=ask", and type in 37D, it will boot at 1920x1200. However, if you enter "vga=37D" into 'text.cfg', it will boot at the 1600 resolution. Oh well, at least it works now. I've yet to test it on a system that can't handle 1920x1200 though.

---

