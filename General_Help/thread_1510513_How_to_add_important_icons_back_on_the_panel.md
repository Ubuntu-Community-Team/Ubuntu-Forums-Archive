---
title: "How to add important icons back on the panel?"
date: 2010-06-15
forum: General Help
---

### Post by galobuntu on 2010-06-15
Hi, everyone.

I have accidentally removed a few icons from my panel. Since they are kind of important and I use them a lot, I was wondering how I can have them display again on may panel. The icons I'm talking about are the POWER/BATTERY STATUS, SOUND/VOLUME and COMMUNICATIONS/E-MAIL icons. I still have other gadgets running on the panel, such as the weather monitor, time and date, etc.

To try to restore the lost icons, first thing I did was to right-button click on the panel and then choose the "Add to panel" option, hoping that I'd find those there. Unfortunately it didn't work.

Any ideas?

Any help is appreciated.

---

### Post by golanbatrac on 2010-06-15
Did you try the 'Notification Area' applet and the 'Indicator Applet'?  That should bring back everything you're looking for.

---

### Post by galobuntu on 2010-06-15
Yeah, I did and all it got me was an area between two little bars with nothing in it

---

### Post by golanbatrac on 2010-06-15
Go to **System > Preferences > Startup Applications**, and make sure that 'Volume Control' 'Indicator Applet' and 'Network Manager' are both listed and checked and then reboot.

If they're not listed in Startup Apps, post back and I'll walk you through adding them.

---

### Post by wojox on 2010-06-15
Run these two commands and it will reset your panels

```

gconftool --recursive-unset /apps/panel
pkill gnome-panel
```

---

### Post by galobuntu on 2010-06-15
Thank you, wojox. It worked.

:p

---

### Post by wojox on 2010-06-16
Your Welcome :p

---

