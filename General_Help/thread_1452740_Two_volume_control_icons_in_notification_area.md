---
title: "Two volume control icons in notification area"
date: 2010-04-12
forum: General Help
---

### Post by donsy on 2010-04-12
This happened upon boot-up this morning. Two volume control icons appeared in the notification area. One volume control icon is the real thing, the other appears to overwrite the network manager icon, which isn't showing up at all. If I left click on the "dummy" icon, it does nothing. If I right click and select About, it describes itself as the notification area, the same as if I right click on the little = handle to the left of the notification area. Ubuntu 9.10, system up-to-date.

---

### Post by nitstorm on 2010-04-12
Then why don't you try right-clicking the dummy icon and click remove from panel, and then right click the empty space on the panel and choose add to panel and select the network manager.

---

### Post by donsy on 2010-04-12
> **nitstorm said:**
> Then why don't you try right-clicking the dummy icon and click remove from panel, and then right click the empty space on the panel and choose add to panel and select the network manager.

Because the icon thinks it's the notification area. If I remove it I'll be removing the entire notification area.

---

### Post by nitstorm on 2010-04-12
> **donsy said:**
> Because the icon thinks it's the notification area. If I remove it I'll be removing the entire notification area.

you can also add a notification area by right clicking and add to panel...

---

### Post by donsy on 2010-04-12
> **nitstorm said:**
> you can also add a notification area by right clicking and add to panel...

Yes I know. But I'd like to avoid having to remove the notification area and adding it back every time I boot up.

---

### Post by nitstorm on 2010-04-12
LOL, this is the best I can help you out mate, I am a newbie here as well...

---

### Post by donsy on 2010-04-12
> **nitstorm said:**
> LOL, this is the best I can help you out mate, I am a newbie here as well...

It's OK mate. Thanks for trying.

---

### Post by kamikazepsi on 2010-04-16
i have this issue too on two different machines....(desktop and netbook)

it happens randomly...removing the notification area and adding it back fixes the problem but that's pretty annoying.  

sometimes, i'll get 2 volume icons with one being "dead" like donsy gets....sometimes times i'll get a gray box...and sometimes i'll get a partial "dead" volume icon.

my netbook is a fresh install from about 2 weeks ago.....my desktop had 9.10 installed 5 months ago...but only started acting up recently.

---

### Post by noremacyug on 2010-04-16
i had this happen in 10.04.  removing the notification area and the indicator applet and then re-adding solved it for me, no further issues.

---

### Post by kamikazepsi on 2010-04-16
well, i did a little more research and it seems like a lot of people have this bug. i didn't see an official fix but one user suggested making a script that kills gnome panel on start up which makes it restart. 

#!/bin/bash
killall gnome-panel

set it to run under startup applications.

---

### Post by TnTonly on 2010-05-04
I've just upgraded Ubuntu 10.04 and now I have 2 volume icons, one belongs to Indicator Applet, have a nice graphical icon like the rest of the theme. The other belongs to Notification Area with the Network Manager, and has an incredibly ugly icon. I don't know how to remove the other volume icon, as I have to remove the entire Notification Area as well as the Network Manager icon. 

This only happens with my account. The Guess Session seems to be not affected by this. Does anyone have any solution?

---

### Post by RedMartin on 2010-05-16
Sorry to bump this one but I'm having a similar issue. Mine differs in that I occasionally get two network manager icons instead of one plus the volume applet.

Any ideas?

---

### Post by linuxman94 on 2010-05-16
Go to startup applications (System -> Preferences -> Startup applications) and remove the entry for gnome volume control.  That solved my problem.

---

### Post by platz on 2010-06-02
> **linuxman94 said:**
> Go to startup applications (System -> Preferences -> Startup applications) and remove the entry for gnome volume control.  That solved my problem.

I have the same trouble without the gnome volume control in start-up apps - any other ideas out there?

---

