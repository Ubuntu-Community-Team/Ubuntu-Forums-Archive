---
title: "System Monitor"
date: 2011-12-11
forum: General Help
---

### Post by krellmk on 2011-12-11
Can't get System Monitor a to stay open after a few updates and changes in 11.10.. when i try to open system Monitor all it does is flash on the screen and close

---

### Post by lechien73 on 2011-12-11
Sometimes if you try run it from a terminal window, you can see the error messages that are stopping it from running correctly.

Open a terminal window and type:

```
gnome-system-monitor
```

and see if any errors are reported in the terminal window.

---

### Post by krellmk on 2011-12-11
i get this if i run it in terminal..

mike@mike-Ubuntu:~$ gnome-system-monitor

** (gnome-system-monitor:12476): WARNING **: SELinux was found but is not enabled.

terminate called after throwing an instance of 'Gio::Error'
Aborted

---

### Post by lechien73 on 2011-12-11
Have you changed or updated the theme recently?

Perhaps you could run:

```
strace gnome-system-monitor
```

and post the last few lines of output here. Does it mention anything about [FONT="Courier New"]ENOENT (No such file or directory)[/FONT]

---

### Post by BC59 on 2011-12-11
Looks like a bug. Look here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/180087](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/180087)

It has a workaround installing SELinux
```
sudo apt-get install selinux
```

or trying to find which icon you altered and was produced the bug.

---

### Post by krellmk on 2011-12-11
Did all the above still the same

---

### Post by BC59 on 2011-12-11
Did you change an icon on /usr/share/pixmaps/ directory?

---

### Post by krellmk on 2011-12-11
I did this..

gconftool-2 --set "/apps/metacity/general/button_layout" --type string "close,minimize,maximize:"

sudo apt-get purge liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 overlay-scrollbar

---

### Post by BC59 on 2011-12-11
You used this to delete the overlay scrollbars:

> sudo apt-get purge liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0 overlay-scrollbar

Maybe you should try to restore them:

```
sudo apt-get install overlay-scrollbar liboverlay-scrollbar3-0.2-0 liboverlay-scrollbar-0.2-0
```

and then check if is this the problem.

---

### Post by lechien73 on 2011-12-11
It looks like it could be similar to [this bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/351754"). That's why I was wondering about the strace output.

You could try some of the workarounds at that link, though.

---

### Post by krellmk on 2011-12-11
Funny thing happen if i have Nicotine running then System Monitor won't open but if i close Nicotine System Monitor will work.

---

