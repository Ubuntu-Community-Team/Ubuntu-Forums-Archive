---
title: "Netbooks: Getting More Vertical Screen Real Estate"
date: 2009-10-26
forum: General Help
---

### Post by flipper9 on 2009-10-26
Netbooks are great, but they have height-restricted netbook screens. I have found that the best way to reclaim quite a bit of that vertical space by making the following changes to the default Gnome setup in Ubuntu (I'm running Karmic but should work in Jaunty and possibly others)...

1. Remove the bottom toolbar from the Ubuntu Desktop.
2. Remove the Applications/Places/System bar and replace with the standard Gnome menu (just the icon)
3. Remove the Firefox and Help shortcuts
4. Add the "window-picker-applet" (sudo apt-get install window-picker-applet) to the top Gnome toolbar and justify to the left. This bar will show all windows as icons, and integrate the titlebar when windows are maximized and have focus.
5. Configure compiz to hide the window decoration for maximized windows (since the titlebar is integrated into the top toolbar (into the window picker applet) when maximized. First install the CompizConfig Settings Manager (sudo apt-get install compizconfig-settings-manager), then goto the "Effects/Window Decoration" setting. Under "Decoration Windows" you will need to change "any" to "!state=maxvert". This prevents maximized windows from having their window decoration drawn.
6. To switch desktops, I just configure the "Desktop/Expo" compiz plugin to show all desktops when I place the mouse pointer into the bottom left-hand corner of the screen. 
7. To show all open windows, I configure the "Window Management/Scale" compiz plugin to show all windows on all desktops when I place the mouse pointer in the lower right-hand corner of the screen (I also disable showing the desktop when the desktop is clicked under this plugin).

Hope this helps.

---

