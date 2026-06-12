---
title: "UNR crushed"
date: 2009-10-02
forum: General Help
---

### Post by gos1 on 2009-10-02
I am getting an empty desktop and even alt + f2 doesn't work I cannot do anything .

---

### Post by jward3010 on 2009-10-02
I think I've seen this before, is the background area completely black. 

Try this (if possible). Go to Applications menu > the top option > Terminal - now type nautilus and hit enter, does anything appear?

---

### Post by gos1 on 2009-10-03
I dont have an applications menu I cannot launch the terminal .

---

### Post by Shibblet on 2009-10-03
hit ctrl+alt+f2

Login, and password.

---

### Post by gos1 on 2009-10-03
Nautilus cannot be launched error message : 
  
  Could not parse arguments: Could not open display:

   It happened after I fallow the Nvidia installaiton tutorial on ubuntuguide.org

---

### Post by Primefalcon on 2009-10-03
sounds like your graphics driver could be, check system=>administration=>hardware drivers to see if you have any propierary drivers you can use, also what exact card are you using?

---

### Post by gos1 on 2009-10-03
I don't know the exact car but trying to install UNR on a msi u120 netbook. I cannot do anythin in the gnome ? So the solution should be in the terminal without the display manager. 

 Is there a place where I can find chipset of laptop and netbooks ? I tried to install Nvidia because my other MSI laptop was Nvidia ...

---

### Post by Primefalcon on 2009-10-03
darn good point tried sudo dpkg-reconfigure xserver-xorg?

---

### Post by jward3010 on 2009-10-03
Before you try above, when you're at the terminal (Ctrl+Alt+F2) type:
```
sudo gdm
```
This will attempt to start the desktop.

---

### Post by beastrace91 on 2009-10-03
> **gos1 said:**
> I tried to install Nvidia because my other MSI laptop was Nvidia ...

By this do you mean you installed nVidia gfx drivers on your netbook? If so this is your issue. That netbook (and most other netbooks) does not have an nVidia graphics card - this is why you are getting a blank screen, because your drivers are trying to work on a card that does not exist.

If this is indeed what you did to resolve the issue drop down to a terminal log in (ctrl+atl+f1) and enter the following commands: ```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo shutdown -r now
```

~Jeff

---

### Post by gos1 on 2009-10-04
thank you very much all my screen came back but now. 
 
   I have the menu but did not have the panel. I added gnome-panel command to my startup applications. Now I have the panel and the menu everything seems fine when I open the computer but when I open a window like this one . It does not appear in my panel and the size of the panel is about 1/2 of my whole screen. 
 
   Do i have to start another application too to have the old features. All the windows were in the top panel with the active one was covering the whole panel 
 
   Thanks again for your help

---

### Post by jward3010 on 2009-10-04
Some part of me says "reinstall ubuntu-desktop" but maybe it simpler than that. If you right click on that insanely sized panel, Properties you should be able to reduce it's "height". I think your panels are missing some things as well as if there set up afresh again.

---

### Post by gos1 on 2009-10-04
only one problem left when I boot the computer there are problems in the UNR menu. When I open a window it does not fill the screen only a small window on the left top corner of the screen 
 
 When I run desktop-switcher and switch to classic and switch back to UNR desktop everything seems fine as in the first installation. 
 
  What should I do . 
 
  PS : I reinstalled the ubuntu-desktop.

---

### Post by jward3010 on 2009-10-05
Any chance you can post some pictures. Hit the PrntScrn button on your keyboard to take a snapshot of what you see and post them here. Also how did you get on with reinstalling ubuntu-desktop?

---

