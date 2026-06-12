---
title: "Login Window Lost"
date: 2012-03-21
forum: General Help
---

### Post by Cambyses on 2012-03-21
Hello Everyone...

I've downloaded a new skin for Login Window so I use terminal to set the skin, but after rebooting, I couldn't see any Login Window!!!! Just Background being loaded and I hear the Login Sound but Now window appear to choose my user and enter my password!!!

The command was:

sudo cp /PATH/Earth.desktop /usr/share/gdm/autostart/LoginWindow
sudo unlink /usr/share/gdm/autostart/LoginWindow/Earth.desktop

I'm also new with Linux and I can't stand Microsoft Windows anymore...
I would appreciate any help...

---

### Post by raja.genupula on 2012-03-21
[http://ubuntuforums.org/showthread.php?t=1420021](http://ubuntuforums.org/showthread.php?t=1420021)

[http://www.linuxquestions.org/questions/linux-newbie-8/lost-login-screen-on-ubuntu-10-04-a-876782/](http://www.linuxquestions.org/questions/linux-newbie-8/lost-login-screen-on-ubuntu-10-04-a-876782/)

---

### Post by Cambyses on 2012-03-21
Sorry I didn't find the thread with this problem, this is why I made this thread...
Thanks for useful links...I could learn some other things. But unfortunately the tips couldn't solve my problem.

The following command:
```

sudo /etc/init.d/gdm restart

```It did "restart" but nothing happen & Login Window has not appeared.

But probably same error being showed by running 2 following commands:
```

sudo /etc/init.d/gdm stop
startx

```and,
```

sudo dpkg-reconfigure -phigh xserver-xorg

```Both show same error:
> 
No Protocol Specified.
Cannot open display:
Also executing:
```

gnome-control-center

```Shows same error.

---

