---
title: "Networking help..."
date: 2006-02-05
forum: General Help
---

### Post by Surferdude on 2006-02-05
Hi,

I recently downloaded Breezy and installed it on my computer. I have two problems though:

1. The screen resolution doesnt go beyond 640x480. I think this has somthing to do with my monitor (Envision EN-5100e). Is there any way to force it to go to 1024x768?

2. I have a Belkin USB Wi-Fi adapter (F5D6050) and am trying to use it to connect to my network with Ubuntu.  It appears that Ubuntu can pick up the devices MAC address, but nothing more. Is there an easy way to make this device compatable? If not, are there any other Wi-Fi cards that would be compatable with little or no configuration?

Thanks!
Surferdude

---

### Post by dcstar on 2006-02-05
[QUOTE=Surferdude]Hi,

I recently downloaded Breezy and installed it on my computer. I have two problems though:

1. The screen resolution doesnt go beyond 640x480. I think this has somthing to do with my monitor (Envision EN-5100e). Is there any way to force it to go to 1024x768?
......[/QUOTE]
In a terminal:

sudo dpkg-reconfigure xserver-xorg

---

### Post by Surferdude on 2006-02-05
just tried that, does nothinng when it finishes.

---

### Post by andrewsawyer on 2006-02-11
Try ```
sudo gedit /etc/X11/xorg.conf
``` and manually type in the display resolution you want into the Section "Screen" part.  You need to edit the SubSection "Display" to look something like this:
```
SubSection "Display"
    Depth    24
    Modes   "1024x768"
EndSubSection
```
This should do the trick.  You are basically replacing the 640x480 with 1024x768 directly in the config file.

Andy

---

