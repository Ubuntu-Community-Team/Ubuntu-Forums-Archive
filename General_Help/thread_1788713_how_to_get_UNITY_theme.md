---
title: "how to get UNITY theme"
date: 2011-06-23
forum: General Help
---

### Post by sravan008 on 2011-06-23
Recently i installed ubuntu 11.04 through virtual box , i didnt get the unity theme after it was installed it , and i searched for  drivers to my graphics card  but i couldn't get any drivers , can  any one have suggestions to solve this prob .

---

### Post by gyussz on 2011-06-23
Virtualbox needs the Guest Additions installed for 3D applications or features. From the menu: Devices -> Install Guest Additions. This will download and install the quest additions. After 1-2 reboots (sometimes it fails the first time) unity should be active.

Also make sure the 3D acceleration is enabled in the Virtual computer preferences (virtualbox main window). To enable this, or modify every settings the Guest OS should be turned off.

---

### Post by sravan008 on 2011-06-28
i will try it once and get back to you in shortly.:)

---

### Post by sravan008 on 2011-06-28
thanks alot dude .. its working but too slow :( any tweaks ??

---

### Post by sravan008 on 2011-06-29
can any one help me out in this ??

---

### Post by sravan008 on 2011-06-29
any one is ther ???:confused:

---

### Post by NERDMAN! on 2011-06-29
if your working with virtualbox, it might be an idea to up the resource allocation for the guest os. you can do this in the settings dialog. ive personally found unity requires a fair decent amount of graphics memory, i'd give it at least 128mb to be on the safe side, also it may be an idea to give it 1024mb of normal ram to play with if you have enough spare.
if its still slow after that then the issue is likely unity itself being slower than gnome.
hope that helps.

---

