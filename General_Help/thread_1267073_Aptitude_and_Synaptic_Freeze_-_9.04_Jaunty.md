---
title: "Aptitude and Synaptic Freeze - 9.04 Jaunty"
date: 2009-09-15
forum: General Help
---

### Post by Lordmonkey on 2009-09-15
Hi,

I'm running Ubuntu 9.04 Jaunty

I did:

```
sudo aptitude update
```

It prompted for password then froze when I hit return. Usually it does it's thing and goes into the repositories but right now it's doing nothing. The terminal does not crash but aptitude simply sits there and performs no action (that I can see).

The above also happens if I do:

```
sudo apt-get update
```

I also tried to run Synaptic Package Manage but it seems to crash as it loads!

I had to use killall aptitude because it would not die via htop.

I haven't updated or install anything for a couple of weeks, but today I tried to reinstall something and the process froze, which is when I tried using aptitude and Synaptic.

I have restarted a few times and immediately opened a terminal window and tried to run aptitude but it still freezes.

Any thoughts? Aptitude usually works fine for me so I have no idea what has changed...

If it needs a reinstall, is the process safe?

---

### Post by Lordmonkey on 2009-09-15
Ok, so the terminal finally decided to report that aptitude cant lock dpkg  - Synaptic was still loitering as a process and blocking it.

Killed Synaptic and now everything is hunky-dory! :D

---

