---
title: "Remove Ext HDD From Boot-Up"
date: 2010-07-26
forum: General Help
---

### Post by victor9098 on 2010-07-26
I bought a new Seagate external HDD, formatted it via gparted (as I have done with others) but now whenever I start Ubuntu, the start-up pauses as Ubuntu cannot detect my seagate drive (then asks if I want to skip or manually fix).

Pressing F11 at start-up shows that the Seagate drive is listed as a boot-up drive (though second after the internal HDD), but I have no idea how this happened and would like to remove it as a boot option altogether.

As far as I can tell I did nothing different then I have done a dozen times before, so any input would be great.

---

### Post by victor9098 on 2010-07-26
OK... figured it out!

Somehow the new drive was added to fstab, so I had to remove it by doing the following.

1 - "Alt+F2"
2 - Typed "gksudo nautilus" and hit the run button
3 - Navigated to /etc/fstab
4 - Opened file and edited out the extra drive that was launching
5 - Saved the file when done and closed
6 - Restarted laptop

Everything seems to be back to normal now.

---

### Post by Paulgirardin on 2010-10-21
Thanks for the tip.

---

