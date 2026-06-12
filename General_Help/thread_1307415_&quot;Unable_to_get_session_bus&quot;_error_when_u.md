---
title: "&quot;Unable to get session bus&quot; error when using notify-send"
date: 2009-10-31
forum: General Help
---

### Post by abcuser on 2009-10-31
Hi,
on Xubuntu 9.04 I have installed notify-send (sudo apt-get install libnotify-bin).

I need to run some script with root privileges and when script finished I would like to notify user with notification.

I log in with user which does not have root privilege (sudo does not work):
```

notify-send "hello world"

```
is executed from Terminal with normal user and it works fine.

But if I am still logged in with normal user and trying to execute code with sudo/root user:
```

su - *my_sudo_user*
sudo notify-send "hellow world"

```
I get error:
Unable to get session bus: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.

It is probably some permissions problem.

How to solve this problem in such a way, that bash script running in background could send notifications to normal-non-root user?
Thanks

---

