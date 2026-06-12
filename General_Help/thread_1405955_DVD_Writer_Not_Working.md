---
title: "DVD Writer Not Working"
date: 2010-02-13
forum: General Help
---

### Post by joeknoodle on 2010-02-13
Solved. I figured I'd put a known working DVD in place, and upon opening the case I saw a wire that was unplugged. Whatever that wire is, it sure needs to be plugged in :) (no, it wasn't the power)
---------------------------------------
9.04 / Gnome

My friend has a dvd-writer that reads dvds just fine, but won't let him write with it.

(He's actually trying to write CDs - it's my understanding this should work even with a DVD writer)

Here's the fstab if it means anything:

[code]
dev/sdc0 /media/cdrom0 udf, iso9660 user, noauto,exec,utf8 0 0
[/quote]
Thanks in advance for any help.

---

### Post by lenoirrichelieu on 2010-02-13
Check if he is member of cdrom group. In terminal type:
 
*id username*
 
It should list the groups your friend is member of.
 
And check the disk is not mounted when writing.

---

### Post by joeknoodle on 2010-02-13
Thanks, I'll try that. I'm snowed in right now so it'll take a bit to report back.

---

### Post by joeknoodle on 2010-02-15
> **lenoirrichelieu said:**
> Check if he is member of cdrom group. In terminal type:
 
*id username*
 
It should list the groups your friend is member of.
 
And check the disk is not mounted when writing.

He seems to be...
```

uid=1000(okey) gid=1000(okey) groups=1000(okey),
4(adm),20(dialout),21(fax),

24(cdrom),

26(tape),29(audio),30(dip),
44(video),46(plugdev),104(fuse),
106(lpadmin),112(netdev),121(admin),
122(sambashare)

```It shows CDROM, but does that mean DVD Writer? 

How can the machine write if it's not mounted?

---

### Post by mk1w86 on 2010-02-15
What program is he using to burn the CD and is there a specific error message?

---

