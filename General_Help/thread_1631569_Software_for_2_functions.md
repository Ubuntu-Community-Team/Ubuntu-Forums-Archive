---
title: "Software for 2 functions"
date: 2010-11-26
forum: General Help
---

### Post by jpboyrox on 2010-11-26
Is there software for Ubuntu that can imitate the alt-left mouse button drag to resize windows functionality of 'Taekwindow' (only on Windows). Resizing windows with Ubuntu on my resolution is just a pain as you must be ridiculously precise, this would help. If there is another alternative, please let me know. 
Is there software/a setting to allow me to hold the middle mouse and move the cursor to scroll, this would speed things up considerably.
Also: how do you edit your bookmarks and how do you change a link's icon in Ubuntu? I downloaded and installed a program ('thunderbird-gnome-support'), how do I run this?

EDIT: Is there software that will allow me to middle mouse click on windows in the bottom panel in order to close them like 'Taskbar Shuffle' for windows.

---

### Post by jpboyrox on 2010-11-26
Taekwindow and Taskbar Shuffle have actually imitated linux's functions and added a bit extra. The bit extra is the bit that I want to keep now I am considering moving to ubuntu. I have installed ubuntu on my dud laptop to see how things play out. That's what I am using now.

---

### Post by jpboyrox on 2010-11-26
Also, on an unrelated note, I went into main menu and created a new menu. Now I have changed my mind and want to delete it, how do I do this? I thought it would be obvious but apparently not.

---

### Post by asmoore82 on 2010-11-26
> **jpboyrox said:**
> Resizing windows with Ubuntu on my resolution is just a pain as you must be ridiculously precise, this would help. If there is another alternative, please let me know.
By default in Gnome:
Alt + Left Click moves a window;
Alt + Right Click opens the window menu;
Alt + Middle Click resizes a window.

If you are on a 2-button mouse or laptop, you can achieve a middle clicking by clicking both buttons at once. To swap the middle and right click behaviors, open the configuration editor ```
gconf-editor
```
For metacity (no desktop effects), edit:
"/apps/metacity/general/resize_with_right_button"
For compiz (desktop effects), edit:
"/apps/compiz/general/allscreens/options/window_menu_button"
"/apps/compiz/plugins/resize/allscreens/options/initiate_button"

You can also right click the menu title bar or window list button and select "resize."

---

### Post by asmoore82 on 2010-11-26
> **jpboyrox said:**
> Also, on an unrelated note, I went into main menu and created a new menu. Now I have changed my mind and want to delete it, how do I do this? I thought it would be obvious but apparently not.

You can either:
Right-click the menubar and "edit menus," then hit the "revert" button.
This will undo all of your menu changes.

Or:
I believe your custom menu entries are in the hidden folder:
"$HOME/.local/share/applications"

---

