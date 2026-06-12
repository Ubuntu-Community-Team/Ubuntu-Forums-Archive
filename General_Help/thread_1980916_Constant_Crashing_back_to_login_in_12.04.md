---
title: "Constant Crashing back to login in 12.04"
date: 2012-05-16
forum: General Help
---

### Post by kotoro on 2012-05-16
hp xw8600 workstation, freshly installed ubuntu 12.04. Constantly crashes out of user sessions back to login. No idea why, how do I go about diagnosing it?

---

### Post by carl4926 on 2012-05-16
try selecting ubuntu 2D from the session login

---

### Post by 2F4U on 2012-05-16
Did you already look into the log files? If not, the ones to look at first would be:
- /var/log/syslog
- /var/log/Xorg.0.log
- .xsession-errors in your home folder

---

### Post by markbl on 2012-05-16
> **2F4U said:**
> Did you already look into the log files? If not, the ones to look at first would be:
- /var/log/Xorg.0.log

Actually, also have a look at /var/log/Xorg.0.log.old as that is where the last xorg crash (if any) will be recorded. Do you have a nvidia graphics card? There are many reports of the nvidia driver crashing, search these forums for more details.

---

### Post by kotoro on 2012-05-16
It does in fact have an nvidia card, its a quadro, i'll get the full name in a few minutes when I try to grab the logs.

My system76 laptop ALSO has nvidia card, but has not crashed at all.

---

### Post by kotoro on 2012-05-16
Attempting to use 3TB HDD as the booting drive is causing me headaches. For some reason the boot partition isn't being configured properly and it drops out to grub rescue. When I attempt manual grub install it says the disk ran out of space. (apparently it isn't being given the full 1MB that it was supposed to put into the partition).

Any advice on this?

---

### Post by gifford on 2012-06-16
I also had the problem with the HP xw8600 crashing back to the login. My solution was to disable Ubuntu One. It seemed the problem occurred with syncing, which I was unable to disable, so just removed the machine from Ubuntu One.

Sorry about the above post..it was only temporary.

What I had to do was make sure the bios was set to correctly for the video card, x16 in the PCIe setting. Also, I could not get 12.04 to work without crashing so had to install 11.10. It is working great now but only after much frustration and hair pulling.

---

### Post by gifford on 2012-07-28
The issue returned and gradually got worse. With much frustration and time spent trying to solve it, I opted to get an AMD/ATI graphics card to replace the NVIDIA. No more problems and 12.04 runs great.

It seems Linus was right!

---

