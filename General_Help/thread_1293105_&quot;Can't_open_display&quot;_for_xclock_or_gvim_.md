---
title: "&quot;Can't open display&quot; for xclock or gvim on kubuntu root shell konsole 1.6.6"
date: 2009-10-16
forum: General Help
---

### Post by tsanchung on 2009-10-16
I use kubuntu 8.04.
"gvim", "sudo gvim", "xclock" and "sudo xclock" are all running ok on a non-root shell on konsole.
$ gvim
$ sudo gvim /etc/fstab
[sudo] password for ts:

$ xclock
$ sudo xclock
[sudo] password for ts:

However, starting xclock or gvim on root shell on konsole has the "Can't open display" error appears.
# DISPLAY=localhost:0.0
# xclock
Error: Can't open display: localhost:0.0
# gvim /etc/fstab
E233: cannot open display
Press ENTER or type command to continue

# DISPLAY=:0.0
# xclock
Invalid MIT-MAGIC-COOKIE-1 keyError: Can't open display: :0.0
# DISPLAY=:0
# xclock
Invalid MIT-MAGIC-COOKIE-1 keyError: Can't open display: :0

I did this at regular user's shell.
$ xhost +localhost
localhost being added to access control list

Then try starting xclock or gvim at the root shell.
However, the same problem exists.

---

### Post by Rocket2DMn on 2009-10-16
With a root shell, you aren't sharing a session with your graphical login like you are with sudo, so the shell doesn't know about X.  This is the same behavior as if you tried to run a graphical application from a tty.  Is there a particular reason you are trying to run these apps from a root shell, or that you have a root account enabled to begin with?

---

### Post by Giblet5 on 2009-10-16
That's because xhost authentication prevents another user from opening windows on your desktop (or grabbing your key strokes), locally or via remote.

If other (simultaneous) local and other LAN users are not an issue, you can open up your X server via the following. (WARNING: You are wide open at this point. Very dangerous.)
```
xhost +
```

Read the man page ```
man 1 xhost
``` for more info, or grab Volume 3 of the "The X Window System" over on O'Reilly's web (free and very useful).

---

### Post by Giblet5 on 2009-10-16
Read up on xauth and xhost.

It's worth the effort. X is incredibly powerful as compared with other GDIs, but you can really stomp the snot out of yourself with it if you aren't careful.


My previous recommendation is EXTREMELY dangerous if you're directly on the internet.

---

### Post by tsanchung on 2009-10-22
> **Rocket2DMn said:**
> With a root shell, you aren't sharing a session with your graphical login like you are with sudo, so the shell doesn't know about X.  This is the same behavior as if you tried to run a graphical application from a tty.  Is there a particular reason you are trying to run these apps from a root shell, or that you have a root account enabled to begin with?

The konsole allows a root shell which I use to install software and so on.
I want to run the gvim on root shell to edit files owned by root (e.g. files in the /etc directory) without typing the root pw.

---

### Post by tsanchung on 2009-10-22
> **Giblet5 said:**
> That's because xhost authentication prevents another user from opening windows on your desktop (or grabbing your key strokes), locally or via remote.

If other (simultaneous) local and other LAN users are not an issue, you can open up your X server via the following. (WARNING: You are wide open at this point. Very dangerous.)
```
xhost +
```Read the man page ```
man 1 xhost
``` for more info, or grab Volume 3 of the "The X Window System" over on O'Reilly's web (free and very useful).

# xhost +
Invalid MIT-MAGIC-COOKIE-1 keyxhost:  unable to open display ":0"
# DISPLAY=:0.0
# xhost +
Invalid MIT-MAGIC-COOKIE-1 keyxhost:  unable to open display ":0.0"

---

