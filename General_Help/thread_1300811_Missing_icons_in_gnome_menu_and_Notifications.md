---
title: "Missing icons in gnome menu and Notifications"
date: 2009-10-25
forum: General Help
---

### Post by celtic426 on 2009-10-25
Hi,

2 problems I've been having since I installed Ubuntu 9.10 RC the other day.  First is the missing icons in the menu which just make the menu look weird.  You can see from the screenshot at the bottom left where the icons are missing.  Is there a way to fix this?

[IMG]http://img257.imageshack.us/img257/8008/screenshotbs.png[/IMG]


The second problem I have is the notifications that pop up in the top right of the screen when a buddy signs in or signs off of pidgin.  Yes I switched from empathy to pidgin.  I'm aware that these are a part of a new system wide notification system, so I'm wondering how I can turn them OFF for pidgin.  

Thanks.

---

### Post by gnuisancev3 on 2009-10-25
To turn off pidgin notifications, look in Pidgin's plugins section and uncheck Libnotify (or change the options for libnotify if you wish)..

I too am having the problem on Ubuntu's Main Menu  and/or Menu Bar applets where the "System" menu does not  have icons either.  In Karmic.

---

### Post by celtic426 on 2009-10-25
> **gnuisancev3 said:**
> To turn off pidgin notifications, look in Pidgin's plugins section and uncheck Libnotify (or change the options for libnotify if you wish)..

I too am having the problem on Ubuntu's Main Menu  and/or Menu Bar applets where the "System" menu does not  have icons either.  In Karmic.

Thanks for the response but I'm not looking for pidgin notifications.  I know about those and I do use those, but in addition to those there is a new notification system which includes notifiying you about piding buddies.  I want to configure this so it stops telling me about pidgin.  This is what it looks like, except it says my buddy's name: [http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/]("http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/")

---

### Post by lovinglinux on 2009-10-25
Go to "System >> Preferences >> Appearance". There is an option there to enable the menu icons. I don't remember exactly where, because I switched to KDE and can check it. But it is there.

---

### Post by celtic426 on 2009-10-25
> **lovinglinux said:**
> Go to "System >> Preferences >> Appearance". There is an option there to enable the menu icons. I don't remember exactly where, because I switched to KDE and can check it. But it is there.

System - Preferences - Appearance - Go to Interface tab - Check "Show icons in menus"

Thank you.

---

### Post by kgaipal on 2010-06-05
> **celtic426 said:**
> System - Preferences - Appearance - Go to Interface tab - Check "Show icons in menus"




$ gconf-editor

and then select "/desktop/gnome/interface"

check the entry for "menus_have_icons"

---

