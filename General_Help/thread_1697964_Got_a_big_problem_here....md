---
title: "Got a big problem here..."
date: 2011-03-01
forum: General Help
---

### Post by beliyyal on 2011-03-01
Alright guys, here's the deal. I just recently got my internet back, so I had quite a few updates to install as you could imagine. Well, during the installation of the updates, my computer froze. I restarted it, and get to the log in screen, but I cannot type my password. It's like my computer doesn't even recognize that my keyboard is hooked up. I really need some help with this, and I'm hoping one of you guys might know how to correct this problem.

---

### Post by Smart Viking on 2011-03-01
Can you do <ctrl>+<alt>+<F3>? If so, log in(of you can) and launch "/etc/init.d/gdm3 stop" (maybe replace "gdm3" with just "gdm"), and launch "startx" and see if that works.

If not, have you tried plugging in another keyboard?

---

### Post by beliyyal on 2011-03-01
> **Smart Viking said:**
> Can you do <ctrl>+<alt>+<F3>? If so, log in(of you can) and launch "/etc/init.d/gdm3 stop" (maybe replace "gdm3" with just "gdm"), and launch "startx" and see if that works.

If not, have you tried plugging in another keyboard?

I'll give it a shot. I got my other hard drive in right now, and I'm updating it (fingers crossed).


EDIT:nope, didn't work. Tried two different keyboards, neither of them worked. And since I can't type anything, I can't do <ctrl>+<alt>+<F3>.

---

### Post by stoneage on 2011-03-01
If you have another kernel installed try booting from that, or from a Live CD, to repair and complete the updates.

---

### Post by beliyyal on 2011-03-01
> **stoneage said:**
> If you have another kernel installed try booting from that, or from a Live CD, to repair and complete the updates.
Ahh, didn't know you could complete updates with a live cd. Thanks man, I'll give it a shot.

---

### Post by beliyyal on 2011-03-01
Alright, I got the live cd booted up, now how do I go about completing/repairing the upgrades?

---

### Post by Bcrowes11 on 2011-03-01
Sounds like that's what he was saying...:p

---

### Post by jerome1232 on 2011-03-01
To complete the updates from a live cd I believe you'd have to mount your partitions and chroot into your install, then finish upgrading.

It's been awhile since I've had to do it so here's a little guide on how to chroot from a live cd, looked fine to me although it's not specific to ubuntu it should still be perfectly applicable.

[http://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation](http://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation)


edit: Were you able to boot an older kernel?

edit2: Once chrooted in you'd probably need to do
```
sudo dpkg-reconfigure -a
sudo apt-get upgrade
```

---

### Post by beliyyal on 2011-03-01
> **jerome1232 said:**
> To complete the updates from a live cd I believe you'd have to mount your partitions and chroot into your install, then finish upgrading.

It's been awhile since I've had to do it so here's a little guide on how to chroot from a live cd, looked fine to me although it's not specific to ubuntu it should still be perfectly applicable.

[http://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation](http://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation)


edit: Were you able to boot an older kernel?
I'm not really sure how to boot from an older kernel on 10.04. It was easy on 8.04, but I wouldn't know how to go about it on the newer version.

---

### Post by jerome1232 on 2011-03-01
If you don't get a grub prompt during bootup then mashing shift or esc during the boot process should get you one, you should have a list of kernels (unless you haven't updated before) you would select the next one down the list.

---

