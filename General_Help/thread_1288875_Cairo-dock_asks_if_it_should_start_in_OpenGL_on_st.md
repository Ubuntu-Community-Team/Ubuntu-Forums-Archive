---
title: "Cairo-dock asks if it should start in OpenGL on startup"
date: 2009-10-11
forum: General Help
---

### Post by Slaskie on 2009-10-11
Whenever logging into Kubuntu 9.04, I get a popup asking if I want to run cairo-dock normally or in OpenGL (I can't run it in OpenGL because my intel graphics card messes OpenGL up). Screenshot attached. I want cairo-dock to automatically start up upon login without me having to first select 'No' from the dialog that appears. I added a -c to the cairodock command in the Autorun menu, but it made no difference. How can I stop the popup and have cairodock autorun normally when I login?

---

### Post by ankspo71 on 2009-10-11
Hi,
This is strange because I just tried cairo-dock -c and it worked like it was supposed to and removed the yes or no window at startup. I use opengl but I wanted to see what would happen. Is your start up entry correct with cairo-dock -c ? I don't use KDE and I am using Karmic beta so what works for me may not be working for you. Try ```
cairo-dock --cairo
``` to see if that helps.
James.

---

### Post by Slaskie on 2009-10-17
I went to the autostart menu and deleted the cairodock entry, then retyped it as cairo-dock -c , just like before. I rebooted and the dock loaded normally without the popup - and then the popup appeared. Now whenever I log on, I have cairo-dock -c start up and then I get a popup, which results in a second cairo-dock appearing no matter what I click. I then have to close one of the docks. :( How can I make the OpenGL popup go away? as I now have a working cairo dock start up upon login

---

### Post by punchdrunkgrunt on 2009-10-17
Had exactly the same problem. Try this:
Open System Settings => Session Manager
Select "Start with an empty session" and apply.
Leave the cairo-dock -c command in autorun.
Worked for me.

---

### Post by Slaskie on 2009-10-18
Worked perfectly, thanks

---

### Post by jackharvest on 2011-01-14
cairo-dock -c   worked for me (just replaced the -o with -c, tada - worked. :popcorn:

---

