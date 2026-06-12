---
title: "Latest flashplayer installed but not working in FF"
date: 2009-07-30
forum: General Help
---

### Post by artanyon on 2009-07-30
Hi.  This is my first post so I hope it goes well.

I have searched this problem and can't find the answer so I hope somebody can help me.  I have only recently converted to Ubuntu from Vista.  This is my first ever experience with Linux.  So far I have loved it but for some reason I can't get flash to work.  I have installed and reinstalled the latest update from Adobe.  I have done it myself and had the OS do it.  I have searched and installed every update and flash player in the synaptic package manager.  However, every site I try (youtube, hulu, addicting games,...) won't play.  It either says I have to install the latest player (maddening!!!!) or I don't have javascript turned on.  I'm pretty sure I do.  

Sometimes an arrow will appear to start flash but when I click it the entire window disappears like it had been "cut" to be pasted elsewhere.

I hope there hasn't been pages upon pages discussing the problem I just couldn't find it.

Please help a newb.

---

### Post by hyperAura on 2009-07-30
[http://www.cyberciti.biz/tips/linux-install-flash-player-10.html](http://www.cyberciti.biz/tips/linux-install-flash-player-10.html)

go on this page and follow the method #2.. it should solve ur problem..

---

### Post by artanyon on 2009-07-30
I just ran through #2 twice and nothing has changed.  Still no flash.

---

### Post by Arup on 2009-07-30
untar the flashplayer in your home folder, from terminal, do a sudo mv libflashplayer.so /usr/lib/mozilla/plugins

It should work fine. Remove the ./mozilla folder in your home folder.

---

