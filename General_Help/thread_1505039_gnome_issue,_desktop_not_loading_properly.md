---
title: "gnome issue, desktop not loading properly"
date: 2010-06-08
forum: General Help
---

### Post by Matt26 on 2010-06-08
i recently restarted my computer after trying to install an update that was available for ubuntu (linux kernel image update i believe) which failed.

after restarting the computer, the ubuntu splash screen appeared as usual, and now my desktop is gone (see attached image).

i also got a gnome error message (attached) which i've never seen before, but i'm guessing it's related to my absent desktop.

can anyone help me restore my desktop?

thanks in advance.

---

### Post by Matt26 on 2010-06-09
i've tried the suggestions outlined in the post below, but so far i haven't been able to resolve this issue.

[http://ubuntuforums.org/showthread.php?t=980711](http://ubuntuforums.org/showthread.php?t=980711)

has anyone else run into this issue before?

---

### Post by Matt26 on 2010-06-10
so.. i've seen this issue posted elsewhere, including on these forums, so someone must have run into this issue before (and hopefully fixed it).

i've tried a number of suggestions (sorry, i can't remember the details at the moment, and i'm not in front of the computer), none of which seem to have made any difference.

please help!

---

### Post by konqueror7 on 2010-06-10
i would just throw out some suggestions here.

have you tried booting with a different kernel version, the one that worked before you upgraded; and, did you try reinstalling the desktop? 'sudo apt-get install ubuntu-desktop' or via synaptic.

---

### Post by Matt26 on 2010-06-11
> **konqueror7 said:**
> i would just throw out some suggestions here.

have you tried booting with a different kernel version, the one that worked before you upgraded; and, did you try reinstalling the desktop? 'sudo apt-get install ubuntu-desktop' or via synaptic.

yes, i have tried reinstalling the desktop using that command with no success.

i haven't tried booting with a different kernel version- how do i do that?

---

### Post by konqueror7 on 2010-06-11
usually when you upgrade, there are some new menu items in GRUB, so you can choose there.

---

### Post by Matt26 on 2010-06-15
> **konqueror7 said:**
> usually when you upgrade, there are some new menu items in GRUB, so you can choose there.

i tried using the last 4 versions of the kernel with no success, same issue.  i also tried recovery mode with the newest kernel with no success.

using recovery mode, i tried the fail safe graphics mode which didn't work- the picture on the screen became distorted so there was nothing to see.

i also tried doing an update using the 'repair broken packages' option in recovery mode, which allowed me to update the kernel to a newer version.  all of the updates were installed successfully, but upon reboot i still ended up with the same gnome power manager error.

is there anything else that i can try to fix this issue?

---

### Post by Matt26 on 2010-06-17
anyone?

any suggestions or options would be greatly appreciated.

---

### Post by konqueror7 on 2010-06-18
seems pretty strange, have you tried reinstalling gnome-power-manager in synaptic? just so it can reinitialize its configs?

i'll try to look if this is a bug...

---

### Post by Matt26 on 2010-06-18
> **konqueror7 said:**
> seems pretty strange, have you tried reinstalling gnome-power-manager in synaptic? just so it can reinitialize its configs?

i'll try to look if this is a bug...

that it is... i can't get into synaptic because i have no desktop... i have tried reinstalling gnome-desktop entirely, which from what i've read, will reinstall the gnome-power-manager.

at this point it can't hurt to try, though- what's the command for reinstalling the gnome-power-manager?

---

### Post by konqueror7 on 2010-06-18
```
sudo apt-get --reinstall install gnome-power-manager
```

oh, and could it be your harddrive is full? try doing
```
df -h
```
when '/' is at 100% or almost try freeing up some space,
```
sudo apt-get clean
```
```
sudo apt-get autoclean
```

---

