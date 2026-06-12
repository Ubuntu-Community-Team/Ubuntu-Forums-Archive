---
title: "xgl/compiz - no extra right click menu options??"
date: 2006-06-17
forum: General Help
---

### Post by jms830 on 2006-06-17
I recently did the update of xgl/compiz along with the newest kernel update, but for some reason now my menus when i right click on the top bar of any window there is no longer an option to move the window to another workspace or to set the opacity/brightness/saturation.  It only has the basic move, minimize, maximize, resize, and close. Also, when I scroll my mousewheel on the desktop it no longer rotates workspaces.  How can I investigate this problem? Anyone else experience this? I tried rebooting several times, it still didn't fix it.  I thought to uninstall compiz and then reinstall it but I'm not quite sure how to do that.

---

### Post by zgerrz on 2006-06-17
[QUOTE=jms830]I recently did the update of xgl/compiz along with the newest kernel update, but for some reason now my menus when i right click on the top bar of any window there is no longer an option to move the window to another workspace or to set the opacity/brightness/saturation.  It only has the basic move, minimize, maximize, resize, and close. Also, when I scroll my mousewheel on the desktop it no longer rotates workspaces.  How can I investigate this problem? Anyone else experience this? I tried rebooting several times, it still didn't fix it.  I thought to uninstall compiz and then reinstall it but I'm not quite sure how to do that.[/QUOTE]


I can confirm your first error that you are experiencing about windows no longer having the "advanced" options. I only get the basic functions now that I am fully upgraded. However, I can still scroll through workspaces with my mouse at the edge of my screen.

Just thought I'd confirm this issue in hopes of bringing some attention to this situation.

---

### Post by jms830 on 2006-06-17
yes I actually reinstalled compiz and my desktop rotation by mousewheel is working again, but the advanced options are still gone

---

### Post by zgerrz on 2006-06-17
[QUOTE=jms830]yes I actually reinstalled compiz and my desktop rotation by mousewheel is working again, but the advanced options are still gone[/QUOTE]

I'm going to take a guess here and say that the recent Gnome updates that we got have interfered with compiz/xgl, and most likely the fix will have to come from Quinn when he releases newer packages for compiz/xgl. Are you using Quinn's repo like I am to get the latest compiz/xgl?

---

### Post by jms830 on 2006-06-17
yes I am using quinn's repo as well

---

### Post by zgerrz on 2006-06-17
If this is strictly a compiz/xgl issue, then I'll bet Quinn will have it fixed in the next update. At this time I can't find the compiz forums related to his packages to check if someone has already posted this issue there. More than likely a fix is already in the works though.

---

### Post by jms830 on 2006-06-17
the forums are right at this site in case you want to look around, I am as well.  [http://www.compiz.net/](http://www.compiz.net/)

EDIT: progress here [http://www.compiz.net/viewtopic.php?id=1295](http://www.compiz.net/viewtopic.php?id=1295) but I can't find either of the packages listed in the repos

---

### Post by reclusivemonkey on 2006-06-17
[QUOTE=zgerrz]I'm going to take a guess here and say that the recent Gnome updates that we got have interfered with compiz/xgl, and most likely the fix will have to come from Quinn when **he** releases newer packages for compiz/xgl. Are you using Quinn's repo like I am to get the latest compiz/xgl?[/QUOTE]

QuinnStorm is actually female. Let's give the ladies of linux some credit eh? ;-)

---

### Post by panurge77 on 2006-06-17
You need quinns version of libwnck18 and libwnck-common. If you tell synaptic to use the previous version it should work. I'll wait for quinn to patch it again ;)

---

### Post by jms830 on 2006-06-17
how can i tell synaptic to use the old versions? and can I easily tell it to use the newer ones again?

---

### Post by panurge77 on 2006-06-17
search the packages, click on it and choose packages > force version on the menu bar. yes, you can always come back to the latest

---

### Post by jms830 on 2006-06-17
Ok, I downgraded and the Always in Viewport, Move to Viewport, and On Top menu items are back, but I still don't have opacity/brightness/saturation options

---

### Post by panurge77 on 2006-06-17
Shortcuts are easier, anyway ;)
alt-wheel
ctrl-wheel

---

### Post by zgerrz on 2006-06-17
[QUOTE=reclusivemonkey]QuinnStorm is actually female. Let's give the ladies of linux some credit eh? ;-)[/QUOTE]

Bah! I had a feeling Quinn was actually a girl but was just too lazy to check up on that. Always nice to have ladies in Linux :D

---

### Post by purfier on 2006-06-17
10x for this post, I have the same problem and it made me crazy:P

---

### Post by purfier on 2006-06-17
[QUOTE=panurge77]You need quinns version of libwnck18 and libwnck-common. If you tell synaptic to use the previous version it should work. I'll wait for quinn to patch it again ;)[/QUOTE]

I did try this... Now the scroll dont work, now menu's and shift+ctrl+alt+keypad does not work....

---

