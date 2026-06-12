---
title: "kUbuntu Live CD - Resolution too high"
date: 2006-03-01
forum: General Help
---

### Post by kodiak41226 on 2006-03-01
I'm trying to run the kubuntu live CD, and I get it up and running fine, but KDE starts in to high of a screen resolution for my LCD monitor (the monitor just says the signal is out of range.) I've been trying to fix the issues without asking for help, but my limited Linux knowledge is coming up short. 

When KDE starts I hit CTRL+ALT+F1 to get to a text console. Once in the text console I type _sudo dpkg-reconfigure xserver-xorg_ to reconfigre the xserver to start at a lower resolution, and normally this would be fine and I would re-boot and problem solved. But, since I'm running a Live CD the settings won't really be saved so rebooting won't help. My question is once I reconfigure the xserver to the new resolution how do I:

1.) exit the text console 
2.) Restart the xserver
3.) Restart KDE

I hope I type this in a way people can understand what I'm talking about. Thanks for your help.

---

### Post by fannymites on 2006-03-01
Sorry if it's not what you're after but the last time I used a live cd (can't remember which distro) I had the opposite problem, my monitor wasn't recognized correctly and I had too low a resolution.  I exited to a text console, reconfigured xorg then typed startx and it started up with my new res.

---

### Post by kodiak41226 on 2006-03-01
I thought typing startx would do it too, but its already running I guess so it doesn't work.

---

### Post by Jucato on 2006-03-01
have you tried stopping KDM first before reconfiguring xorg?
```
sudo /etc/init.d/kdm stop
```
My situation, however, was similar to fannymites. the LiveCD always gave me lower resolutions.

---

### Post by aysiu on 2006-03-01
When you boot up the live CD, instead of pressing **Enter** at the beginning, type ```
boot vga=791
``` or ```
boot vga=788
``` or if that's still too high a resolution, try ```
boot vga=785
```

---

### Post by kodiak41226 on 2006-03-01
> When you boot up the live CD, instead of pressing Enter at the beginning, type
Code:

boot vga=791

or
Code:

boot vga=788

or if that's still too high a resolution, try
Code:

boot vga=785


When I do that I get a error saying:
Cannot find kernel image: boot vga=788
or
Cannot find kernel image: vga=788

---

### Post by aysiu on 2006-03-01
[QUOTE=kodiak41226]When I do that I get a error saying:
Cannot find kernel image: boot vga=788
or
Cannot find kernel image: vga=788[/QUOTE] I'm sorry. I gave you the wrong command. It should be ```
live vga=788
```

---

### Post by Jucato on 2006-03-01
aysiu: what do those numbers represent? 781, 788, 791?

---

### Post by aysiu on 2006-03-01
[QUOTE=Fenyx]aysiu: what do those numbers represent? 781, 788, 791?[/QUOTE] Screen resolutions and color depths.

781 is 640x400, I think.
788 is 800x600.
791 is 1024x768.

---

### Post by Jucato on 2006-03-01
that's great! thanks for the info! now I can try to enjoy the LiveCD with my 1024x768 resolution. (To think that I only found this out after months of using Ubuntu...)

---

