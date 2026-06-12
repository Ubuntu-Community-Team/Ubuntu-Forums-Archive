---
title: "blank windows"
date: 2010-08-22
forum: General Help
---

### Post by Gakumerasara on 2010-08-22
At the login screen, the background loads and the border of the login window loads, but everything within the window is white. There's no text, no buttons, nothing. Since I've logged in so many times and know the routine, I can press spacebar, type in my password, and proceed into the Desktop environment without having to use the windows. As I type my password, I can see a cursor moving, but no text is displayed. My mouse cursor isn't showing up either.

At the desktop, I can again see the background fine. The panels show up, but their contents are hidden by gray boxes. The only panel object that isn't obscured is the CPU usage monitor, which seems to be behaving normally. When I insert a photo SIM card, a window pops up, and I can see the photos thumbnails and nothing more. A few windows pop up. The title bars are dark, and the window panes are different colors in some cases, but the window contents are completely gone. I'm guessing this is a problem with X, but any help would be appreciated since I'm not an expert at diagnosing Linux problems.

---

### Post by bergfly on 2010-08-22
I think you may be right in pointing out this might be an X issue, however in order to start working on it, we will need more information. 

The first place to start is -- Did anything change recently. Did you install new packages or hardware, or did you do a system update?

Secondly, let look more into the graphic system. What graphics card are you using? Have you made any tweaks to your X11.conf file. 

If we can isolate a cause for this, fixing it will be a lot easier

---

### Post by Gakumerasara on 2010-08-23
Ubuntu 10.04 kernel 2.6.31-22 is the last kernel that works for me.
2.6.32-22 goes to a black screen.
2.6.32-23 and 2.6.32-24 both have the same blank window issue.

I haven't changed anything recently, but the 3 newer kernels have never worked for me on this particular computer.
I updated to each new kernel as it became available and have since been updating within the oldest one (since it works).

This is an Acer 9800 laptop with an NVidia GeForce Go 7600 graphics card.
I'm not using the NVidia proprietary drivers b/c doing so kills my display.

I'm fairly certain I haven't tweaked X11.conf since I last re-installed Ubuntu.
(My last attempts to tweak it killed the display, causing me to re-install the whole system.  I haven't messed with it since.)

---

### Post by andthewicked on 2010-08-23
I'm having the same problem I am using nvidia driver and just updated to lucid 10.4LTS and after the upgrade is when I started having this problem.

---

### Post by Gakumerasara on 2010-08-26
Is there any other information I could provide that would help?

---

### Post by bergfly on 2010-08-27
I would recommend installing the drivers for this card. Here is a step by step for your card.

[http://ubuntuforums.org/showthread.php?t=446578]("http://ubuntuforums.org/showthread.php?t=446578") 

Hope it helps

---

