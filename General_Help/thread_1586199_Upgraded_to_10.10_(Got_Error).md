---
title: "Upgraded to 10.10 (Got Error)"
date: 2010-10-01
forum: General Help
---

### Post by ki4jgt on 2010-10-01
upgraded to 10.10 last night with update-manager -d
Install problem!
The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator.

shows up in the right hand top corner of the screen.

Empathy which I have setup to run when the computer starts is open, with no window outline and it's asking for the keyring password also no outline.

Back ground is dark purple with no gnome-panels or anything.

I have grub2 setup with noapic nolapic and acpi=off

I upgraded for the better audio support, my speakers weren't working correctly. Any suggestions would be appriciated and I am willing to do anything, so please be creative.

---

### Post by sikander3786 on 2010-10-01
Are you sure you are not running out of disk space?

---

### Post by ki4jgt on 2010-10-01
Yes, I'm sure! I have 120 gigs

---

### Post by sikander3786 on 2010-10-01
Try

```

sudo dpkg --configure gnome-power-manager

```

Post back any error messages encountered.

---

### Post by ki4jgt on 2010-10-01
Didn't do anything. How do you install updates via the terminal? I had to use CTRL + ALT + F1 but my laptop says it is connected to the network

---

### Post by sikander3786 on 2010-10-01
> but my laptop says it is connected to the network

It is good if it is connected to the network. All you need is sudo apt-get update but I doubt you'll not be able to do any package related tasks until gnome-power-manager issue is sorted out.

---

### Post by ki4jgt on 2010-10-01
I did that, but how do I install them, and I guess the question still remains how do I fix GPM

---

### Post by ki4jgt on 2010-10-01
It's actually installing the updates, so I don't know what's going on

---

### Post by sikander3786 on 2010-10-01
You didn't post the output of

```

sudo dpkg --configure gnome-power-manager

```

---

### Post by sikander3786 on 2010-10-01
Also please post the output of

```

df -h

```

I still have some doubts about the disk space.

If it is installing the updates, the issue might sort itself once they finish.

---

### Post by ki4jgt on 2010-10-01
Hold on. It's about 20 lines and I can't C&P. Bare with me, if I make any mistakes.

Actually in short: Gnome power manager depends on XXX (>= V#); However Package XXX is not configured yet. Do I just go through and configure each one of these packages?

---

### Post by ki4jgt on 2010-10-01
Filesys
/dev/sda1
none
""
""
""
Size
227G
465M
470
470
470
Used
8.2G
280K
0
344K
0
Avail
207G
465M
470M
470M
470M
Used
4%
1%
0%
1%
0
mounted on
/
/dev
/dev/shm
/var/run
/var/lock

---

### Post by sikander3786 on 2010-10-01
Post the exact output when you get a chance. I am going to hang in there for a while :)

Also you haven't posted the complete output from df -h.

---

### Post by ki4jgt on 2010-10-01
It's not letting me configure any of these packages. All of them are dependent on other packages and when I try to configure them, they say the packages weren't installed.

---

### Post by ki4jgt on 2010-10-01
Just edited the post

---

### Post by sikander3786 on 2010-10-01
> **ki4jgt said:**
> It's not letting me configure any of these packages. All of them are dependent on other packages and when I try to configure them, they say the packages weren't installed.
df -h seems pretty ok. But from the quoted post, no one can understand the offending packages. Please be a little more specific.

---

### Post by ki4jgt on 2010-10-01
it goes like this:

> dpkg: dependency problems prevent configuration of gnome-power-manager:

> gnome-power-manager depends on XXX (>= VVV); however:
Package XXX is not configured yet.

XXX - VVV
libappindicator1 - 0.0.19
libbonobo2 - 2.15.0
libcairo2 - 1.2.4
libcanberra-gtk0 - 0.17
libcanberra0 - 0.2
libdbus-glib-1-2 - 0.88
libgconf2-4 - 2.31.1
libgdk-pixbuf2.0-0 - 2.21.6
libgnome-keyring0 - 2.20.3
libgtk2.0-0 - 2.18.0
libnotify1 - 0.5.0
libnotify1-gtk2.10 (not installed - <libnotify1 provides libnotify1-gtk2.10 is not configured yet>)
libpanel-applet2-0 - 2.26.0
libpango1.0-0 - 1.18.0
libunique-1.0-0 - 1.0.0
libupower-glib1 - 0.9.1
libxext6 - (none)
gconf2 - 2.28.1-2
notification-daemon (not installed - <notify-osd provides notification-daemon is not configured yet> <kdebase-runtime provides notification-daemon is not configured yet>)
dbus-x11 - (none)
consolekit - (none)
upower - (none)

> dpkg: error processing gnome-power-manager (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
gnome-power-manager

---

### Post by sikander3786 on 2010-10-02
Hi.

Try

```
sudo dpkg --configure -a
```

And if that doesn't work either, try

```
sudo apt-get install --reinstall ubuntu-dekstop
```

And even if that doesn't work, I fear you'll either have to reinstall or will have to manually clean the apt-get cache.

---

