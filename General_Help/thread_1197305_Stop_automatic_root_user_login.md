---
title: "Stop automatic root user login"
date: 2009-06-25
forum: General Help
---

### Post by jaems-kun on 2009-06-25
This is probably a stupid question, but it's a tough query to do a search for.

I'm making a custom xubuntu experience on a usb drive for my young nephews.  I followed the instructions via [http://www.pendrivelinux.com/usb-xubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-xubuntu-904-persistent-install-windows/) and so far it's all gone swimmingly.

One small hang up, however, when I boot from usb drive xubuntu automatically logs me in as the root user.  I've set up another account I'd like the kids to use so that they can't mess around with the settings too much, but it's kind of pointless if I can't stop the system from booting in root mode. 

Is there a way I can work around this or is this just a drawback to using usb persistent installation?

Thanks in advance.

---

### Post by jake16424 on 2009-06-26
its a persistance install, you select it from the boot menue and you *if you made the account* should be able to log on as said user.

if not then persistance isn't saving the info, 

not entirely sure how to stop root logon =\

---

### Post by jaems-kun on 2009-06-26
Prior to my first login, I've never manually made an account, though.  

I click "run xubuntu perssistently" and it automatically logs me in as root.

Now I have made a second account that I want my nephews to be able to use.  I'd like this to be the account which automatically starts up when xubuntu is run.  But as it is right now, I press "run xubuntu" and it automatically starts up in root.  From there I have to log out, then it will take me to a login screen where I can manually enter the account I want.

Thanks for your help.

---

### Post by jaems-kun on 2009-07-03
Bump?

So if I can assume that my automatic log-in transfer is impossible for me... is there a way I can at least hide/delete that "install" icon that seems to be permanently adhered to the desktop?

---

### Post by DeMus on 2009-07-03
> **jaems-kun said:**
> Bump?

So if I can assume that my automatic log-in transfer is impossible for me... is there a way I can at least hide/delete that "install" icon that seems to be permanently adhered to the desktop?

Isn't it possible to make an install in which you do make a user account during installation, like you would when you are installing Ubuntu normally on a HD?

Then this account is a normal user account, but by using the given password (during installation also) it will get privileged rights to perform root tasks.

---

### Post by jaems-kun on 2009-07-03
I would assume so, however the way I did this (via the instructions at pendrivelinux) didn't give me any account options, everything was done automatically.  Unfortunately I'm not experienced enough to experiment with install methods without specific instructions.

---

### Post by dcstar on 2009-07-03
> **jaems-kun said:**
> This is probably a stupid question, but it's a tough query to do a search for.

I'm making a custom xubuntu experience on a usb drive for my young nephews.  I followed the instructions via [http://www.pendrivelinux.com/usb-xubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-xubuntu-904-persistent-install-windows/) and so far it's all gone swimmingly.

One small hang up, however, when I boot from usb drive xubuntu automatically logs me in as the root user.  I've set up another account I'd like the kids to use so that they can't mess around with the settings too much, but it's kind of pointless if I can't stop the system from booting in root mode. 

Is there a way I can work around this or is this just a drawback to using usb persistent installation?

Thanks in advance.

Try removing the automatic login setting: System-Administration-Login Window

---

### Post by JKyleOKC on 2009-07-03
> **dcstar said:**
> Try removing the automatic login setting: System-Administration-Login Window

For Xubuntu, it's Settings>>Login Window>>Security tab to control automatic login; on that tab you can specify the user to log in automatically. I don't know if this conflicts with the "run persistently" settings but it works as expected on all of my Xubuntu boxes (four of them)...

---

### Post by jaems-kun on 2009-07-04
Perfect!  That's what I was looking for, thank you so much!

---

