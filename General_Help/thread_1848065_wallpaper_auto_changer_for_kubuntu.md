---
title: "wallpaper auto changer for kubuntu"
date: 2011-09-21
forum: General Help
---

### Post by elliotn on 2011-09-21
I am looking for a app that I can use to change wallpaper at a certain time like in win7

---

### Post by elliotn on 2011-09-22
anyone

---

### Post by varunendra on 2011-09-22
I personally use Desktop Drapes and like it. But you may get more suggestions to try here: [http://ubuntuforums.org/showthread.php?t=1848236](http://ubuntuforums.org/showthread.php?t=1848236)

**_PS_:** Drapes is simple and effective. However, there is a common issue with its 'Run at Startup' function. It is there as an option in Preferences > General tab, but it often (perhaps never) does not work by default. Solution is this:

[LIST]
[*]Open Preferences > General tab and check the option to "Start Desktop Drapes at Start"
[/LIST]

[LIST]
[*]Open its startup configuration file **drapes.desktop**: ```
gedit ~/.config/autostart/drapes/drapes.desktop
```
[/LIST]

[LIST]
[*]Add this line at the bottom (or top - doesn't matter): ```
Type=Application
``` Save, close and reboot to see if it worked (it always works for me!)
[/LIST]


**_EDIT_:**
Just found it doesn't even run on Natty by default. Here's a bug report with solution (posts #2,3 for 64 bit & 32 bit resp.):
[https://bugs.launchpad.net/ubuntu/+source/drapes/+bug/756687](https://bugs.launchpad.net/ubuntu/+source/drapes/+bug/756687)
Also, the address of configuration file is **~/.config/autostart/drapes.desktop** in Natty.

---

### Post by sumski on 2011-09-23
You don't need aditional applications, just select background image as presentation

---

### Post by varunendra on 2011-09-23
> **sumski said:**
> You don't need aditional applications, just select background image as presentation
You don't get that amazing amount of options and control there. :)

Just try one of them and you'll get the appealing difference.

---

### Post by ankspo71 on 2011-09-25
Hi,
The KDE4 desktop in Kubuntu has a wallpaper changer built into the desktop already. Right click on your desktop and choose Desktop Settings (or Folder View Settings etc, depending on the desktop layout you are using), then when the settings window opens, go to the view category, then look for "Wallpaper:" and choose "Slideshow" in the dropdown menu.

When you are done setting that up, you will find a right click menu entry for "Next Wallpaper Image" on your desktop.

The KDE wallpaper changer can have independent settings for each of your different virtual desktops too. To see what I mean you would have to right click on your panel's pager, then choose Pager Settings, then click on Virtual Desktops, then enable the option called "Different Widgets For Each Desktop". Then you can click on each of your virtual desktops and configure your wallpaper settings for each one. 

Hope this helps.

---

