---
title: "Change a specific icon"
date: 2010-12-18
forum: General Help
---

### Post by 3rr0r on 2010-12-18
Hello all.  I was wondering how to change a specific icon.  This icon is the network connection icon and shows your network connectivity status.  I just need to know what path the system is using to select this icon, so then I can change it to my desired icon.  Please see screenshot below in the upper right hand corner (it's white and I have a black version I'd like to use instead).

Thank you all for the support!  Ubuntu community has been very helpful.

EDIT: It's very hard to see so I added some additional screenshots to make it clearer which icon I'm trying to change.

---

### Post by Wobblybob on 2010-12-18
check out the Appearance menu for the icon theme you are using then check out /usr/share/icons and that icon theme folder

for instance /usr/share/icons/Humanity-Dark/status/16/nm-signal-00.svg

---

### Post by 3rr0r on 2010-12-18
> **Wobblybob said:**
> check out the Appearance menu for the icon theme you are using then check out /usr/share/icons and that icon theme folder

for instance /usr/share/icons/Humanity-Dark/status/16/nm-signal-00.svg

This is a bit weird but I went into SYSTEM > Preferences > Appearance  to lookup which icon theme I was using.  I noticed that when I changed themes, all my icons changed except for the network connectivity icon (the one I want to change).  Any ideas?

I am using Drakefire Evolution Inverted. 
I went through /usr/share/icon/Drakefire\ Evolution\ Inverted/ directory and could not find that icon anywhere.


EDIT:  I should have probably tried this... I rebooted and it updated correctly.  Thank you :)

---

