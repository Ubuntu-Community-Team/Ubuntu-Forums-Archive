---
title: "Natty: Where are my minimised folders/programs?"
date: 2011-05-15
forum: General Help
---

### Post by ortaa23 on 2011-05-15
Just gone over to Ubuntu. One thing I really can't work out is how to access minimised folders and programmes. The first few times I used Natty I'm sure that they were on the bottom bar, but now this is no longer the case. I am using an Asus Eee netbook. Can anyone advise? Thanks in advance.

---

### Post by uRock on 2011-05-15
If you click the unity icon for the program/folder, then it should reappear.

---

### Post by teachop on 2011-05-15
You should see them on the Launcher.  I have pretty much stopped minimizing things, and use the key combination windows-W to find what I need, which triggers compiz scale.

---

### Post by ortaa23 on 2011-05-15
uRock: Would you be kind enough to instruct me as to where the unity icon is to be found? Googling does not seem to provide an answer..

Teachop: Thanks for the shortcut, I suppose that will work if nothing else does.

---

### Post by garvinrick4 on 2011-05-15
anything that you have open will be in the icons on the left (launcher) notice  the white mark
next to open icon and if two white marks two open.
If you want a program to open tap on Windows key and then type in app and click on.
Will find as your type usually 2 or 3 letters and will open.
Alt/F2 still is a run command.
Windows key and A will open Applications available. (check out all applications in upper right also.)
Windows S shows all desktops
Windows W shows all open. (Click on and will be in front.)
Check out Windows D and then Windows D again.
If you want a little more access use Docky and intellihide.

---

### Post by ortaa23 on 2011-05-15
Well for some reason Launcher doesn't launch for me when I take my pointer to the left edge of the screen..

---

### Post by n1ght5t4lk3r on 2011-05-15
> **garvinrick4 said:**
> 
If you want a little more access use Docky and intellihide.


glx-dock (cairo with opengl) is pretty nice too, as well as funtional.

---

### Post by ortaa23 on 2011-05-15
Hi,

Some of those work. Win + A doesn't seem to do anything. I just don't understand why I can't access Launcher. And why things I minimise just disappear into nowhere. Is that how Ubuntu works as standard? Seems very strange...

---

### Post by garvinrick4 on 2011-05-15
Run 
```
unity --reset
```
in a terminal

If does not work run:
```
/usr/lib/nux/unity_support_test -p 
```
above to see if unity capable machine.

---

### Post by uRock on 2011-05-15
> **ortaa23 said:**
> uRock: Would you be kind enough to instruct me as to where the unity icon is to be found? Googling does not seem to provide an answer..

I took a screenshot. Every open application has an icon in the Unity launcher. In the screenshot you can tell which ones are open by the little white mark on the left side of the launcher. Thunderbird, Update Manager and Pidgin are minimized in the screenshot. All you have to do is click on the launcher and the application's window will be restored.

---

### Post by garvinrick4 on 2011-05-15
If that does not work try:
sudo apt-get install compizconfig-settings-manager

```
rick@rick-HP:~$ aptitude show compizconfig-settings-manager
Package: compizconfig-settings-manager   
State: installed
Automatically installed: no
Version: 0.9.4-0ubuntu2
Priority: extra
Section: universe/x11
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 5,894 k
Depends: python, python-central (>= 0.6.11), python-compizconfig (>= 0.9.0),
         python-gtk2
Description: Compiz configuration settings manager
 The OpenCompositing Project brings 3D desktop visual effects that improve
 usability of the X Window System and provide increased productivity. 
 
 This package contains the compizconfig settings manager.

```

## open after install and make sure Ubuntu unity plugin is checked.
run
```
ccsm
```
to open

---

### Post by ortaa23 on 2011-05-15
Sorry guys, I'm using Ubuntu Classic, not Unity, the difference between which I've only just worked out. 

However, I created a new user and on that account things are working as they should, i.e. I can see minimised windows. So how do I reset whatever went wrong? To summarise, on the bottom bar all I can see is the recycle bin icon, no red 4 screen symbol, and no minimised windows.

---

### Post by Blasphemist on 2011-05-15
> **ortaa23 said:**
> Hi,

Some of those work. Win + A doesn't seem to do anything. I just don't understand why I can't access Launcher. And why things I minimise just disappear into nowhere. Is that how Ubuntu works as standard? Seems very strange...

When you login, do you see at the bottom of the screen a session choice box that shows Ubuntu? Or do you use auto login? Do you get prompted for a login when you boot up?

You have to be logging in to, or auto logged into the "Ubuntu" session to have full unity. As long as you are, lets go to the next step. See my first screen shot. Go to System settings, CompizConfig Settings Manager. Is the Ubuntu Unity Plugin checked?

If it is checked, click on the words and not the check box to get to my second screen shot. On the hide launcher option, you can choose the never setting and the launcher will always stay on your screen. The setting I use and that is shown on my screen shot is dodge active window. The launcher shows unless I have a window maximized or I drag one to the left far enough to touch the launcher. If I do that the launcher hides. Some people prefer that the launcher only shows when they move the mouse to the left edge of the screen.

This should help unless you have not been successful in getting the unity session to run. If that is the case, let us know and we'll start troubleshooting that.

---

### Post by ortaa23 on 2011-05-15
Sorry guys, I'm using Ubuntu Classic, not Unity, the difference between which I've only just worked out. 

However, I created a new user and on that account things are working as they should, i.e. I can see minimised windows. So how do I reset whatever went wrong? To summarise, on the bottom bar all I can see is the recycle bin icon, no red 4 screen symbol, and no minimised windows.

---

### Post by jerome1232 on 2011-05-15
You should be able to right click your bottom panel and add the Window Selector I believe it's called.

---

### Post by ortaa23 on 2011-05-15
Hi,

The option does exist to add Workspace Switcher to the panel, but there's no option to deselect minimised windows showing up, so I'm still wondering what happened...

---

### Post by ortaa23 on 2011-05-15
Can anyone tell me how to fix Ubuntu Classic? Presumably the above codes only work for Unity...

---

### Post by garvinrick4 on 2011-05-15
> **ortaa23 said:**
> Hi,

The option does exist to add Workspace Switcher to the panel, but there's no option to deselect minimised windows showing up, so I'm still wondering what happened...
Do you mean the 3 buttons on upper bar are not there, to close, minimize
or do you mean right click on upper or lower panel and add to panel.

---

### Post by teachop on 2011-05-15
> **ortaa23 said:**
> Can anyone tell me how to fix Ubuntu Classic? Presumably the above codes only work for Unity...
Right click on the panel, add to panel, select Window List.  That will let you see minimized stuff.

---

### Post by jerome1232 on 2011-05-16
> **teachop said:**
> Window List

I had half of it right, do I at least get 50%?

---

### Post by BunnyDee on 2011-06-09
For some reason, the white mark on the left of the icon for Chrome (haven't tried it with anything else yet) seems to disappear when I minimize the program. However, I press Alt - Tab and it's one of the choices of the open windows there, so I can return to it that way.

---

