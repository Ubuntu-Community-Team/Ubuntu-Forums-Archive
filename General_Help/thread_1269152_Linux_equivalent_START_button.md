---
title: "Linux equivalent START button?"
date: 2009-09-17
forum: General Help
---

### Post by jvanbonn on 2009-09-17
I deleted the "START" button from my desktop.  Does anyone know how to get it back?  It's the button that had links to system menus and applications.

Thanks

---

### Post by llamabr on 2009-09-17
You mean you deleted the panel at the top of the screen?

---

### Post by etnlIcarus on 2009-09-17
- Right-click an empty spot on the panel.

- Choose, "Add New Items".

- In the window that pops up,  scroll down to the bottom.

- Drag & drop the, "Xfce Menu", onto your panel.

---

### Post by jvanbonn on 2009-09-17
> **etnlIcarus said:**
> - Right-click an empty spot on the panel.

- Choose, "Add New Items".

- In the window that pops up,  scroll down to the bottom.

- Drag & drop the, "Xfce Menu", onto your panel.

I think I actually deleted the Xfce Menu, because it does not even appear in the window that pops up.

Do I need do a sudo apt-get *something* install?

---

### Post by etnlIcarus on 2009-09-17
> **jvanbonn said:**
> I think I actually deleted the Xfce Menu, because it does not even appear in the window that pops up.

Do I need do a sudo apt-get *something* install?

What are the last 5 items that appear in that list of panel plugins?

---

### Post by jvanbonn on 2009-09-17
User switching
Verve Command Line
Weather Update
Window List
Workspace Switcher

---

### Post by etnlIcarus on 2009-09-17
Just do a:

```
sudo aptitude reinstall xubuntu-desktop
```

to make sure you haven't accidentially uninstalled something you shouldn't have.

---

### Post by jvanbonn on 2009-09-17
How can I start the command line interface?

I have no destop icons or menus.

---

### Post by savagenator on 2009-09-17
if Alt+f2 and typing terminal doesn't work, press ctrl+alt+f1 and login.

---

### Post by zeroseven0183 on 2009-09-17
press Alt + F2 and type **xfce4-terminal**

---

### Post by jvanbonn on 2009-09-17
Very cool... Thanks.

Here is the output I get:
computer:~$ sudo aptitude reinstall xubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done[B]
xubuntu-desktop is not currently installed, so it will not be reinstalled.
xubuntu-desktop is not currently installed, so it will not be reinstalled.[/B]
The following packages will be REMOVED:
  exiv2{u} kde-icons-oxygen{u} kdebase-runtime-data{u} 
  kdebase-runtime-data-common{u} kdelibs5-data{u} libclucene0ldbl{u} 
  libexiv2-5{u} libgif4{u} libmodplug0c2{u} libphonon4{u} libpq5{u} 
  libpulse0{u} libqt4-dbus{u} libqt4-designer{u} libqt4-network{u} 
  libqt4-opengl{u} libqt4-qt3support{u} libqt4-script{u} libqt4-sql{u} 
  libqt4-svg{u} libqt4-xml{u} libqtcore4{u} libqtgui4{u} libraptor1{u} 
  librasqal1{u} libstreamanalyzer0{u} libstreams0{u} libxcb-shape0{u} 
  libxcb-shm0{u} libxcb-xv0{u} libxfce4menu-0.1-0{u} libxine1{u} 
  libxine1-bin{u} libxine1-console{u} libxine1-misc-plugins{u} 
  libxine1-x{u} mysql-common{u} oss-compat{u} phonon-backend-gstreamer{u} 
  qt4-qtconfig{u} raptor-utils{u} 
0 packages upgraded, 0 newly installed, 41 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 107MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 130655 files and directories currently installed.)
Removing exiv2 ...
Removing kde-icons-oxygen ...
Removing kdebase-runtime-data ...
Removing kdebase-runtime-data-common ...
Removing kdelibs5-data ...
Removing libstreamanalyzer0 ...
Removing libclucene0ldbl ...
Removing libexiv2-5 ...
Removing libgif4 ...
Removing libxine1 ...
Removing libxine1-misc-plugins ...
Removing libmodplug0c2 ...
Removing phonon-backend-gstreamer ...
Removing libphonon4 ...
Removing libpq5 ...
Removing libpulse0 ...
Removing qt4-qtconfig ...
Removing libqt4-qt3support ...
Removing libqt4-designer ...
Removing libqt4-script ...
Removing libqt4-dbus ...
Removing libqt4-network ...
Removing libqt4-opengl ...
Removing libqt4-sql ...
Removing libqt4-svg ...
Removing libqt4-xml ...
Removing libqtgui4 ...
Removing libqtcore4 ...
Removing raptor-utils ...
Removing librasqal1 ...
Removing libraptor1 ...
Removing libstreams0 ...
Removing libxine1-x ...
Removing libxcb-shape0 ...
Removing libxcb-shm0 ...
Removing libxcb-xv0 ...
Removing libxfce4menu-0.1-0 ...
Removing libxine1-console ...
Removing libxine1-bin ...
Removing mysql-common ...
Removing oss-compat ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

Current status: 2 updates [-1].
computer:~$ 

So, does this mean it did not reinstall?
Do I need to reboot?

---

### Post by etnlIcarus on 2009-09-17
What the hell.

Try:

```
sudo aptitude install xfce4
```

---

### Post by jvanbonn on 2009-09-17
Will I need to reboot?

---

### Post by etnlIcarus on 2009-09-18
Probably easier than restarting GDM/X so yeah.

---

### Post by jvanbonn on 2009-09-18
Well, I have my desktop icons back, but still no Applications button or Places button in the upper left.

Any thoughts how to reload them?

[IMG]http://xubuntu.org/sites/default/files/xubuntu-jaunty.png[/IMG]

OK, I got the Xfce menu back.  How about Places?

---

### Post by etnlIcarus on 2009-09-18
Try my original intructions again.

---

### Post by jvanbonn on 2009-09-18
> **etnlIcarus said:**
> Try my original intructions again.

Thanks!

I got the Xfce menu up, but still not Places button.

Any suggestions?  Maybe create a new button and start Thunar?

Thanks again!

---

### Post by etnlIcarus on 2009-09-18
It should be installed but just to be sure:
```
sudo aptitude install xfce4-places-plugin
```.

Then add it back to the panel, like you did for the apps menu.

Edit: Actually, now would be a good time to run: ```
sudo aptitude install xubuntu-desktop
```

---

### Post by etnlIcarus on 2009-09-18
You also want to be a bit more careful in future. It looks like you accidentally uninstalled half of Xfce. When you uninstall something and aptitude, Add/Remove or Synaptic tell you additional packages have to be removed, pay close attention to what packages it's asking for permission to remove. If it's asking to remove any more than 5-10 packages or it looks like it's going to remove something important, err on the side of caution.

---

### Post by jvanbonn on 2009-09-18
Thank you for your assistance.

Very wise words to follow.  I guess I'll count that lesson as newbie move number 982. :)

Hopefully, soon, I'll start to get a grip on Linux.

Again Thanks for your help!

---

### Post by etnlIcarus on 2009-09-18
Not wise at all. This is just a really common mistake people make. I even made it, myself, about 3 or 4 years ago (whoever's idea it was to make evolution a hard dependency of half of Gnome needs an ****-whooping :P).

---

