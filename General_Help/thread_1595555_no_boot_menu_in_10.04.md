---
title: "no boot menu in 10.04"
date: 2010-10-13
forum: General Help
---

### Post by oboedad55 on 2010-10-13
Hi, I have a strange issue. I installed Lucid on a new box and although it boots fine I get no boot menu. I just did a bunch of updates, including a new kernel, so I would expect that the older kernel would show up as well as the recovery option. I've rerun "update-grub" a few times but to no avail. Any ideas would be welcome!

---

### Post by Quackers on 2010-10-13
If it is the only OS I think the default in grub2 is to just boot it. If you hold down the shift key during boot I think the menu will show up.

---

### Post by lindsay7 on 2010-10-13
install startup-manager from synaptic package manager and find it under system/administration.  Make sure the time out is long enough to see the kernels

---

### Post by oboedad55 on 2010-10-13
> **lindsay7 said:**
> install startup-manager from synaptic package manager and find it under system/administration.  Make sure the time out is long enough to see the kernels

I installed startup mangler and the time out is set to 10 seconds. The previous poster was correct about holding the shift key to bring up the boot menu. Why it doesn't do this by default escapes me, and I would be happy if someone had a resolution to this.

---

### Post by plucky on 2010-10-13
> **oboedad55 said:**
> I installed startup mangler and the time out is set to 10 seconds. The previous poster was correct about holding the shift key to bring up the boot menu. Why it doesn't do this by default escapes me, and I would be happy if someone had a resolution to this.

Try
```
gksudo gedit /etc/default/grub
```

Change this line ```
#GRUB_HIDDEN_TIMEOUT=0
``` to ```
GRUB_HIDDEN_TIMEOUT=05
``` and then run ```
sudo update-grub
```

Good luck

---

### Post by oboedad55 on 2010-10-13
> **plucky said:**
> Try
```
gksudo gedit /etc/default/grub
```

Change this line ```
#GRUB_HIDDEN_TIMEOUT=0
``` to ```
GRUB_HIDDEN_TIMEOUT=05
``` and then run ```
sudo update-grub
```

Good luck

Thanks for the reply. I found that same answer minutes before I saw your post. The "fix" works great. Apparently if you only have the one OS installed you don't get the boot menu by default with Lucid. I still think it's odd and after I managed to word the search properly I got a number of Google hits on this issue. I did notice that in your reply the order for correction is backwards. If the line is commented out the boot menu will show.

---

