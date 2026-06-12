---
title: "Issue involving a missing part of my top panel"
date: 2010-02-24
forum: General Help
---

### Post by icthis3t7 on 2010-02-24
I'm relatively new to Ubuntu, but I'm not a completely helpless guy haha. However, I've done something and cannot figure out how to fix it.

Somehow, during my messing around, I notice that my username isn't in the top right part of my panel. This is what I've always used to log off/shutdown/restart/etc. Yes, I know I can use simple, 1 click alternatives, but I like the way it looks (plus I'm a slight control freak, hence my customizing of the GRUB2 menu haha).

So, I've even used terminal to reset the panels to default...

> 
$ gconftool-2 --shutdown
$ rm -rf .gconf/apps/panel
$ pkill gnome-panel


But this did not fix my problem either.

I've attached below a screenshot to help visually show you what I'm talking about.

[IMG]http://img718.imageshack.us/img718/1026/screenshot1bu.th.png[/IMG]

Thanks in advance! :D

EDIT: direct link to pic [http://img718.imageshack.us/img718/1026/screenshot1bu.png]("http://img718.imageshack.us/img718/1026/screenshot1bu.png")

---

### Post by Agent Smith on 2010-02-25
You need to right click the top panel and choose add to panel. You will then get a list of things you can add to it, such as kill apllication , shutdown icon etc. The one your missing will be listed also.

---

### Post by icthis3t7 on 2010-02-25
> **Agent Smith said:**
> You need to right click the top panel and choose add to panel. You will then get a list of things you can add to it, such as kill apllication , shutdown icon etc. The one your missing will be listed also.

I have done this, but cannot find the right panel option.

[Look at me!]("http://www.linuxforu.com/wp-content/uploads/2009/12/01-The-GNOME-Desktop.png")

The top right of this screenshot is what I'm talking about!

---

### Post by Jackzor on 2010-02-25
Indicator Applet Session

Add that.

---

### Post by plucky on 2010-02-25
> **icthis3t7 said:**
> I have done this, but cannot find the right panel option.

[Look at me!]("http://www.linuxforu.com/wp-content/uploads/2009/12/01-The-GNOME-Desktop.png")

The top right of this screenshot is what I'm talking about!

**Indicator Applet Session** is what it is called.

Good Luck

---

### Post by Jackzor on 2010-02-25
> **plucky said:**
> **Indicator Applet Session** is what it is called.

Good Luck

I beat you :D:D

---

### Post by icthis3t7 on 2010-02-25
> **plucky said:**
> **Indicator Applet Session** is what it is called.

Good Luck

Alright, how do I get that back on the panel? I've done quite a bit of searching and still can't figure it out. I've tried a custom panel loader, using terminal.. I'm lost! :confused:

---

### Post by Jackzor on 2010-02-25
Right click the panel on a blank space and click add to panel Then the window I have in the screenshot will come up. Add what I have selected.

---

### Post by icthis3t7 on 2010-02-25
Well, it turns out that the Indicator Applet Session is not installed by default! After going to Synaptic, I found it, installed it, logged off and back on and vola! I can add it onto my panel! Thanks for your help! :D

I'm still not quite sure why it disappeared or how it was even able to exist before I installed it via Synaptic!! :confused:

Anyway, its working! Now to go back and re-customize the panel. :popcorn:

---

