---
title: "Xubuntu Newbie: iDesk? + I accidently deleted panel 1 :'("
date: 2010-04-26
forum: General Help
---

### Post by ptuy on 2010-04-26
Hello fellow linux-geeks!

First: I am very new to linux, and I just installed Xubuntu on my laptop, fantastic experience!.. But as always, i'm a bit confused adjusting to a new OS. This is what i'm experiencing right now :)

I have several questions for you guys, but at the moment I only remember two of them. I will add more as I remember them.

**1:** I was playing around with the panels, adding icons and stuff. Then i added the "verve-commando bar" but found out that I couldn't remove it again.. This annoyed me and I decided to make a clone of the "panel 1" and just adding everything manual. I deleted panel 1, and later found out that PowerManagement and the wireless network connection icon was lost.. and I can't figure how to get them back.. :confused::confused:

**2:** First I installed Ubuntu 10.04 on my laptop, later to find out that it made my laptop very slow. When I had Ubuntu i could put icons on the desktop, and resize them just as I wanted.I made a huge chrome icon as the only one on the desktop, mmmmhhhhhh yum yum!
But this isn't working in xubuntu :cry:, as you probably already know all about!
I surfed the Internet and found this tiny little Idesk application. I installed, made a .idesktop folder inside my HOME directory. I made a file called chrome.lnk - inside this file I put the following, but i doesn't show any Google Chrome icon on the desktop.  ](*,):^o

[B] table Icon
    Caption: Google Chrome
    ToolTip.Caption: Run Chrome
    Command: google-chrome
    Icon: usr/share/icons/hicolor/16x16/apps/google-chrome.png
    Width: 600
    Height: 700
    X: 30
    Y: 20
  end[/B]

Regards Rasmus - who looooooves linux!

---

### Post by ptuy on 2010-04-26
+ What is a keyring? :)

---

### Post by conradin on 2010-04-26
> **ptuy said:**
> + What is a keyring? :)

Place to hold your keys (passwords)

---

### Post by ptuy on 2010-04-26
Thank you! :) I could have googled that, silly me!

How do I access the internet when the network manager is gone in panel 1? Please help!

---

### Post by SnickerSnack on 2010-04-26
> **ptuy said:**
> **1:** I was playing around with the panels, adding icons and stuff. Then i added the "verve-commando bar" but found out that I couldn't remove it again.. This annoyed me and I decided to make a clone of the "panel 1" and just adding everything manual. I deleted panel 1, and later found out that PowerManagement and the wireless network connection icon was lost.. and I can't figure how to get them back.. :confused::confused:

Add the "Notification Area".

> **ptuy said:**
> **2:**I surfed the Internet and found this tiny little Idesk application. I installed, made a .idesktop folder inside my HOME directory. I made a file called chrome.lnk - inside this file I put the following, but i doesn't show any Google Chrome icon on the desktop.  ](*,):^o

[B] table Icon
    Caption: Google Chrome
    ToolTip.Caption: Run Chrome
    Command: google-chrome
    Icon: usr/share/icons/hicolor/16x16/apps/google-chrome.png
    Width: 600
    Height: 700
    X: 30
    Y: 20
  end[/B]

Regards Rasmus - who looooooves linux!

I haven't used xfce in a couple of weeks, but I recall that there is an option somewhere that lets you determine what shows up on the desktop.  If you have it set to be blank, then nothing will show despite what other programs try to do (probably).  I'll log in to xfce later today to find out, but right now, I have to be going.

> **ptuy said:**
> Thank you! :) I could have googled that, silly me!

How do I access the internet when the network manager is gone in panel 1? Please help!

See above.

---

### Post by ptuy on 2010-04-26
> **SnickerSnack said:**
> Add the "Notification Area".

Thank you.. I've searched for hours now on google.. I right click my top panel -> click "add to panel" -> looking for notication area, but really can't find it anywhere.. Remember, I deleted the original panel with the notification area enabled, and then added a new panel and manually added stuff so it looked like the old panel.
But as said before I can't find the "notification area" in the "add to panel" window..

I also tried deleting the systray file in home/me/.config/xfce4/panel folder.
Like this guy sais: [http://ubuntuforums.org/showthread.php?t=1176238]("http://ubuntuforums.org/showthread.php?t=1176238")

I read this topic, with no luck!:
[http://forum.xfce.org/index.php?topic=3504.0]("http://forum.xfce.org/index.php?topic=3504.0")

And this guy has the same problem as me, except he is able to find the notification area in "add to panel"..
[http://ubuntuforums.org/showthread.php?t=376080]("http://ubuntuforums.org/showthread.php?t=376080")

Heeeelp, this is frustrating!

---

### Post by ptuy on 2010-04-26
Don't worry, I'm about making a fresh install..

Thanks for the help!

---

