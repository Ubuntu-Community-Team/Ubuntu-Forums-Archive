---
title: "Laptop screen garbled when no external monitor plugged in."
date: 2012-02-26
forum: General Help
---

### Post by paulig2001 on 2012-02-26
This is very strange, my normal setup at work is I have my external monitor plugged into my laptop, with my Ubuntu desktop extended onto the external monitor. 

However recently when I boot into Ubuntu with no external monitor plugged in, my screen is garbled (See attached photo).

There seems to be an error message being printed but I can't read it! Any ideas!?

---

### Post by MacDaddy1660B on 2012-02-26
Sorry, I don't have any fixes for you, but I am having what may be a related problem. My screen garbles intermittently and my laptop locks up. If I cut the power, the problem doesn't go away. The screen will garble up again and freeze upon reboot. I must go through several power cycles to get the problem to clear. I get nothing from log files.

It happened after I installed the following programs (taken from /var/log/dpkg.log)

```
2012-02-23 07:27:02 startup archives unpack
2012-02-23 07:27:06 upgrade jockey-gtk 0.9.4-0ubuntu10 0.9.4-0ubuntu10.1
2012-02-23 07:27:06 status half-configured jockey-gtk 0.9.4-0ubuntu10
2012-02-23 07:27:06 status unpacked jockey-gtk 0.9.4-0ubuntu10
2012-02-23 07:27:06 status half-installed jockey-gtk 0.9.4-0ubuntu10
2012-02-23 07:27:06 status triggers-pending bamfdaemon 0.2.104-0ubuntu1.1
2012-02-23 07:27:07 status half-installed jockey-gtk 0.9.4-0ubuntu10
2012-02-23 07:27:07 status triggers-pending desktop-file-utils 0.18-0ubuntu9
2012-02-23 07:27:07 status half-installed jockey-gtk 0.9.4-0ubuntu10
2012-02-23 07:27:07 status triggers-pending gnome-menus 3.2.0-0ubuntu2
2012-02-23 07:27:07 status half-installed jockey-gtk 0.9.4-0ubuntu10
2012-02-23 07:27:08 status half-installed jockey-gtk 0.9.4-0ubuntu10
2012-02-23 07:27:08 status unpacked jockey-gtk 0.9.4-0ubuntu10.1
2012-02-23 07:27:08 status unpacked jockey-gtk 0.9.4-0ubuntu10.1
2012-02-23 07:27:09 upgrade jockey-common 0.9.4-0ubuntu10 0.9.4-0ubuntu10.1
2012-02-23 07:27:09 status half-configured jockey-common 0.9.4-0ubuntu10
2012-02-23 07:27:09 status unpacked jockey-common 0.9.4-0ubuntu10
2012-02-23 07:27:09 status half-installed jockey-common 0.9.4-0ubuntu10
2012-02-23 07:27:09 status triggers-pending hicolor-icon-theme 0.12-1ubuntu1
2012-02-23 07:27:09 status half-installed jockey-common 0.9.4-0ubuntu10
2012-02-23 07:27:10 status half-installed jockey-common 0.9.4-0ubuntu10
2012-02-23 07:27:10 status unpacked jockey-common 0.9.4-0ubuntu10.1
2012-02-23 07:27:10 status unpacked jockey-common 0.9.4-0ubuntu10.1
2012-02-23 07:27:10 trigproc bamfdaemon 0.2.104-0ubuntu1.1 0.2.104-0ubuntu1.1
2012-02-23 07:27:10 status half-configured bamfdaemon 0.2.104-0ubuntu1.1
2012-02-23 07:27:10 status installed bamfdaemon 0.2.104-0ubuntu1.1
2012-02-23 07:27:10 trigproc desktop-file-utils 0.18-0ubuntu9 0.18-0ubuntu9
2012-02-23 07:27:10 status half-configured desktop-file-utils 0.18-0ubuntu9
2012-02-23 07:27:10 status installed desktop-file-utils 0.18-0ubuntu9
2012-02-23 07:27:11 trigproc gnome-menus 3.2.0-0ubuntu2 3.2.0-0ubuntu2
2012-02-23 07:27:11 status half-configured gnome-menus 3.2.0-0ubuntu2
2012-02-23 07:27:11 status installed gnome-menus 3.2.0-0ubuntu2
2012-02-23 07:27:11 trigproc hicolor-icon-theme 0.12-1ubuntu1 0.12-1ubuntu1
2012-02-23 07:27:11 status half-configured hicolor-icon-theme 0.12-1ubuntu1
2012-02-23 07:27:17 status installed hicolor-icon-theme 0.12-1ubuntu1
2012-02-23 07:27:17 startup packages configure
2012-02-23 07:27:17 configure jockey-common 0.9.4-0ubuntu10.1 <none>
2012-02-23 07:27:17 status unpacked jockey-common 0.9.4-0ubuntu10.1
2012-02-23 07:27:18 status unpacked jockey-common 0.9.4-0ubuntu10.1
2012-02-23 07:27:18 status unpacked jockey-common 0.9.4-0ubuntu10.1
2012-02-23 07:27:18 status half-configured jockey-common 0.9.4-0ubuntu10.1
2012-02-23 07:27:19 status installed jockey-common 0.9.4-0ubuntu10.1
2012-02-23 07:27:19 configure jockey-gtk 0.9.4-0ubuntu10.1 <none>
2012-02-23 07:27:19 status unpacked jockey-gtk 0.9.4-0ubuntu10.1
2012-02-23 07:27:19 status unpacked jockey-gtk 0.9.4-0ubuntu10.1
2012-02-23 07:27:20 status half-configured jockey-gtk 0.9.4-0ubuntu10.1
2012-02-23 07:27:20 status installed jockey-gtk 0.9.4-0ubuntu10.1
```

I'm hoping that this problem is related and that we may figure something out.

---

