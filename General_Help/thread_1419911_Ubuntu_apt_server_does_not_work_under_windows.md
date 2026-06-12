---
title: "Ubuntu apt server does not work under windows"
date: 2010-03-02
forum: General Help
---

### Post by CyberJacob on 2010-03-02
for some strange reason the ubuntu apt server will not work on windows, i am trying to access it via http ([http://apt.ubuntu.com/p/lightyears](http://apt.ubuntu.com/p/lightyears)) becuase my ubuntu pc does not work with my either of my wireless cards, any idea why you cant get onto in under windows or how i could get onto it as i would like to install quite a lot of software? the only pc i have connected to the internet is an acer laptop running windows vista and internet explorer 8

---

### Post by pastalavista on 2010-03-02
Apt and apturl are linux applications and won't work with Windows. To download Ubuntu packages on Windows, use the package search for your distro from this page:

[http://packages.ubuntu.com/]("http://packages.ubuntu.com/")

Lightyears is [HERE]("http://packages.ubuntu.com/lucid/games/lightyears")

edit: The lightyears link is for the Lucid (10.04) alpha release. You don't say what version you're running. Just replace "lucid" in the URL with "karmic" or "jaunty" or whatever you use.

---

### Post by darolu on 2010-03-02
Weird, they seem to have put a filter so only browsers identifying themselves as "Ubuntu" can access it, the weird part is, I'm using Ubuntu and can't get it either, I get "You don't seem to be running Ubuntu" message. I am using Chromium (from daily builds ppa), I also tried with Epiphany (installed from repos) and same result, so it seems like you can only access with the default Firefox browser.

Anyways, you won't be able to access that website running Windows, and even if you could it would be completely useless as it attempts to download and install a package.

---

### Post by CyberJacob on 2010-03-02
what i was going to do was save the packages onto a memory stick and then transfer them onto my ubuntu pc and install them. thanks for the link though

---

