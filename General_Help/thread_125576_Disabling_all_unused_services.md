---
title: "Disabling all unused services"
date: 2006-02-04
forum: General Help
---

### Post by laxstar5 on 2006-02-04
I have a computer (64 RAM only , 933 Mhz PIII though) that's very old. Could u plz tell me which services i should disable that are unneeded on my computer. i have no CD writer or DVD drive so is there anyway i could disable support for these devices , and will it save any memory? 

PS: WinXP runs fine on my computer. then why does GNOME need such a fast computer (i've heard even 256 MB is too low)

---

### Post by twigboy on 2006-02-04
[http://www.ubuntuforums.org/showthread.php?t=89491&highlight=Boot-Up+Manager](http://www.ubuntuforums.org/showthread.php?t=89491&highlight=Boot-Up+Manager)

[https://wiki.ubuntu.com/InitScriptHumanDescriptions?highlight=%28boot-up%29%7C%28mana%29](https://wiki.ubuntu.com/InitScriptHumanDescriptions?highlight=%28boot-up%29%7C%28mana%29)

Im pretty amazed that you actually have xp running with 64megs of ram when its minimum requirements are 128megs.    I know its supported but wow.  Also xp needs a just as fast computer to run all its features.

---

### Post by simon_is_learning on 2006-02-04
first of all i don't know how much effect the CD-writer and DVD has on the memory. Maybee you'll gain som bootup time.

Something that really eats memory is the Xserver. 
To spare some memory use fluxbox or XFCE.

What i have done when installing on low-ram systems:
 - when booting from CD to install, write server.
          (now only the base system is installed)
 - when done. uncomment sources.list in /etc/apt/
               ---------easy and fast way-------------
 - sudo apt-get install xubuntu-desktop
               -----long way but with total control-----
 - sudo apt-get install x-window-system-core 
 - sudo apt-get install XFCE4
 - sudo apt-get install xterminal

after that you can type startx and it will hopefully start. 
next step is to manually install all your applications, most things is in the repositories. 

My choice for file manager is Thunar, Firefox for web-browser and GAIM for chatting. But you are free to do what ever you want...

good luck

---

### Post by handy on 2006-02-04
[QUOTE=laxstar5]I have a computer (64 RAM only , 933 Mhz PIII though) that's very old. Could u plz tell me which services i should disable that are unneeded on my computer. i have no CD writer or DVD drive so is there anyway i could disable support for these devices , and will it save any memory? 

PS: WinXP runs fine on my computer. then why does GNOME need such a fast computer (i've heard even 256 MB is too low)[/QUOTE]

xp on 64Mb ram runs fine!!:confused: 

I'm astounded!

---

