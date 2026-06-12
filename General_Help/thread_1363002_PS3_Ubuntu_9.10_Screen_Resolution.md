---
title: "PS3 Ubuntu 9.10 Screen Resolution"
date: 2009-12-23
forum: General Help
---

### Post by plip on 2009-12-23
Apologies if this has been asked already. I installed Xubuntu 9.04 and updated to 9.10 on my PS3 on a standard TV and was wondering if there's any way to make it run fullscreen.

---

### Post by alanjcfs on 2009-12-25
This is what I've discovered from my own experience, but they may not necessarily apply to you. It's not too common for people to install Ubuntu on PS3, so there aren't much stuff online.

If you type ps3videomode in the Terminal, you should get this output:

```
YUV 60Hz 1:480i 2:480p 3:720p 4:1080i 5:1080p
YUV 50Hz 6:576i 7:576p 8:720p 9:1080i 10:1080p
RGB 60Hz 33:480i 34:480p 35:720p 36:1080i 37:1080p
RGB 50Hz 38:576i 39:576p 40:720p 41:1080i 42:1080p
VESA 11:WXGA 12:SXGA 13:WUXGA
```

Since you said you are using standard TV (not HDTV), it's likely you need 480i, so you need to use 1 or 33.

You must add 128 to the number to make it fullscreen, so that would be 129 or 161.

Press ```
Ctrl+Alt+F1
``` to switch to the terminal.

Type the following to gracefully kill gdm: ```
sudo service gdm stop
```

Type the following to change video resolution: ```
sudo ps3videomode -v 129
``` or ```
sudo ps3videomode -v 161
```

Type to start X11: ```
startx
```

If the graphics take up fullscreen, then you have the desired number.

Type the following to edit kboot.conf: 
```
cd /etc
sudo nano kboot.conf
```

At the penultimate line, where you see ```
linux='/boot/vmlinux initrd=/boot/initrd.img root=/dev/ps3da1 quiet '
```

Add video=ps3fb:mode:133 within the single quotation marks so you wind up with this: ```
linux='/boot/vmlinux initrd=/boot/initrd.img root=/dev/ps3da1 quiet video=ps3fb:mode:129'
```
129 can be changed as necessary.

Reboot. And hope it works.

---

