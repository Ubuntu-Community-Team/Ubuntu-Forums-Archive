---
title: "Karmic hangs during shutdown"
date: 2010-05-02
forum: General Help
---

### Post by zedi on 2010-05-02
After last update (kernel 2.6.31-21) my Karmic won't fully shut down.
I added `rmmod snd-hda-intel` to the halt script: `/etc/init.d/halt` and added `acpi=force` in the line `GRUB_CMDLINE_LINUX_DEFAULT="no splash"` of `/etc/default/grub`, also tried `sudo shutdown -h now` and `sudo shutdown -P now` in terminal but nothing works for me. Alt + SysRq + REISUO doesn't work either.
I am attaching shot of the screen when it hangs. (bottom cursor is blinking)
I found semi solution; when I boot to previous kernel 2.6.31-20 everything is OK.
Unfortunately with GRUB 2, I don't know how to make kernel 2.6.31-20 default (top) entry in `menu list`.
BTW, how to get rid of old kernels from `menu list`?

---

### Post by brotherz on 2010-05-02
Zedi - I had the same problem.  See my post put in about an hour before yours (hang at shutdown).  Good screen shot, I couldn't figure out how to get one.  I am still waiting for some advice but in the meantime thank you for additional details.

---

### Post by BrokeMahPC on 2010-05-02
I had this - a clean install was the only thing that solved it - I tried fixing and reconfiguring broken packages and purging/un-installing drivers.
I suspect something goes wrong with the kernel update - do you have any exotic ppa's?
One thing I did try that made things run better was updating the bios to the newest version.

---

### Post by zedi on 2010-05-03
**BrokeMahPC**,
Mine BIOS is already  the newest version and, yes I do have  exotic Ppa's but I need them (tualatrix/ppa – Ubuntu Tweak and berndth/ppa – Nautilus dual pane).
Why  clean install? Previous kernel 2.6.31.-20 works great. 
All I need is: how to move this kernel to the top position in GRUB menu – make it default.
I  tried:
1.`sudo grub-set-default 2` with `DEFAULT=saved in /etc/default/grub`
2.`gksudo gedit /etc/default/grub`– and `GRUB_DEFAULT=2` 
Nothing work. 
But I already got rid of old kernels from GRUB menu – Synaptic.
Unfortunately GRUB2 beats me! Maybe I'll have to revert to GRUB Legacy which is soooo much easier. Bloody GRUB2!!!

**brotherz,**
I just used digi camera to get screen shot. Easy!

Anybody out there, who knows what damage did kernel update?

---

### Post by dino99 on 2010-05-03
> **zedi said:**
> **BrokeMahPC**,
Mine BIOS is already  the newest version and, yes I do have  exotic Ppa's but I need them (tualatrix/ppa – Ubuntu Tweak and berndth/ppa – Nautilus dual pane).
Why  clean install? Previous kernel 2.6.31.-20 works great. 
All I need is: how to move this kernel to the top position in GRUB menu – make it default.
I  tried:
1.`sudo grub-set-default 2` with `DEFAULT=saved in /etc/default/grub`
2.`gksudo gedit /etc/default/grub`– and `GRUB_DEFAULT=2` 
Nothing work. 
But I already got rid of old kernels from GRUB menu – Synaptic.
Unfortunately GRUB2 beats me! Maybe I'll have to revert to GRUB Legacy which is soooo much easier. Bloody GRUB2!!!

**brotherz,**
I just used digi camera to get screen shot. Easy!

Anybody out there, who knows what damage did kernel update?

to customized grub2 order, use the custom section ( see below or posts by ranch hand)

---

### Post by dino99 on 2010-05-03
Note:

final installation is done and many devs are working on known bugs, wait a few days for new packages into repo if you have a minor problem  :)

---

### Post by zedi on 2010-05-03
dino99,
The custom section at first reading I found a bit intimidating. Yet after your suggestion I think I'll read it again; we'll see - or I can  wait a few days for new packages into repo if unsuccessful.
TY - thank you!

---

### Post by jrushslo on 2010-05-06
I found usable this workaround:
I go to /boot/ directory, create "old" directory and then move all *2.6.31-21* files to this directory. Before this you must have also another version of kernel installed (for example i have 2.6.31-20).
After moving files i update grub.cfg automatically with command "update-grub".
After next reboot you will have another kernel active.
You can check it before and after changes with command "uname -r".
Good luck!

---

### Post by brotherz on 2010-05-08
> **dino99 said:**
> Note:

final installation is done and many devs are working on known bugs, wait a few days for new packages into repo if you have a minor problem  :)


Dino99, Thanks.  I've been waiting and updating but so far the problem is not fixed.  Does this call for a bug report or just more patience?  I am holding off on trying jrushslo's workaround...for now.  It does not seem like a minor problem to have to power off by brute force every time.

---

