---
title: "logout freezing"
date: 2006-03-19
forum: General Help
---

### Post by jms830 on 2006-03-19
ubuntu freezes when i try to logout. I click on the menu, i click logout, then nothing happens: the box with options doesnt pop up, nothing, it just freezes. 

if I press ctrl-alt backspace, i can "killall gdm" from the command prompt, and then "gdm" to get back in. But I cannot logout, it just freezes.

---

### Post by varunus on 2006-03-19
When it freezes, hit escape.  Does this bring your desktop back?

Are you using Composite effects like in poofyhairguy's howto?  If so, this is a bug with xcompmgr that causes the logout dialog not to appear.

---

### Post by jms830 on 2006-03-20
yes i am using the xcompmgr, is there a way around the bug?

---

### Post by varunus on 2006-03-20
One way, of course, is to just close xcompmgr before you try to logout.

The other is to set GNOME (when you select the logout option) to just take you straight back to the GDM menu.  Open the "Configuration Editor" and navigate to apps > gnome-session > options, and uncheck "logout_prompt" there.  This will make you have to reboot and shutdown at the login prompt rather than straight from your session.

Once you're up to Dapper Drake (when its released), you can get XGL and compiz for much stabler, much nicer composite effects than xcompmgr.  I'm using them right now; almost no graphical glitches, and amazing graphics.

---

