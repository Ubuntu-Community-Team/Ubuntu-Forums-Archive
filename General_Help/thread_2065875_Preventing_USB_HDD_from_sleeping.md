---
title: "Preventing USB HDD from sleeping"
date: 2012-10-03
forum: General Help
---

### Post by szafran on 2012-10-03
Hi,

I have a Verbatim 2TB USB3.0 external HDD enclosure (with Samsung HD204UI inside). I'm having trouble preventing that drive from sleeping. I've tried:

in rc.local:
```
hdparm -S 0 -M 254 <device>
```

in crontab:
```
* * * * * root test -b /dev/disk/by-label/backup && su - szafran -c 'mkdir --parents /home/szafran/Backup/lost+found' > /dev/null
```

also in crontab:
```
* * * * * root test -b /dev/disk/by-label/backup && touch /home/szafran/Backup/tmp > /dev/null
```

But the drive keeps spinning down every couple of minutes (and then spinning up every time I login, reboot, access some files, open my home dir on the desktop, etc.).

Does anyone have any ideas on that topic?
Thanks in advance.

---

