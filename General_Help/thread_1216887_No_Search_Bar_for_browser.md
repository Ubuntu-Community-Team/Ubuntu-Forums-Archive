---
title: "No Search Bar for browser"
date: 2009-07-18
forum: General Help
---

### Post by Ratcage on 2009-07-18
Hey guys I have a Ubunto release 9.04 (jaunty)
 Kernel Linux 2.6.28-13-generic
Gnome 2.26.1 \
--------------------------------------------------------
So, I start my firefox web browser and theres no search bar at the top.
Here's a screenshot: /home/dominique/Desktop/Screenshot-1.png

So I was wondering If you guys could help.
I appreciate any help.:)

---

### Post by master_kernel on 2009-07-18
Might want to fix that link first.

---

### Post by Ratcage on 2009-07-18
Oh sorry about that.

---

### Post by LightningCrash on 2009-07-18
Try right-clicking on the empty space next to the Help menu, go to Customize, then drag Search Bar over where you want it.

---

### Post by Ratcage on 2009-07-18
I'm trying to upload a screenshot but i don't know how to for this thread any help?

---

### Post by master_kernel on 2009-07-18
Quick Reply > Go Advanced > Scroll down to manage attachments > Profit.

---

### Post by Ratcage on 2009-07-18
[ATTACH]121568[/ATTACH]

There it is no web bar.

---

### Post by master_kernel on 2009-07-18
I reproduced it. Go to View > Toolbars > and check Navigation Toolbar.

---

### Post by Ratcage on 2009-07-18
Oh thanks alot do you know how that happened?

---

### Post by master_kernel on 2009-07-18
Did you visit any pages before this happened?

Edit: malicious sites could use the 'goToggleToolbar('nav-bar','');' javascript function and set it to a well used key on your keyboard to get you to toggle it off.

---

