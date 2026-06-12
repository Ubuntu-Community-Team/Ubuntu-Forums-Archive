---
title: "Ubuntu equivalent to Windows' Control Panel (where's Flash Player Settings Manager)?"
date: 2011-05-13
forum: General Help
---

### Post by nrundy on 2011-05-13
Just got Flash Player 10.3 installed. In the Windows control panel there is now a Flash Player Settings Manager that lets me configure various settings.

Where do I find this in ubuntu?

---

### Post by lithopsian on 2011-05-13
I think [this]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html") is what you want.  Click link.

---

### Post by nrundy on 2011-05-13
sort of. The new Flash Player released yesterday I think has a new feature where it adds a settings panel into the OS. Linux is listed as an OS that received this feature. I'm wondering where to find it in Ubuntu. It was easy enough to find in Windows.

see here:  [http://www.ghacks.net/2011/05/13/adobe-flash-player-10-3-final-downloads/](http://www.ghacks.net/2011/05/13/adobe-flash-player-10-3-final-downloads/)

---

### Post by lithopsian on 2011-05-13
The settings manager in 10.3 is basically the same as the online one I linked to.  There are also supposed to be APIs for browsers themselves to access settings directly.  I don't have 10.3 yet, but according to the documentation you will find it either in:

Gnome: System > Preferences > Adobe Flash Player
or in:
KDE: System Settings > Adobe Flash Player

In Gnome you should have a binary:
usr/bin/flash-player-properties

In KDE you get a shared object:
usr/lib/kde4/kcm_adobe_flash_player.so
and a desktop file:
usr/share/kde4/services/kcm_adobe_flash_player.desktop

Hopefully one of those will work for you.

---

### Post by zevans on 2013-01-04
You need to install the package "adobe-flash-properties-kde"

(This seems to be giving me some weird dependency problems but nothing has actually broken)

---

### Post by overdrank on 2013-01-04
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

