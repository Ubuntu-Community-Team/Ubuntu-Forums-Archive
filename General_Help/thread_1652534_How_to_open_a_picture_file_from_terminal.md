---
title: "How to open a picture file from terminal?"
date: 2010-12-25
forum: General Help
---

### Post by Sxynerd on 2010-12-25
Hello, I am trying to find a way to open a picture file from the terminal.  I have a picture located at  'home/michael/pictures/backgrounds/BSOD.gif'

I want to use GNOME image viewer and I want it to open in full screen mode.  


Is this possible with a single terminal command?

Thanks,
Wolvee

Ubuntu 10.10 Desktop

---

### Post by Verbeck on 2010-12-25
it would be like
```

eog -f /home/michael/pictures/backgrounds/BSOD.gif

```

---

### Post by Sxynerd on 2010-12-25
That's great.  It opens file in fullscreen mode just like I wanted.  :0)  

I'll post up a video as to why I wanted this soon.  It is a little on the silly side but fun for a new user like me.

Merry Christmas & Season

---

### Post by Verbeck on 2010-12-25
> **Sxynerd said:**
> 
I'll post up a video as to why I wanted this soon.  It is a little on the silly side but fun for a new user like me.

> **Sxynerd said:**
> ~**BSOD**.gif~
i could guess ;)

season's greetings to you too

---

### Post by karthick87 on 2010-12-25
```
xdg-open /path/to/the/picture
```
for example
```
xdg-open /home/username/1.png
```

---

### Post by matt_symes on 2010-12-25
Hi

From the terminal you can also use

```
gnome-open <filename>
```

and it will open the file with the application that is associated with that file in gnome.

i.e

```
gnome-open ~/Pictures/picture.gif
```

or 

```
gnome-open ~/article.pdf
```

Kind regards

---

### Post by Sxynerd on 2010-12-30
Eh..  I can't configure my "windows" key on my keyboard. :0(  So I guess I am SOL.

Anyone know how to get Ubuntu to recognize that key?

---

### Post by karthick87 on 2010-12-30
Do you want to bind the key??

---

### Post by Rasa1111 on 2010-12-30
> **Sxynerd said:**
> Eh..  I can't configure my "windows" key on my keyboard. :0(  So I guess I am SOL.

Anyone know how to get Ubuntu to recognize that key?

[http://www.howtogeek.com/howto/27038/use-the-windows-key-for-the-start-menu-in-ubuntu-linux-10.04/](http://www.howtogeek.com/howto/27038/use-the-windows-key-for-the-start-menu-in-ubuntu-linux-10.04/)

---

### Post by Sxynerd on 2010-12-30
> **Rasa1111 said:**
> [http://www.howtogeek.com/howto/27038/use-the-windows-key-for-the-start-menu-in-ubuntu-linux-10.04/](http://www.howtogeek.com/howto/27038/use-the-windows-key-for-the-start-menu-in-ubuntu-linux-10.04/)

Thank you but I have ran through that tutorial several times.  IT works to bind that key but not to use the command I chose.  (^See above) :confused:

---

### Post by Sxynerd on 2010-12-30
Using this: "Alt F2" 

How can I get this as the fuction?
eog -f /home/michael/Pictures/Backgrounds/BSOD.giff

The "Think Geek" uses "gconftool-2 --set /apps/metacity/global_keybindings/panel_main_menu --type string "Super_L" to assign the "main Menu".

---

### Post by Rasa1111 on 2010-12-30
> **Sxynerd said:**
> Thank you but I have ran through that tutorial several times.  IT works to bind that key but not to use the command I chose.  (^See above) :confused:

ahh.
doh!
my apologies. <3

---

### Post by Sxynerd on 2011-01-01
New years day bump for the second half of the question: post #11

Thanks everyone.  Happy New Year.

---

