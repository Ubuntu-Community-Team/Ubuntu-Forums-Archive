---
title: "Libreoffice menu problems"
date: 2012-06-01
forum: General Help
---

### Post by linuxsam777 on 2012-06-01
When I use the Libreoffice suite most of the menu text just shows up as under scores. I have attached a screen shot to the post I am using Ubuntu precise pangolin and I am using the gnome desktop environment

---

### Post by linuxsam777 on 2012-06-02
Can anybody help me?

---

### Post by lonniehenry on 2012-06-02
Change the default font to something else and see if they then appear.  ask.libreoffice.org has a forum for issues.

---

### Post by vasa1 on 2012-06-02
> **lonniehenry said:**
> Change the default font to something else and see if they then appear.  ask.libreoffice.org has a forum for issues.
Here's the link: [http://ask.libreoffice.org/questions/](http://ask.libreoffice.org/questions/)
You may not need to get a new username/password. Do check it out but try to provide more information: version number of LibO, the exact DE, whether you have installed the lo-menubar or other extensions, etc.

---

### Post by linuxsam777 on 2012-06-03
I have changed with Ubuntu Tweak the default font to norasi at size 11. most menu items show up but obviously everything looks pretty ugly. by the way I am using ubuntu precise and LibreOffice 3.5.3.2 Build ID: 350m1(Build:2). Also I am using a toshiba nb-500 with a screen res of 1024x600.

---

### Post by Plodder on 2012-06-04
I think that this may be a video card problem. I have the same problem when using the NVIDIA driver but not when using the Nouveau driver.

---

### Post by Plodder on 2012-06-04
I've just installed lo-menubar from the Ubuntu Software Center. I seems to have solved 90% of my problem.

---

### Post by linuxsam777 on 2012-06-12
I tried that but it hasn't fixed my problem :/
Do you tink it has any thing to do with me using a netbook? or may be the fact that I'm using gnome 3.4 :cry: I don't like unity

---

### Post by Docaltmed on 2012-07-16
> **linuxsam777 said:**
> I tried that but it hasn't fixed my problem :/
Do you tink it has any thing to do with me using a netbook? or may be the fact that I'm using gnome 3.4 :cry: I don't like unity

It's a netbook thing, and a longstanding problem. There are several fixes out in the wild. Unfortunately, none of them have worked for me.

---

### Post by JoseCid on 2012-10-21
Hi all,

I got libreoffice working fine if I use LXDE as a  graphical environment. I did no change to fonts or system configuration,  just installed LXDE and there libreoffice works fine.

# sudo apt-get install lxde

(Log out after installing and select LXDE session from the login screen)

Just  a comment: I found LXDE very light and user friendly. I have it  installed in my girlfriend's computer, it's her first time with linux  and she loved it ;)

:guitar:

---

### Post by mideal on 2012-11-16
You can fix it - no matter which desktop - with another system default font.
I use XFCE, others had this with KDE, Gnome, Unity, LFXE.

1) Start LibreOffice (not maximized, so you can see some desktop icons.
2) Change the Linux systemwide default font in "Settings/Appearance" to another.
3) The change is immediately visible in your LibreOffice menus without restarting it.
Repeat from step 2 until you like the result. (AFAIK I have chosen DejaVu Sans, sitting in front of WinXP now).

---

