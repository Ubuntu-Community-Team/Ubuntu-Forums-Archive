---
title: "Guest XP in VirtualBox on Ubuntu 10.04: no &quot;Start&quot; menu?"
date: 2010-10-27
forum: General Help
---

### Post by t0p on 2010-10-27
I've installed VirtualBox version 3.2.10 r66523 on my Ubuntu 10.04 machine (it's the closed source version, with USB support) and something odd is going on.  I just installed Windows XP as a guest OS, then installed the drivers for my printer (HP Deskjet D2660) and now I can't get to the "Start" menu.  You know how you move the mouse pointer around near the bottom of the display and the "Start" button appears?  Well, it doesn't.

I don't know what I've done to change this behaviour; but it's pretty annoying, yeah?  How am I going to run anything if I can't get to the "Start" button?

If anyone knows what I've done/what I need to do etc, I'd really appreciate your help.  Thanks!!

---

### Post by wilee-nilee on 2010-10-27
Personally I can't tell what start button your talking about how about a screen shot.

---

### Post by t0p on 2010-10-28
> **wilee-nilee said:**
> Personally I can't tell what start button your talking about how about a screen shot.
 
I can't take a screen shot of the "Start" button because it isn't there...

Cast your mind back to the days of XP.  If you move your mouse pointer around the bottom of the screen, a panel becomes visible across the bottom of the display; and in the bottom left corner appears a button with the word "Start" written on it.  You press that "Start" button and you get menus (documents, menus of programs, control panel etc).

Well, I don't know what I've done, but the bottom panel and the "Start" button no longer appear when I mouse over the area.  If I press the "Window" key then the list of apps, places etc appears, but the bottom of the list isn't available (it's lost down under the bottom of the display, and I can't "drag" it up).

I don't know what I've done to cause this, so I don't know how to fix it.

---

### Post by anglican on 2010-10-28
> **t0p said:**
> I can't take a screen shot of the "Start" button because it isn't there...

Cast your mind back to the days of XP.  If you move your mouse pointer around the bottom of the screen, a panel becomes visible across the bottom of the display; and in the bottom left corner appears a button with the word "Start" written on it.  You press that "Start" button and you get menus (documents, menus of programs, control panel etc).

Well, I don't know what I've done, but the bottom panel and the "Start" button no longer appear when I mouse over the area.  If I press the "Window" key then the list of apps, places etc appears, but the bottom of the list isn't available (it's lost down under the bottom of the display, and I can't "drag" it up).

I don't know what I've done to cause this, so I don't know how to fix it.Are you running the VM in fullscreen? If not, there may be a scroll bar on the VM window that you need to drag down to reach the true bottom of the VM screen. 

Another option would be to disable the taskbar autohide feature - so it's always there. Run regedit and look for the key:

HKEY_CURRENT_USER\Software\Microsoft\Internet Explorer\Desktop\Components\0


H

---

### Post by phr0ze on 2010-10-28
Maybe explorer crashed...

Try this to restart explorer.
Press Cntl_Alt_Delete to bring up the Security Window. Hit Task Manager Button, Then From File menu choose new Task.
For the task, just type explorer

If this doesn't work, or if task manager shows explorer is running, you can also try End Task on explorer. In most cases windows will restart the process itself in a few seconds. If it doesn't then just complete the steps above.

---

### Post by wilee-nilee on 2010-10-28
I see you mean the regular XP panel start. You can actually overwrite the original install while keeping your accounts and data. I did this just a couple of days ago just for fun and to clean out the temp stuff in my Vbox XP.
[http://www.informationweek.com/news/windows/showArticle.jhtml?articleID=189400897](http://www.informationweek.com/news/windows/showArticle.jhtml?articleID=189400897)

---

### Post by johnmay on 2010-10-28
my thoughts and Occham's razor would suggest that anglican has a good idea. 

Check the screen resolution in XP and minimize until you see the entire desktop.
If you have not already installed the  VBoxGuestAdditions I would recommend that as well. 

I am running the free version, though I recall that adding the guest additions solved a few problems.

---

