---
title: "black screen after installation"
date: 2006-03-17
forum: General Help
---

### Post by fouadk on 2006-03-17
hey, i just installed ubuntu successfully, and after it loaded all modules with success a black screen appear and nothing happen:( , its strange coz i also installed ubuntu on my other computer and it worked fine, my current pc which ubuntu didnt work on is an AMD sempron...
i searched other threads and i couldnt find anything...
i cant use the ctrl+alt+F1 or other combination...please help

---

### Post by invalid on 2006-03-17
Try using the following boot options:
```
acpi=off noapic nolapic
```

---

### Post by fouadk on 2006-03-17
thanks for the fast reply but man i am a newbie and i dunno how and where to make these changes so please ellaborate as much as you can

---

### Post by wargames on 2006-03-18
[QUOTE=fouadk]hey, i just installed ubuntu successfully, and after it loaded all modules with success a black screen appear and nothing happen:( , its strange coz i also installed ubuntu on my other computer and it worked fine, my current pc which ubuntu didnt work on is an AMD sempron...
i searched other threads and i couldnt find anything...
i cant use the ctrl+alt+F1 or other combination...please help[/QUOTE]

Sounds like your install isn't detecting and using the right video driver in the xorg.conf file. You need to get to the command line, try F1 or F2 and then edit the /etc/X11/xorg.conf file and find the driver section and change that to vesa and then save and reboot. I use the vi command to edit that file. An example would be to change the driver from ati to vesa in the xorg.conf file. This is just my guess, because that happened on my AMD system and after I changed it to vesa and rebooted, then Gnome login screen would work. After that I then installed the right fglrx graphics drivers for my ATI card. Hope it helps.

---

### Post by akiro.yamamoto on 2006-03-18
You can use this command to force the system to re-detect and re-configure your
X system with (relatively ) safe defaults.
```

sudo dpkg-reconfigure -phigh xserver-xorg 

```

---

### Post by invalid on 2006-03-18
[QUOTE=fouadk]thanks for the fast reply but man i am a newbie and i dunno how and where to make these changes so please ellaborate as much as you can[/QUOTE]
You append this text to the end of the boot options, while you are in grub. Select the default kernel to boot (which ever is highlighted), and tack those 3 options on at the end.

---

