---
title: "Root partition full! Now what?"
date: 2006-05-27
forum: General Help
---

### Post by chloraldo on 2006-05-27
My root is full, no disk space left. Home is on a different partition. I can't start synaptic to remove software anymore. What can I delete?

The home partition still has space. Can I resize the / partition and the home partition to transfer space from home to / ? How? I don't have gparted and can't install it because of my space problem...

Thanks for help

---

### Post by johnc4510 on 2006-05-27
You can probably gain some space by running this command:
sudo apt-get clean
This will remove all .deb files that are archived from the installs

---

### Post by chloraldo on 2006-05-27
[QUOTE=johnc4510]You can probably gain some space by running this command:
sudo apt-get clean
This will remove all .deb files that are archived from the installs[/QUOTE]
I tried that already, didn't work, still 100% (7.1 GB) used.

Isn't 7.1 GB quite a lot for the / without home?

---

### Post by johnc4510 on 2006-05-27
My / is at 2.7, but I don't have a lot of Programs apps installed. You might be able to resize the home and / partions if they are next to each other. You would have to backup everything on the /home partition, then resize both, then put your home data back on the newly resized partition. Google: gparted live cd for an easy way to set up partions.

---

### Post by mumushi on 2006-05-27
i totlly agree using the gparted live cd. that would greatly help you resizing your partitions.

---

### Post by wirespot on 2006-05-27
And no, 7 GB is not necessarily a lot. Depends on what you have installed. Add a whole bunch of those bigger games and you'll see it shoot up to 9-10 GB, like mine has.

---

### Post by danjordy on 2006-06-08
[QUOTE=johnc4510]You can probably gain some space by running this command:
sudo apt-get clean
This will remove all .deb files that are archived from the installs[/QUOTE]
I went from ~250mb free to 1.11gb free. That helped alot.

---

