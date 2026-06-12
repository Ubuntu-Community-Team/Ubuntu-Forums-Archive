---
title: "Glaring problem in Natty - where are the notification icons?"
date: 2011-08-11
forum: General Help
---

### Post by CaptSaltyJack on 2011-08-11
Apps like Shutter, Parcellite, Skype, etc., have icons that sit in the notification area. I am deeply puzzled as to how the developers launched 11.04 without realizing that these icons do not show up. Is there some simple way to get them back?

---

### Post by MG&amp;TL on 2011-08-11
[http://www.omgubuntu.co.uk/2011/04/10-things-to-do-after-installing-ubuntu-11-04/]("http://www.omgubuntu.co.uk/2011/04/10-things-to-do-after-installing-ubuntu-11-04/")

I think No.4 is what you are after. Although I agree, it's dumb. Do like Unity though.

---

### Post by CaptSaltyJack on 2011-08-11
Thanks! That's kinda helpful.. but really it's just telling you apps that support the new panel. I'm looking for a way to get other apps (like Skype) to show up in the panel like they used to. Great link though, thanks!

---

### Post by MG&amp;TL on 2011-08-11
No problem. If you don't like the Unity interface, you could always boot classic gnome 'the original' and presumably the system tray icons show up there. :)

---

### Post by CatKiller on 2011-08-12
> **CaptSaltyJack said:**
> I am deeply puzzled as to how the developers launched 11.04 without realizing that these icons do not show up. 

It's not an oversight, it's a deliberate design choice with the new notification system.

---

### Post by timgood on 2011-08-12
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
``` will fix it for you.

Hope this helps.

---

### Post by CaptSaltyJack on 2011-08-12
As someone who specializes in usability and interface design, I have to emphasize what a poor decision it was to just disregard the potentially hundreds of applications that have a notification icon that is an integral part of its functionality. I DO like the Unity interface and I think it's a step in the right direction (simplifying/cleaning things up but still leaving enough wiggle room for power users), but I'm stunned that the Ubuntu team would just shrug off such a huge issue. Sorry guys, there's no two ways about it, it was a poor design decision. There should've at least been an option in system settings that you can toggle on/off to enable the "old panel." I'm not just picking on Ubuntu either, by the way. Mac OS X Lion is rife with usability problems that are just mind-numbingly stupid.

Anyway, end of rant. timgood, thanks for the answer, I'll give that a shot next time I boot up the 11.04 machine.

---

### Post by CatKiller on 2011-08-12
FWIW, it was quite controversial, as was the decision to move the window decorations to the left-hand side. You're in good company & it's not that you're incorrect, just late :)

---

### Post by CaptSaltyJack on 2011-08-12
> **CatKiller said:**
> FWIW, it was quite controversial, as was the decision to move the window decorations to the left-hand side. You're in good company & it's not that you're incorrect, just late :)

Hehe, understood. I am quite late to the table. And I'm fine with the left-hand thing, it reminds me of NeXT which is cool. I actually like grouping windows and indicating them by little tick marks, and clicking the app to do an "expose" for just that app. Sometimes I have a ton of windows open and it's very cluttery in the traditional Gnome interface. I'm ok with change, as long as it's clearly thought out and executed well.

---

### Post by CaptSaltyJack on 2011-08-24
> **timgood said:**
> ```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
``` will fix it for you.

Hope this helps.

Actually, this turns out to be quite bad. It causes other Unity notification icons to stop responding to clicks (such as the network icon and the sound icon). It seems like the proper thing to do is get the current systray-whitelist and just add to it, e.g.:

```
$ gsettings get com.canonical.Unity.Panel systray-whitelist
['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'scp-dbus-service']
$ gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'scp-dbus-service', 'shutter', 'parcellite']"

```

---

### Post by jim_deadlock on 2011-08-25
This happens sometimes, it's a minor glitch, you can fix it though:

```
unity --replace &
```

... will reset it and get the icons working again.

---

