---
title: "When ever i hit the d key only lower case all my windows minimize"
date: 2010-10-25
forum: General Help
---

### Post by coldstreak18 on 2010-10-25
Its really annoying I don't have a monitor I just use VNC and putty to control my computer and when ever I vnc in and hit d all the windows minimize I tried deleting everything under .gnome2,.nautilus,.gconf and nothing. 

I love Ubuntu but this upgrade has been nothing but problems. I did a complete reformat and its a huge pita. its problem after problem never had this with 10.04

---

### Post by luvshines on 2010-10-25
All the windows minimize on the host machine desktop or the one to which you are connected to using VNC ?
Have you checked the keyboard shortcut for 'hide all normal windows...' in System->preferences->keyboard shortcuts ?

---

### Post by Jliax on 2010-10-25
I have the same very annoying problem (XFCE + VNC) here. Unfortunately there is no item under system or preferences named keyboard shortcuts. Also the xfce4-keyboard-shortcuts.xml file does not contain this shortcut.

---

### Post by joshaidan on 2010-11-11
I had the same problem. But what I did was go into System -> Preferences -> Keyboard Shortcuts, and then scrolled down until I found this option, "Hide all normal windows and set focus to the desktop."  For some reason the letter D was there so I selected it and hit delete to disable that shortcut.  Then I had to log out and log back in and it seems to be okay now.

---

### Post by emitflesti on 2011-01-27
Thanks for this.

---

### Post by Amannim on 2011-05-10
What on Earth created this configuration? I just upgraded from 10.04->10.10->11.04 and I too was plagued by this 'feature' in my remote sessions only. Strange thing was I could type 'd' in a password input and that was fine. Having to choose words without 'd' or cutting and pasting for shell commands was getting old.

THANKS FOR THIS THREAD!

Now if only I can figure out why FireFox keeps crashing in VNC and I'm back to 100%

---

### Post by mikeh on 2011-05-23
I just had this problem on a completely clean install of 11.04 desktop on the server.
'D' was set as shortcut. How??
Also, tab was not working, but that seems to be fixed .

---

### Post by StygianAgenda on 2011-05-24
I had this exact same problem appear, seemingly for no apparent cause.  I would love to know where this crept in from.  If this came from an update, then we need to know about it.  If it's installing this way, then we need to know why someone would set such a ridiculous option as a default. :-\"

---

### Post by jaredheath on 2011-08-18
This thread just saved me heartache.

Same issue.  This wasn't the case a month ago...something changed it.

---

### Post by jimerman on 2011-09-27
OK, I deleted the key binding, rebooted, and still when I press the lower-case D all windows minimize, even in password authentication.  I am using Tight VNC Server, Tight VNC Client (Windows), and Ubuntu 11.04.

---

### Post by jimerman on 2011-09-27
OK, very strange!  If I use the built-in desktop sharing, I don't have this problem.  But, the problem with built-in is the user has to be logged in to be able to log in via VNC.  TightVNCServer allows me to log in when a user is not logged in.

---

