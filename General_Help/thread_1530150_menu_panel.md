---
title: "menu panel"
date: 2010-07-13
forum: General Help
---

### Post by choochoousmc on 2010-07-13
I accidentally deleted the main default menu panel at top of desktop.
Is there a way to recover it.

where in the system would I find the various icons that are located in it.
A list of the icons in each category?

Or do I need to use the installation disk and repair / reinstall?

---

### Post by fooman on 2010-07-13
is it just the menu that you lost...or the entire panel?

if just the menu,  then try this:
right-click in the top panel (in the area where the menu was)  and choose "add to panel" from the drop down menu.

scroll through the list and click once on "menu bar"....then click the add button.

hope that helps.

---

### Post by choochoousmc on 2010-07-13
> **fooman said:**
> is it just the menu that you lost...or the entire panel?

if just the menu,  then try this:
right-click in the top panel (in the area where the menu was)  and choose "add to panel" from the drop down menu.

scroll through the list and click once on "menu bar"....then click the add button.

hope that helps.


thanks but no.
I can add a new panel, but I wanted to recover the original.
I was originally just trying to delete an icon that was there, but ended up deleting the whole panel.

it did help some. The main menu did come up.  I will try more later after work. THANKS
Original panel on left had  APPLICATIONS, PLACES, SYSTEM,  And a couple other single icons

---

### Post by brain!ac on 2010-07-13
> **choochoousmc said:**
> thanks but no.
I can add a new panel, but I wanted to recover the original.
I was originally just trying to delete an icon that was there, but ended up deleting the whole panel.

it did help some. The main menu did come up.  I will try more later after work. THANKS
Original panel on left had  APPLICATIONS, PLACES, SYSTEM,  And a couple other single icons

Right click on panel and chose "Add to panel" and from the menu chose "Menu Bar" which is commented "A custom menu bar" .

---

### Post by WorMzy on 2010-07-13
You can reset your panels to their default state by running the following commands in a terminal:

```
gconftool-2 --shutdown
```
```
rm -rf ~/.gconf/apps/panel
```
```
pkill gnome-panel
```

By running these commands you will lose all your changes to the bottom panel too.

---

### Post by Humanity to others on 2010-07-13
> **choochoousmc said:**
> thanks but no.
I can add a new panel, but I wanted to recover the original.
I was originally just trying to delete an icon that was there, but ended up deleting the whole panel.

it did help some. The main menu did come up.  I will try more later after work. THANKS
Original panel on left had  APPLICATIONS, PLACES, SYSTEM,  And a couple other single icons

This may help you

click the below link

[http://jacobwg.com/2010/06/17/restore-original-gnome-panel-configuration-in-ubuntu-10-04/](http://jacobwg.com/2010/06/17/restore-original-gnome-panel-configuration-in-ubuntu-10-04/)

---

### Post by choochoousmc on 2010-07-13
ok back home from work, long day.
Thanks for the help so far.

I now have the original panel back and all the menu items.
The only separate icon in the panel itself that is missing is my network connection showing
I am connected.
I was a vertical stack of arches, with a  exclamation point in it, if I remember right.
I could click it to work with networks, to view available wireless.
How would I retrieve it?

---

### Post by choochoousmc on 2010-07-13
> **Humanity to others said:**
> This may help you

click the below link

[http://jacobwg.com/2010/06/17/restore-original-gnome-panel-configuration-in-ubuntu-10-04/](http://jacobwg.com/2010/06/17/restore-original-gnome-panel-configuration-in-ubuntu-10-04/)

Ok thanks I may try it later.

right now as in above post am only missing the GUI icon for the wireless network.
It was installed by default during setup.
Was a series of vertical arches (I think) with a blue icon in side.  It did not require any specialized user input (such as a terminal etc).
click it, and it showed a list of the available wireless networks in the area. All I had to do was select one and connect.
Will doing the above restore it also?

---

### Post by WorMzy on 2010-07-14
Depends. Did you use my method to restore your original panels? Because that method and my method both just two different ways of doing the same thing.

Try right-clicking on the panel, choosing "add to panel" and dragging an indicator applet onto it.

---

### Post by choochoousmc on 2010-07-16
> **WorMzy said:**
> Depends. Did you use my method to restore your original panels? Because that method and my method both just two different ways of doing the same thing.

Try right-clicking on the panel, choosing "add to panel" and dragging an indicator applet onto it.


as I said everything is back except the original network manager I described it as a series of vertical arches. But could of been like a "radio" tower.
It is NOT on my desktop so I can't drag it.
Did not find it in the ADD menu.
Is there someplace in the system files I can find it?
I used the  right click add panel method.    Time for work will catch up later

---

### Post by WorMzy on 2010-07-16
All applets that can be added to the panel are inside the Add to Panel window. I'm not using Ubuntu at the moment so I'm not sure whether it's part of the Indicator Applet or the Notification Area. Also look for Network Monitor, that's what it's known as on other Linux distros.

---

### Post by choochoousmc on 2010-07-17
> **WorMzy said:**
> Depends. Did you use my method to restore your original panels? Because that method and my method both just two different ways of doing the same thing.

Try right-clicking on the panel, choosing "add to panel" and dragging an indicator applet onto it.

I have not tried your way yet as described in your first post.
Right now all icons and menus are restored, except the network manager.
I found network manager in the list of installed programs, but not as an item I can drag onto the panel.

Also my truecrypt is not working correctly but I will address that later.
In user groups I am the only user and classed as administrator. But I still cannot do many things.

---

### Post by choochoousmc on 2010-07-17
by trial and error I got it back.
I went to add panel.
I clicked on notification applet.
Up popped the icon I described  as a series of arched.
In it is the network manager.
it lets me graphically edit my network without using cryptic commands as in other apps or having to use the terminal.

---

### Post by WorMzy on 2010-07-17
Glad you found it. :)

---

