---
title: "Tweaking xubuntu-desktop"
date: 2011-03-01
forum: General Help
---

### Post by jim_deadlock on 2011-03-01
I installed xubuntu-desktop and it has speeded up my computer quite noticeably (compared to Gnome which I was using before), now how do I:

a) Change the default file manager from nautilus to the Thunar file manager?

b) Fiddle with window settings? I would like to move the buttons over to the left and maybe look at some other themes if there are any.

---

### Post by searchfgold6789 on 2011-03-01
I am glad to hear you are enjoying Xubuntu.
More themes can be found in the Xfce 4 Settings manager, which should come installed with xubuntu-desktop.
I'm not sure if xubuntu-desktop actually comes with xfce-panel - the default panel for xfce. If it does, items on the panel can be easily moved: To separate items on the left side of the panel from the right side, make sure you add "expanding space" to the panel using the Add New Items tool. You can move things around by right clicking the item, selecting Move, and clicking where you want the item to go.
And I would shiver at the thought of xubuntu-desktop not automatically setting Thunar as the default. Maybe you still have nautilus installed, but not default.
After purging nautilus, I'm guessing you will have to remove and then replace the Places Menu using Add New Items on the panel.
Good luck with Xubuntu.

---

### Post by 3Miro on 2011-03-01
> **jim_deadlock said:**
> I installed xubuntu-desktop and it has speeded up my computer quite noticeably (compared to Gnome which I was using before), now how do I:

a) Change the default file manager from nautilus to the Thunar file manager?

b) Fiddle with window settings? I would like to move the buttons over to the left and maybe look at some other themes if there are any.

a) This is not very easy:

[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

b) One of the reasons why XFCE (Xubuntu's environment) is so fast is because of the lack of some features. To change the button placement, you have to go to Applications -> Settings -> Settings Manager -> Windows Manager, however, where you can change the layout, however, not all themes support "flexible" button layout.

XFCE is GTK based and uses GTK themes (same as gnome) for everything inside the windows, however, the windows decorations (buttons and all) are handled by a different Windows Manager (xfwm) and are hence incompatible with Gnome themes. You have to look for specific xfwm4 themes:

[http://xfce-look.org/](http://xfce-look.org/)

Note that some xfce themes should be available via the software center.

---

### Post by jim_deadlock on 2011-03-01
Thank you both, that default file manager script worked a treat and I'll have fun with the XFCE eye candy page later. However, I can't seem to find the XFCE windows manager anywhere on my menus, what's the command for it?

---

### Post by 3Miro on 2011-03-01
> **jim_deadlock said:**
> Thank you both, that default file manager script worked a treat and I'll have fun with the XFCE eye candy page later. However, I can't seem to find the XFCE windows manager anywhere on my menus, what's the command for it?

The windows manager should be running if you are using XFCE. If you want to edit the settings for the window manager, then you need to go to:

Start Menu -> Settings -> Settings Manager

To make sure the window manager is working, use the command:
```
ps -e | grep xfwm4
```
or look for xfwm4 in any Task Manager.

---

### Post by jim_deadlock on 2011-03-01
xfwm4 is running, but I don't have a "start menu". On my top panel I have Applications, Places, System - I would expect the settings to be on the System menu somewhere but it isn't, which is why I'm asking if there's a command I can run instead...?

Edit: I probably still have my original Gnome panels(?)

---

### Post by 3Miro on 2011-03-01
> **jim_deadlock said:**
> xfwm4 is running, but I don't have a "start menu". On my top panel I have Applications, Places, System - I would expect the settings to be on the System menu somewhere but it isn't, which is why I'm asking if there's a command I can run instead...?

Edit: I probably still have my original Gnome panels(?)

How did you install XFCE?

Here is what the default XFCE looks like, you get this if you install "xfce4" package:

[http://www.xfce.org/about/screenshots](http://www.xfce.org/about/screenshots)

If you installed xubuntu-desktop, then you should get this:

[http://www.xubuntu.org/](http://www.xubuntu.org/)

The "Start Menu" is either the X+mouse icon at the lower right or the Applications in the top left.

You can look at
```
ps -e | grep gnome-panel
```
to see if you are running Gnome panel indeed.

---

### Post by jim_deadlock on 2011-03-01
Yes I'm running gnome-panel but there's no windows settings on the Applications menu.

I installed XFCE like this:

```
sudo apt-get install xubuntu-desktop
```

... then I switched to the XFCE windows manager using my compiz icon (fusion-icon)

---

### Post by jim_deadlock on 2011-03-01
Never mind, I found it with the App finder so I'm all sorted, thanks for your help!

---

### Post by aeiah on 2011-03-01
> **jim_deadlock said:**
> Yes I'm running gnome-panel but there's no windows settings on the Applications menu.

I installed XFCE like this:

```
sudo apt-get install xubuntu-desktop
```

... then I switched to the XFCE windows manager using my compiz icon (fusion-icon)

you should log out and select the xfce desktop environment from there. this'll ensure everything xfce is loaded, and all the gnome stuff isnt. you can also set it as the default for future use (or not if you prefer). it seems you've switched from gnome to xfce but things are still hanging around because you used compiz switcher to do it

---

