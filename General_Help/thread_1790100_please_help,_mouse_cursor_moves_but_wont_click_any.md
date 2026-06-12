---
title: "please help, mouse cursor moves but wont click anything! have important files unsaved"
date: 2011-06-24
forum: General Help
---

### Post by fuzzylogic25 on 2011-06-24
Hi,

Basically, i had a bunch of documents opened and i saved one txt file. I then clicked it and dragged it to the recycle bin slowly but didnt release the button. Then the cursor just stayed like that. The cursor changed image while i was dragging it. It now remains as that image for the cursor. I can move it around but cannot click anything. If i press Alt Tab to switch to another window, it just highlights that file. I cant move about on the desktop either.

What do i do? im really worried i wont be able to save my work. please help. would be greatly appreciated!

---

### Post by lisati on 2011-06-24
Are you using a laptop? I occasionally experience a similar effect, and find that using the laptop's touchpad to minimize and then maximize a window is one workaround that seems to help.

---

### Post by fuzzylogic25 on 2011-06-24
I figured out the problem. It relates to this issue:

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/660222](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/660222)

This happens not just for totem. It seems to be an issue when we drag and drop files and hold it for a while without dropping the file.

I fixed it by switching to tty console and terminating nautilus. Then switched back to gnome.

BUT, why did this happen? Is this a problem others are experiencing? This has happened several times to me actually. I can reproduce it too!

---

