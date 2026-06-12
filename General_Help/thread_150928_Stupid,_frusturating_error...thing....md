---
title: "Stupid, frusturating error...thing..."
date: 2006-03-26
forum: General Help
---

### Post by jbritz22 on 2006-03-26
Ok, so I got a new monitor. Hooked it up. I see a loading screen and everything but when it comes to the login screen, It's all black.

So I go into recovery mode, type xrandr -s 1024x768 and it says "Cant open display (null)".

Startx gets a black screen, then I hear a choonk sound and then after I press enter I hear another sound.

Please help. Can anyone reccomened me a really lightweight msn app for linux also? (IF I can get the monitor working, :()

---

### Post by aysiu on 2006-03-27
When you get that black screen, press Control-Alt-F1 and log in. Then type ```
sudo dpkg-reconfigure xserver-xorg
``` Answer the questions as best you can. If you don't know the answer, go with the default. Once you're done, type ```
exit
``` Press Control-Alt-F7 and then press Control-Alt-Backspace.

---

### Post by morpheus2485 on 2006-03-27
theory number two is search google for the moddle number and find the thread where someone else already delt with the problem and was kind enough to post thier xorg.conf file, and just copy/paste the appropriate sections.

---

### Post by akiro.yamamoto on 2006-03-27
[quote=aysiu]When you get that black screen, press Control-Alt-F1 and log in. Then type ```
sudo dpkg-reconfigure xserver-xorg
``` Answer the questions as best you can. If you don't know the answer, go with the default. Once you're done, type ```
exit
``` Press Control-Alt-F7 and then press Control-Alt-Backspace.[/quote]

You can also use the following for a default config....
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by jbritz22 on 2006-03-27
Thanks, it worked!

Anyone know of a lightweight msn client?

---

