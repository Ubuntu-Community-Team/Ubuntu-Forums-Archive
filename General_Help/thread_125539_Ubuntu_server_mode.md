---
title: "Ubuntu server mode"
date: 2006-02-04
forum: General Help
---

### Post by rensu on 2006-02-04
Im using server mode in Ubuntu and dont have X. So question is this: How can i change my resolution? What are the commands for chaning it? Or is it possible?:confused:

---

### Post by bonzodog on 2006-02-04
you mean resolution in the console? 
Enable framebuffer. go to /boot/grub/menu.list and edit the current booting kernel line by adding "vga=791" after "ro quiet splash". reboot to enable framebuffer. the 791 bit actually sets the resolution to 1024x768, and gives you an appropriate font. 
 I can often be found in IRC on freenode in #ubuntuforums- this channel is useful for community chat and they will solve the odd problem for people as well.

---

### Post by Ubuntuud on 2006-02-04
You need to edit you xorg.conf file. I believe you should type something like: 
```
sudo nano /etc/apt/xorg.conf
```
but the location can be different (offcourse you can use an other editor than nano.)
Then go to the next page (type "Ctrl" + the character shown on the bottom of the screen. Scroll down until you see a lot of resolutions. change every (or just the first one) resolution to your resolution, restart and done.
I hope this helps...

---

### Post by leech on 2006-02-04
[QUOTE=Ubuntuud]You need to edit you xorg.conf file. I believe you should type something like: 
```
sudo nano /etc/apt/xorg.conf
```
but the location can be different (offcourse you can use an other editor than nano.)
Then go to the next page (type "Ctrl" + the character shown on the bottom of the screen. Scroll down until you see a lot of resolutions. change every (or just the first one) resolution to your resolution, restart and done.
I hope this helps...[/QUOTE]

Uhm, actually xorg.conf is almost (99.99% of the time) in /etc/X11.  Secondly, Bonzodog had it right, to change the console mode resolution, you need to add the vga= line in /boot/grub/menu.lst.  

Your advice is perfectly helpful though for changing resolution in X.

Leech

---

### Post by Ubuntuud on 2006-02-04
Oh, I said I hoped so...

---

