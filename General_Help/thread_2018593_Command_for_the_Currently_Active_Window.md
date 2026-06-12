---
title: "Command for the Currently Active Window?"
date: 2012-07-06
forum: General Help
---

### Post by Aqil on 2012-07-06
Is there a command that returns the currently active window?

I using ubuntu 11.10 and it seems that compiz is my window manager by default.

Basically I want the terminal to return whatever string is in the menu bar at the top of my screen. Python code would also do the the trick.

---

### Post by rg4w on 2012-07-06
Installing wmctrl should allow you to do what you're looking for:

[http://www.linuxjournal.com/magazine/hack-and-automate-your-desktop-wmctrl](http://www.linuxjournal.com/magazine/hack-and-automate-your-desktop-wmctrl)
[http://spiralofhope.wordpress.com/2010/02/03/wmctrl-user-documentation/](http://spiralofhope.wordpress.com/2010/02/03/wmctrl-user-documentation/)

---

### Post by Aqil on 2012-07-06
Now I installed wmctrl. But what's the command that returns the name of the active window?

The closest I can find is a string with all managed windows:

> aqil@Computer:~$ **wmctrl -l**
0x02200004  0 Computer Desktop
0x02600002  0      N/A DNDCollectionWindow
0x02600003  0      N/A launcher
0x02600004  0      N/A panel
0x03200044  0 Computer wmctrl - A command line tool to interact with an EWMH/NetWM compatible X Window Manager. - Chromium
0x02600005  0      N/A Dash
0x0420008e  0 Computer Trigonometry.odt - LibreOffice Writer
0x04800006  0 Computer aqil@Computer: ~


That's great! But is there also any way to get the *one and only* window currently active? From the string above, there seems to be no telling which window was open when the command was executed.

Thanks!

---

### Post by rg4w on 2012-07-06
For many options you can use the :ACTIVE: keyword to act on the topmost window:
[http://abhijeetmaharana.com/blog/2007/06/22/wmctrl/](http://abhijeetmaharana.com/blog/2007/06/22/wmctrl/)

e.g.:
wmctrl -r :ACTIVE: -b toggle,fullscreen

That seems to work for me with what I've been doing with wmctrl, but according to this page in some cases a workaround may be required - the last post here describes a way of tricking wmctrl to obtain the ID of the topmost window if ":ACTIVE:" isn't doing what you need:
[http://stackoverflow.com/questions/4272232/what-are-the-alternatives-to-wmctrl](http://stackoverflow.com/questions/4272232/what-are-the-alternatives-to-wmctrl)

---

### Post by Aqil on 2012-07-07
Well, this is more complicated than what I'm used to but it sure gives me something to work on. There seems to be no command to simply print the active window, but the workaround is working for me so I'll keep working on that. Thank You rg4w!

---

