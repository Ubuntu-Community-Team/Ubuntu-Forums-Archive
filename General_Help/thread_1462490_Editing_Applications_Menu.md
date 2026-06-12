---
title: "Editing Applications Menu"
date: 2010-04-25
forum: General Help
---

### Post by kjtruitt on 2010-04-25
After an hour of googling and snooping around my file system, I still
have not found a way to get rid of the Applications menu entry for eclipse that was put in 'Development' and replace it or update it with an appropriate command for the newer eclipse binary I just installed.

This comes up frequently and I've not been able to figure out how to do it.
I downloaded Alacarte and this doesn't help--it's clearly getting its information from one of the obsolete xml menu files I found under X11 which has an 'Education' entry, and rather than a 'Development' entry, it has a 
'programming' sub menu.  Can't be right.

Right-clicking on the Applications menu only brings up options for the Panel--NOT the Applications menu that is part of the panel.

Xubuntu 9.10

I'm seeking, at this point, a command-line solution.

---

### Post by Jose Catre-Vandis on 2010-04-25
Try browsing to:

/usr/share/applications

Find the offending entry and delete (to trash)

Log off Log on

or 

edit the entry you need to point to the correct binary/script

No way to properly edit the xfce4 menu - hopefully coming soon :)

---

### Post by -humanaut- on 2010-04-25
> **Jose Catre-Vandis said:**
> Try browsing to:

/usr/share/applications

Find the offending entry and delete (to trash)

Log off Log on

or 

edit the entry you need to point to the correct binary/script

_**No way to properly edit the xfce4 menu - hopefully coming soon**_ :)

That is entirely wrong it's simple to edit the applications.gtkrc-2.0 file.

---

### Post by kjtruitt on 2010-04-25
Thanks that was what I was looking for.

Btw, I couldn't *locate* applications.[etc]-2.0, or anything like it.

---

### Post by -humanaut- on 2010-04-26
se a transparent background for desktop icon titles 
To change the default white background of desktop icon titles to something more suitable, edit the .gtkrc-2.0 file in your home directory (or create the file if needed) and add the following: 
style "xfdesktop-icon-view" {
XfdesktopIconView::label-alpha = 10
base[NORMAL] = "#000000"
base[SELECTED] = "#71B9FF"
base[ACTIVE] = "#71FFAD"
fg[NORMAL] = "#ffffff"
fg[SELECTED] = "#71B9FF"
fg[ACTIVE] = "#71FFAD" }
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

 How to customize xfce panel background 
The same, edit ~/.gtkrc-2.0. ( foo.bar is path to your image ) Note that you must place the image in the same directory as the configuration, which is ~/. You can not specify the path to the image, or it won't work. 
 style "panel-background" {
   bg_pixmap[NORMAL]        = "foo.bar"
   bg_pixmap[PRELIGHT]      = "foo.bar"
   bg_pixmap[ACTIVE]        = "foo.bar"
   bg_pixmap[SELECTED]      = "foo.bar"
   bg_pixmap[INSENSITIVE]   = "foo.bar"
 }
 widget_class "*Panel*" style "panel-background"

 Quicklaunch and smart bookmark plugins for xfce panel 
If these options do not appear in your "add new items" panel menu when the appropriate package(s) are installed,

credit=Archlinux wiki

Google is your friend.

---

### Post by Jose Catre-Vandis on 2010-04-26
dang - please ignore

---

### Post by Jose Catre-Vandis on 2010-04-26
> **-humanaut- said:**
> That is entirely wrong it's simple to edit the applications.gtkrc-2.0 file.

I think we are talking about different things. I agree you can change the look and feel of the menu as you suggest, I was seeking to answer the OP's request to remove a menu item? :confused: Happy to be proved wrong.

---

