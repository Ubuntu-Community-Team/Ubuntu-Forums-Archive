---
title: "login screen Q"
date: 2010-07-17
forum: General Help
---

### Post by tneva82 on 2010-07-17
Just minor one but seems that from 9.10 ahead login screen works so that you choose user with mouse and then type in password like in windows.

Fair enough and helpful for most of the people I suppose but for me I type on so fast this actually _slows_ me down on login process when I have to move hand from keyboard to mouse and then back :D I would much prefer simply being able to TYPE the username like in 9.04.

Is there any setting with which I could switch it back?

Yeah very minor issue but figured might just as well ask.

---

### Post by sisco311 on 2010-07-17
Disable the face browser: 
```
sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list true
```

Enable the face browser: 
```
sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list false
```

---

### Post by dullard on 2010-07-17
Still using 8.04 here, so this might not work...

...but have you tried hitting the tab key? I suspect that would highlight and cycle through each user, followed by hitting the enter key to select?

---

