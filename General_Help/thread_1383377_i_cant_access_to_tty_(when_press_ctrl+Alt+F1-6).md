---
title: "i cant access to tty (when press ctrl+Alt+F1-6)"
date: 2010-01-17
forum: General Help
---

### Post by enghezi on 2010-01-17
i use kubuntu 9.10. 

i want access to tty for installing Nvidia driver (195)

but when i press Ctrl+Alt+F1 to F6 , i see just a black screen with blinker cursor! 

and i think so there is a problem in xorg or X11.  

i see some warning and error in xorg log. 

error:
1-  p, li { white-space: pre-wrap; }  XKB: No components provided for device Virtual core keyboard


waring:
1- The directory "/usr/share/fonts/X11/cyrillic" does not exist.
2- AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.3- disabling Keyboard0
4- Disabling Mouse0
5- Couldn't load XKB keymap, falling back to pre-XKB keymap

and full xorg log: [http://pastebin.com/m4c704b62](http://pastebin.com/m4c704b62)

and also there are many Errors in Authentication Log : [http://pastebin.com/m5bb8a77c](http://pastebin.com/m5bb8a77c)

---

### Post by webaake on 2010-04-25
Same problem here but I solved it by adding vga=vesafb to the kernel line in menu.lst (gub.cfg for grub2). This thread is really to the point:

[http://ubuntuforums.org/showthread.php?p=1541970](http://ubuntuforums.org/showthread.php?p=1541970)

tty 1 thru 6 uses the vesafb videodriver built into the kernel. I think it's something with the video card, or possibly that I have another video chip on the motherboard. By the way, I have a Nvidia 7600GS AGP card.

---

