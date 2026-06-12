---
title: "Remote logoff script in windows"
date: 2009-07-02
forum: General Help
---

### Post by Keithamus on 2009-07-02
At work I have installed two Xubuntu kiosk machines. They're for use for Internet, and I've locked them down quite tightly. When the user logs off (into gdm, and the timed login kicks in and subsequently logs them in) all the user data is wiped and a fresh "account" is made. It works really well, but its a pain to have to manually go to the machine and log it out each time a user doesn't. Right now I have setup Putty on a windows machine which sits on the counter, so I remotely log off both machines by signing into ssh, but this is pretty much as much effort as walking over to the machines.

What I really want is an icon sitting on the Windows desktop, which I could just double click and it could tell the Xubuntu machines to log off back to gdm. So when a customer is finished with the internet, I can double click the icon and reset the accounts for the next user.

Is there any way to do this?

---

### Post by Keithamus on 2009-07-06
I've gotten quite close, but it still isn't working. On the windows PC I have a "logout.sh" which contains:

```

`xfce4-session-logout --logout --fast --display=:0 > logout.log`

```

I have a shortcut on the desktop which has:

```

"C:\Program Files\PuTTY\putty.exe" -load Xubuntu -m "C:\Program Files\PuTTY\logout.sh"

```

When I double click the shortcut I get the following error on the Xubuntu machine:

```

Unable to contact D-Bus session bus

dbus-launch failed to autolaunch D-Bus session:
Autolaunch error: X11 Initialization failed.

```

I should say, I can use putty to SSH to the PC, and manually run the command, and it runs absolutely fine. Any ideas?

---

### Post by Keithamus on 2009-07-06
Sussed it!

Added export DESKTOP=:0 to the beginning of the file, so logout.sh now reads:

```
`export DISPLAY=:0 && xfce4-session-logout --logout --fast --display=:0 > logout.log`
```

This works fully, so I double click the icon and the machine logs out.

---

