---
title: "Hard Drive info command/CLI program?"
date: 2011-12-18
forum: General Help
---

### Post by espo111 on 2011-12-18
I want to boot into a Live CD and gather system information

Is there a utility or program I can run at the CLI (and pipe to e txt file) that will display all info on all my hardrives??

I am looking for model numbers, serial numbers, size, manufacturer... etc.

something like lspci or uname I was thinking. I want Commandline, no gui.


thanks

-f

---

### Post by dieseleldo on 2011-12-18
Try to install hdparm and use the command ```
 hdparm -i /dev/(drive)
```. This will give you make, model, serial, firmware revision if reported, as well as current and supported DMA/UDMA/PIO transfer modes.

---

### Post by espo111 on 2011-12-18
hdparm 9.37 is already installed on the 11.10 live CD and it gave me what i wanted. never knew about it.

thanks :)

---

### Post by seawolf167 on 2011-12-19
Additionally, you can use a command like

```
sudo lshw -class disk
```

to list all the stats (description, product, vendor, etc. etc.) for your hard drives

---

### Post by espo111 on 2011-12-19
> **seawolf167 said:**
> Additionally, you can use a command like

```
sudo lshw -class disk
```

to list all the stats (description, product, vendor, etc. etc.) for your hard drives

thanks that worked even better as the other did not manufacturer.

---

### Post by seawolf167 on 2011-12-19
glad you got it working - if you have everything answered please mark this thread as solved under thread tools

---

