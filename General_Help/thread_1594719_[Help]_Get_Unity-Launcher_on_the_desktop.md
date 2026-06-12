---
title: "[Help] Get Unity-Launcher on the desktop"
date: 2010-10-12
forum: General Help
---

### Post by fimfree on 2010-10-12
Is there any way to get the unity-launcher (that thing that isn't a dock :D) which sit in the left of the screen in the Ubuntu-netbook 10.10; to get it in the desktop version instead of using of AWN or Docky.

I googled it & I searched in the software center but found nothing helpful.

---

### Post by ankspo71 on 2010-10-12
Hi,
My advice will depend on if you are already using Ubuntu 10.10, or are you wanting to try out Unity in another version such as 10.04

If you are using Ubuntu 10.10, you could simply install 'ubuntu-netbook' which is what I have done. For netbook to work it requires graphics drivers that support 3D though. If you install ubuntu-netbook, you can log out and have the choice to start Ubuntu Netbook or Ubuntu Desktop.

If you are using 10.04, you can install the ubuntu-netbook (ubuntu-netbook-unity-default-settings) by adding a PPA repository. 
[http://www.ubuntugeek.com/new-unity-release-ready-for-testing-in-ubuntu-10-1010-04.html](http://www.ubuntugeek.com/new-unity-release-ready-for-testing-in-ubuntu-10-1010-04.html)

As far as running Unity in the Ubuntu Desktop, 'I think' all I know is that it requires Mutter as the window manager (command: 'mutter --replace' ?), not metacity, plus running whatever binary that is or starts unity. This is something that I haven't tried to do yet though.

Edit: I checked to see if running Unity in Ubuntu Desktop is possible, and it looks like it is. I used the commands:
```
mutter --replace 
unity
```

Hope this helps.

PS. Just to let you know ahead of time... As of now, Unity is far less configurable than most docks are. Even the GTK2 themes for the gnome desktop can't be changed while using the Ubuntu Netbook (they don't apply)... unless I simply haven't figured out how to do that yet.

---

### Post by fimfree on 2010-10-12
Thks for your quick reply, but I have already tried Ubuntu unity & I didn't liked it. But what I want is just the unity-launcher were applications shorcuts exists (which sits on the left).

---

### Post by kerry_s on 2010-10-12
> **fimfree said:**
> Thks for your quick reply, but I have already tried Ubuntu unity & I didn't liked it. But what I want is just the unity-launcher were applications shorcuts exists (which sits on the left).

dockbarx applet, does the same thing. make sure you install the extra themes so get the unity themes.
[https://launchpad.net/~dockbar-main/+archive/ppa](https://launchpad.net/~dockbar-main/+archive/ppa)

i use mine dock style.

---

### Post by rinaldow on 2010-10-13
is there any way possible to force unity-launcher to autohide?

or even better: make "workspaces" work in the 2d netbook launcher?

coz unity is taking too much display-space from me, and i preferred the netbook launcher of 10.04 to unity... so workspaces is the feature i appreciate most....

---

### Post by omskates on 2010-10-15
> **rinaldow said:**
> is there any way possible to force unity-launcher to autohide?

or even better: make "workspaces" work in the 2d netbook launcher?

coz unity is taking too much display-space from me, and i preferred the netbook launcher of 10.04 to unity... so workspaces is the feature i appreciate most....

I just F11 full-screen my apps when working netbooks any way.  Especially browsers, word processing and photo management - F11 and F11 to escape it.  Otherwise I find many of the accessory apps really don't have to use that extra 1/2 inch to be productive.  Maybe its just me but an auto hide dock on 10" screen is always popping out accidentally when working apps in full screen....gets annoying.

Cheers

---

### Post by mikhaell on 2010-10-16
@kerry S

Your setup is a great idea and I am using dockbarx as well. I have a small graphic issue though- when i add a vertical panel, i see a lot of horizontal lines. as if there are a lot of horizontal panels stacked on each other. Do you know how to fix this?

---

