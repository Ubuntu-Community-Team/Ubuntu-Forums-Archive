---
title: "At startup, getting &quot;Cannot find /media/&lt;various mount points&gt;&quot;"
date: 2011-05-28
forum: General Help
---

### Post by MorganRogers on 2011-05-28
I am running 10.10 x64.  Every time I boot up, after logging in I am getting several error messages to the effect of:

"Cannot find /media/<various mount points>"

such as /media/sdc1, /media/sdc1/Software, etc.  I *think* these are coming from Nautilus, which is starting up automatically, but not 100% certain about that.  These devices DID exist at one time, but no longer (I changed the mount point). There is still /dev/sdc1 but I don't think that alone has anything to do with it.    I see no evidence of them  in fstab or /media. I no longer have any shortcuts to them in Nautilus either.

What could be generating these ? 

TIA, Morgan

---

### Post by hawthornso23 on 2011-05-28
Is there anything in startup applications that might point to them perhaps.

---

### Post by Hedgehog1 on 2011-05-28
These old mount points may need to be removed from your **/etc/fstab** file.

You can edit it by doing:

```
gksudo gedit /etc/fstab
```

To be safe, put a '#' character in front of any mount point you think is outdated, rather than delete the line right way.

After a reboot and the messages stop happening, you can edit **/etc/fstab** again and delete the unwanted lines 'for real'.


***The Hedge***

:KS

---

### Post by hawthornso23 on 2011-05-28
Hedgehog - read carefully - he said he'd already checked fstab.

---

### Post by MorganRogers on 2011-05-29
I just looked through all auto start apps, nothing obvious there.  Still looking.

---

