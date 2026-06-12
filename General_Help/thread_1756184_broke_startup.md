---
title: "broke startup"
date: 2011-05-12
forum: General Help
---

### Post by DanBender on 2011-05-12
Alright, I broke my computer startup process. I added an ext4 partition for something and set it to automount using storage device manager. Then I had to delete it and create the same partition ID as NTFS. I forgot to redo the storage device manager step.

So when I rebooted later, it tried to mount the partition as ext4, and thus did not complete the startup process. I was able to edit /etc/fstab to set the partition to ntfs using nano relatively easily, and when I rebooted it appeared to mount everything correctly, best I can tell.

Unfortunately, it's just sitting there giving me a tty login prompt. At this point in a normal startup, it would start the graphical desktop (xfce, for Mythbuntu). I was hoping by solving the mount issue the rest of the startup would go without a hitch, but obviously this broke something else as well, and I'm at a loss as to what it is or how to fix it.

Ctrl-Alt-F7 only brings up a blank black screen with a blinking dash cursor in the upper left-hand corner.

Any suggestions?

---

### Post by DanBender on 2011-05-13
Ok. I fixed it, I think.```
sudo shutdown now
```instead of shutting the computer down, it brought up a number of recovery and low-graphics mode options. I reloaded the default graphics settings, which allowed me to boot into the graphical desktop. I then reinstalled the NVIDIA drivers 256, and I think I'm back where I'm supposed to be.

I'm not marking this as "SOLVED" because I still have no idea what was wrong, and what actually got fixed.

---

