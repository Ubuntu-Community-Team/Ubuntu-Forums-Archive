---
title: "DBus Hogging Memory"
date: 2010-10-13
forum: General Help
---

### Post by rfdeshon on 2010-10-13
G'day Ubuntu Forums. Been a while. I've been having a problem over the past few weeks with DBus going hog-wild with my memory. It's gotten to be so bad I have to reboot my workstation at least once a week now (whereas before I used to only reboot when a new kernel was released). Yesterday, dbus was using around 30% of my 4G of RAM. Rebooted, now dbus is already back up to almost 15%. 

```
rfdeshon  1837  0.5 14.2 575360 541560 ?       Ss   Oct12   9:06 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session

```

Searching the forums and the "Ubuntu Search Engine" haven't yielded any results for me so far. Just wondering if anyone else has been noticing similar issues, has any idea what could be going on, etc.

Oh, this is on a fully up to date 10.04, 64-bit install. 2.6.32-25-generic kernel. The only non-repo software installed is Dropbox and folding@home. I don't think either of those use dbus at all.

---

### Post by Jebtrix on 2010-10-13
Dropbox most definitely uses DBus

---

### Post by rfdeshon on 2010-10-14
Hmm... well stopping dropbox doesn't appear to be helping things any. Then again, I suppose I would have to restart dbus and see if the memory usage climbs without it running to be sure.

Of course, that said, I also have dropbox running on my netbook using UNR 10.04 and dbus doesn't omnomnom all the memory on that =/

---

### Post by rfdeshon on 2010-10-14
Actually, I guess I don't need to do that. I've been running with Dropbox stopped my whole shift today and dbus has been steadily increasing it's memory usage the whole time. Up to 25.3% now from just under 24% when I came in.

---

### Post by rfdeshon on 2010-10-17
I hate to be a jerk... but well... it's been 3 days now so, bump?

Are there any dbus experts out there that can offer some insight into figuring out why it's leaking memory? I can't be the only Ubuntu user in the world having this issue... can I?

---

### Post by dino99 on 2010-10-17
Dbus is now left behind on actual distro, replaced by udev

Dbus have links with: GLib, Python, Qt & Java. So you might have either some old settings breaking your system, or some weird app still using dbus

---

### Post by rfdeshon on 2010-10-19
dbus may be left behind, but it seems like half the base system install relies on it, including such important packages like gksu, compiz, avahi, vim, ubuntu-desktop, etc.

---

