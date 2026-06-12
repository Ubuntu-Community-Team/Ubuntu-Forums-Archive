---
title: "External 1394 HD automounted in 8.04, but not 9.04"
date: 2009-08-04
forum: General Help
---

### Post by lawtech on 2009-08-04
I installed 8.04 on a desktop in the spring of 2008. Since then I've been using a 1394 Lacie 300 GB hard disk for backups, manually powering it, plugging it in and invoking rsync. I bought a new desktop last week. When time came for backup, I plugged the Lacie into the new machine and powered it on, as I've done many times under 8.04.

Nothing obvious happened.

I did not get a nautilus window showing me the Lacie drive contents. There was nothing in /media/ relating to the Lacie, such as /media/LACIE2, as before.

The drive still works on the old machine under 8.04. The connection to the new machine appears to be fine mechanically.

Anybody have any idea what's going on here?

Can somebody please post a series of instructions about how to chase this problem and hopefully get it resolved?

Many thanks!

---

### Post by michy99 on 2009-08-04
This may not be the solution your looking for, but I have a USB dvd drive that will only show up if it is plugged in and turned on before I boot,

---

### Post by lawtech on 2009-08-04
Thanks for the response.

I tried that. No joy.

I'm beginning to wonder if the 1394 connector or system on the new machine is bad. Anybody have any thoughts on how to tell? I don't have a second 1394 device available at the moment.

And is it possible something was left out of the 9.04 release that was present in the 8.04 release?

---

### Post by michy99 on 2009-08-04
Does it show up with:```
sudo fdisk -l
```

---

### Post by lawtech on 2009-08-04
"sudo fdisk -l"

Only the primary disk, the /dev/sda group of partitions, shows up.

---

### Post by ajgreeny on 2009-08-04
How about running the live CD and trying the **fdisk -l** command in that, or gparted on the live CD to see if that sees the disk.  Use the 9.04 live CD, of course, for a proper comparison.

---

### Post by lawtech on 2009-08-04
Booted from the 9.04 LiveCD. Ran "sudo fdisk -l"

It reported only the primary hard drive.

I tried various combinations of plugging in the 1394 drive before and after powering it on. No joy.

I think it's time to pop the box and inspect the cables and connectors. And I may have a 1394 interface card I can plug in. I think I have a hardware issue.

Thanks for the advice so far. I'll report back to this list when fdisk sees the 1394 drive. Bet when that happens, it all works fine.

---

### Post by lawtech on 2009-08-21
The drive now works.

The problem was the connection at the back of the box. The socket is recessed slightly and not every cable makes contact. I found one that does, and the drive immediately pops up and works fine.

Thanks for all the advice.

---

