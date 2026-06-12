---
title: "firefox menubar lost"
date: 2011-10-02
forum: General Help
---

### Post by CryptKeeper777 on 2011-10-02
I lost the menubars in all programs! At first I thought it was only a Firefox problem (when I started the thread, BTW), but then I recognized that also the other programs have lost their menubars!

---

### Post by dodle on 2011-10-02
Try right-clicking on the tab bar where you don't have a tab open.

---

### Post by CryptKeeper777 on 2011-10-02
> **dodle said:**
> Try right-clicking on the tab bar where you don't have a tab open.
I did try that. But actually, you've just been a little bit too fast with your answer since I just discovered that it's a system wide problem, also Thunderbird, Thunar etc. have lost their menubars!

---

### Post by dodle on 2011-10-02
Are you using Gnome? There may be a setting in gconf. Try using gconf-editor and see if you can find something.

---

### Post by CryptKeeper777 on 2011-10-02
I'm running Xubuntu 11.04, so not Gnome, but Xfce4.

---

### Post by CryptKeeper777 on 2011-10-02
Alright, problem solved. I recently installed unity (sudo apt-get install unity) to give it another shot, and that wasn't a really good idea... It seems to have installed globalmenu packages for Firefox and Thunderbird. I've removed those packages, and now the menus are back.

The problem left is that the menu of Thunar (the file manager) is still lost, and there's no "globalmenu" package left... BTW I've already done "sudo apt-get remove unity" and "sudo apt-get autoremove".

But maybe I should open a new thread on how to fully remove the changes made by trying to install unity...

---

