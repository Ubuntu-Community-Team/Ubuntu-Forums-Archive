---
title: "Grub boot issue"
date: 2010-11-15
forum: General Help
---

### Post by aquascrotum on 2010-11-15
Hi all

I upgraded from Jaunty - Karmic - Lucid in very quick succession (and surprisingly succesfully too) but have encountered a slight issue with Grub on booting up since the upgrade.

I had a removable HDD plugged in when the upgrade was going on.  Now when I boot up Grub stalls and comes up with a message that its looking for SDD5 or something.  I can tell it to skip this, but I'd rather it wasn't appearing at all.

How can I edit Grub to tell it what disks it should and shouldnt be looking for?

---

### Post by drs305 on 2010-11-15
The problem is probably with /etc/fstab. If it boots properly after you tell Ubuntu to skip it, it means it's not a required system partition. 

After you boot, open /etc/fstab and either remove or (safer) place a # symbol at the start of the sdd5 line.  Then figure out what is/was contained in sdd5 and why it now fails (mount point, formatting, etc).

```
gksu gedit /etc/fstab &
```

If all your fstab entries are UUIDs, run this command to find what the UUID is for sdd5:
```
sudo blkid -c /dev/null
```

---

