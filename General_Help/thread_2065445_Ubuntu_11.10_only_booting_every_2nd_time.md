---
title: "Ubuntu 11.10 only booting every 2nd time"
date: 2012-10-01
forum: General Help
---

### Post by roger_reject on 2012-10-01
A recent update seems to have broken something in the boot process.  Others have noted similar problems in the past (see: [http://ubuntuforums.org/showthread.php?t=1752091](http://ubuntuforums.org/showthread.php?t=1752091), for example), but unfortunately they (mostly) seem to stem from an NVIDIA driver issue, but since I'm not using an nvidia card I think in my case it must be a different issue.  

The best I can tell, during boot three will be a purple splash but no ubuntu logo, then the screen goes black.  I think it actually boots up to the login screen but without turning on the display, because when I type my password and hit enter, I can see the HDD light blinking like the cpu is busy, so it's not that the system is just hanging.  I'm guessing this means it is a graphics driver issue, but I'm not sure what to do to solve it..

Any help would be much appreciated, output of lshw [_here_]("http://pastebin.com/gw2KUvid") in case it is helpful...

---

### Post by h113331pp on 2012-10-02
could you use "ctrl + alt + F1~F6" to switch to console?

if you can, try to restart your DM after you login on console.like following:

sudo service your_DM_name(lightdm, lxdm, gdm etc...) restart(or start)

---

### Post by roger_reject on 2012-10-02
> **h113331pp said:**
> could you use "ctrl + alt + F1~F6" to switch to console?

if you can, try to restart your DM after you login on console.like following:

sudo service your_DM_name(lightdm, lxdm, gdm etc...) restart(or start)
I did try this, but no dice.  Switching doesn't turn the display back on.

---

### Post by Stonecold1995 on 2012-10-03
I think the same thing is happening with my brother's HP Pavilion laptop, and my brother doesn't use Nvidia either, he has an AMD Radeon.  Approximately every other boot, he has to use the magic SysRq combo to force reboot and after that it'll boot correctly.

---

### Post by u2nTu on 2012-11-06
Had exactly this same problem and noticed no  resolution here so I'll mention what worked for me. It was pretty simple, really.
```
sudo gedit /etc/default/grub
```Arrow down to the line ```
#GRUB_HIDDEN_TIMEOUT=0
```and remove the leading **#** (uncomment). Save and exit, then:```
sudo update-grub
```That's it. Restart several times (using menu, not CLI) and it works every time, instead of every other one.

Such an annoyance relieved, hope it works for others. :guitar:

---

