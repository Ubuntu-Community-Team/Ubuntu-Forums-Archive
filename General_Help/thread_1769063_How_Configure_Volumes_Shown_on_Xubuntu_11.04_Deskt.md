---
title: "How Configure Volumes Shown on Xubuntu 11.04 Desktop"
date: 2011-05-27
forum: General Help
---

### Post by fleamour on 2011-05-27
I have installed Xubuntu 11.04 to dual boot with older LTS version.  When booting 11.04 it auto shows LTS root & home volumes on desktop.  I wish to hide them (home encrypted anyway.)

---

### Post by Toz on 2011-05-27
Create a file in /etc/udev/rules.d called 10-local.rules```
sudo mousepad /etc/udev/rules.d/10-local.rules
```with the following contents:```
KERNEL=="sda1", ENV{UDISKS_PRESENTATION_HIDE}="1"
```

...and replacee sda1 with the correct partition name. If you have more than one partition you want to hide, create multiple lines with different partition names.

Reboot.

---

### Post by fleamour on 2011-05-27
Thanks!!!

Using:
```
blkid
```
to identify correct volumes is just the trick!

:grin::biggrin::grin:

---

### Post by kamaji792 on 2011-05-27
Hi,

[edit]
**Toz** obviously knows what he is talking about. Ignore my post.  I'll leave it so you can have a laugh.
[/edit]

You could edit the /etc/fstab file.

Make a copy of it first for backup.

```

sudo cp /etc/fstab /etc/fstab.01
sudo gedit /etc/fstab

```

put a '#' character at the front of the lines associated with the LTS home and root volumes.

That will of course mean they are not hidden, just not mounted.

So another option would be to edit the /etc/fstab file but for the TST home and root volumes add the option (4th group of text - the options) **noauto**.  e.g.
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

**Note** editing the /etc/fstab file is a good way to end up with a system that will not boot.  But hey!  Nothing ventured, nothing gained.

Post your current fstab file if you like.

atb S

---

