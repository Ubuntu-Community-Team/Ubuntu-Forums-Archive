---
title: "Terminal settings"
date: 2010-11-16
forum: General Help
---

### Post by Shungo73 on 2010-11-16
Hi all,

i'm not sure for using the correct channel here but i hope someone out there can answer my little questions.

1st in older version i was able to change the settings of the terminal look as the font color, background color and so on. I was also able to define a default window size of a new terminal window. But since after upgrading to to the first release this year and a complete new installation of the current release Maverick i do not find this option anymore. Is there a way how to set up the terminal default window size??

Many thanks
Shungo

---

### Post by Verbeck on 2010-11-16
you mean you cant change the values in 'edit>profile preferences' from the terminal?

---

### Post by Shungo73 on 2010-11-16
no i can change everyting, but there is no option anymore to define the window size of the terminal. In previous versions of Ubuntu i had a option to define the height and width of a new opened terminal window, but it's gone. 

Each time i will open a new window it is so small and i have to resize it, it's anoying me.....

thanks
Shungo

---

### Post by WorMzy on 2010-11-16
That feature is present again in 2.32, which is installed on Maverick. It should be present on the General tab in your profile preferences.

[[IMG]http://img717.imageshack.us/img717/899/20101116124843876x561sc.th.png[/IMG]]("http://img717.imageshack.us/img717/899/20101116124843876x561sc.png")

If you don't have the option there, then you may still be able to set it in gconf-editor under /apps/gnome-terminal/profiles/Default:
[[IMG]http://img241.imageshack.us/img241/4439/20101116125130702x573sc.th.png[/IMG]]("http://img241.imageshack.us/img241/4439/20101116125130702x573sc.png")

EDIT: If you use the gconf method, don't forget to tick the box in /apps/gnome-terminal/profiles/Default/use_custom_default_size

---

### Post by wojox on 2010-11-16
Open alacarte (Main Menu) and find Terminal.

Beside Command add

```
gnome-terminal --geometry=120x36
```

Just set you geo to your liking.

---

### Post by wojox on 2010-11-16
Okay I booted out of Fedora and into Ubuntu.

```
sudo gedit /usr/share/vte/termcap/xterm 
```

Find out following and change the two numbers:

```
:co#80:it#8:li#24\
```

change 80 and 24 to the number as you want (here 80 is the width,24 is the height)

---

### Post by Shungo73 on 2010-11-16
hi WorMzy

that rocks. Many thanks for your great job!!!!!! 

Shungo

---

### Post by WorMzy on 2010-11-16
> **wojox said:**
> ```
_gk_sudo gedit /usr/share/vte/termcap/xterm 
```

Fixed that for you. ;)

> **Shungo73 said:**
> hi WorMzy

that rocks. Many thanks for your great job!!!!!! 

Shungo

Happy to help. :)

---

### Post by wojox on 2010-11-16
> **WorMzy said:**
> Fixed that for you. ;)

I get so confused between the two distro's. :)

---

### Post by WorMzy on 2010-11-16
You shouldn't use sudo for graphical applications on Fedora either. :p

Not sure about su, but it's probably best to use gksu, if you have it.

---

