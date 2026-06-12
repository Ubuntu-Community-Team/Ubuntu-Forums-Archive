---
title: "Getting into X with 10.10"
date: 2011-06-02
forum: General Help
---

### Post by The Switch Blade on 2011-06-02
Hi,

I upgraded from 10.04 to 10.10 last night.

When I boot, it brings me into the terminal and does not start X automatically. If I type "startx", it gives me an API mismatch error. If I do:

```
sudo rmmod nvidia
sudo modprobe nvidia
startx
```

Then I can get into X. How can I automate this process?

---

### Post by seawolf167 on 2011-06-02
Instead of automating the process right away - I would first try reinstalling the Nvidia proprietary drivers and see if that fixes your issues.

---

### Post by The Switch Blade on 2011-06-02
I did that previously. I ran

```
sudo apt-get remove nvidia-*
```

and installed NVIDIA-Linux-x86_64-270.41.19.run. That's when I got the API mismatch error.

Why does it bring me to the terminal when I load ubuntu?

---

### Post by seawolf167 on 2011-06-02
Here are detailed [uninstallation instructions ]("https://help.ubuntu.com/community/NvidiaManual#Uninstalling%20the%20Driver")for the Nvidia driver

Does reconfiguring xserver-xorg help?

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by The Switch Blade on 2011-06-02
No, it didn't work.

I notice that the error I'm getting when I try to startx is a mismatched version. Apparently I just installed version 270-something and the nvidia kernel is using 260-something.

---

### Post by seawolf167 on 2011-06-03
Try using [Jockey ]("https://launchpad.net/jockey")and see if that is able to solve the problem of mis-matched drivers for you.

---

