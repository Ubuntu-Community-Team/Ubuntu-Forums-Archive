---
title: "nm-applet won't show"
date: 2011-01-20
forum: General Help
---

### Post by Dr Small on 2011-01-20
Greetings,
I am running an old version of Ubuntu (9.04) on this laptop, but that shouldn't matter for this problem. Besides that, I have **2** (two) users on this system, both with administrative (sudo) permissions.

I have the first account (megan) logged in and the network manager applet shows in the notification bar. I log into my account (drsmall) and the nm-applet _does **not** show_ in my notification area.

System > Preferences > Startup Applications shows that Network Manager (nm-applet --sm-disable) is checked to run at startup, yet it doesn't. When I try running the command in the terminal, I get this response:

```
$ nm-applet --nm-disable

** (nm-applet:13551): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3
```

Any idea how to fix this? I would preferably like to be able to have the network applet show up on both accounts, while both accounts are signed in.

Dr Small

---

### Post by Ex_Machina on 2011-01-20
As root try:
/etc/init.d/networking restart

---

### Post by Dr Small on 2011-01-20
> **Ex_Machina said:**
> As root try:
/etc/init.d/networking restart
Tried, and it didn't help.

---

