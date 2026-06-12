---
title: "Num Lock causing 'mouse lock' problems"
date: 2011-03-21
forum: General Help
---

### Post by mendhak on 2011-03-21
I didn't know how to title this well.  I'll describe the problem the best I can. I'd appreciate any troubleshooting steps. 

Basically, if I press Num Lock to use the numeric keypad, the input becomes weird - it's as though the left click button of the mouse has been held down. 

In this image below, I have just logged in.  I press Num Lock and then move the mouse, as you can see it's drawing a rectangle "thinking" that the left mouse button is held down.  I cannot 'escape' from this situation either. 

[img]http://i.imgur.com/9p4Dw.jpg[/img]

For example if I'm in text editor and I press num lock (turn it on), then the mouse-cursor changes to the vertical line and stays like that no matter where I move it on screen.  If I move it over a button, then the button's color changes (indicating that it realizes that a mouse is hovering over it) but I cannot click on anything.  I can right click just fine. 

The only way I can escape - I usually do a sudo reboot from terminal.  I have to reboot a few times and then everything goes back to normal.  I say reboot a few times because sometimes the problem persists across reboots.  I'll log in, and I'm still in that weird num lock mode!

I have tried this with different keyboards (both PS/2 and USB) and the same problem persists.

I also noticed that on the actual login screen, the num lock and numeric keypad works just fine.  It's only after logging in that the num lock behaves weird. 

Here are my settings:

[IMG]http://i.imgur.com/2MQLr.jpg[/IMG]
[img]http://i.imgur.com/Kjve7.jpg[/img]


I am running Ubuntu 10.10 Maverick. I'd really appreciate any way of troubleshooting this or even things to try.

---

### Post by mendhak on 2011-03-26
A day or two after this post, I booted up my machine and was greeted with a "Kernel Panic - unable to mount vfs root" message.  I then had to reinstall Ubuntu.  However, as part of the initial re-setup, I also installed a package called numlockx.

This fixed the issue.  

123456789

I can't tell whether it was the OS reinstall or numlockx which fixed the issue but I figured I might as well post what did happen.

---

