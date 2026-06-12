---
title: "dpkg-reconfigure xserver-xorg ?"
date: 2011-08-13
forum: General Help
---

### Post by eyerouge on 2011-08-13
On my 11.04 (64) using:

```
sudo dpkg-reconfigure xserver-xorg
```

..does *nothing*: I just get back to the terminal and it doesn't show me anything. Is this "normal"? From what I recall it should display some blue menues etc, but it doesn't seem to do anything on my system.

If this is not normal, how can I fix it?

---

### Post by bodhi.zazen on 2011-08-13
> **eyerouge said:**
> On my 11.04 (64) using:

```
sudo dpkg-reconfigure xserver-xorg
```

..does *nothing*: I just get back to the terminal and it doesn't show me anything. Is this "normal"? From what I recall it should display some blue menues etc, but it doesn't seem to do anything on my system.

If this is not normal, how can I fix it?

xorg.conf is depreciated and sudo dpkg-reconfigure xserver-xorg has not worked reliably for several ubuntu releases.

A better question is - what video card do yo have and what monitor ?

---

### Post by eyerouge on 2011-08-13
I have:

Hardware
- MacBook Air 3,2
- GeForce 320M (GPU 0)

Software
- NVIDIA Driver Version: 270.41.06
- Ubuntu 11.04 (64)

( ...reason I want to reset/default my x is because I have issues when trying to get output cloned to external monitor, as seen in: [http://ubuntuforums.org/showthread.php?t=1824457](http://ubuntuforums.org/showthread.php?t=1824457))

---

### Post by bodhi.zazen on 2011-08-13
If you are using the nvidia driver, user the nvidia-settings command

```
gksu nvidia-settings
```

---

