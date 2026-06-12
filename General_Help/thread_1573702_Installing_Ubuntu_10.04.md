---
title: "Installing Ubuntu 10.04"
date: 2010-09-13
forum: General Help
---

### Post by delanri on 2010-09-13
Hey i'm new to ubuntu...
i want to install ubuntu using specifically manual partition...
i have 80 GB HDD and 2GB RAM, and could you tell me how should i make my partition?
Thanks

---

### Post by TNT1 on 2010-09-13
What partitions do you want, and what do you want to do with them?

---

### Post by delanri on 2010-09-13
> **TNT1 said:**
> What partitions do you want, and what do you want to do with them?

i don't know...
that's why i'm asking...
like i make 2 partitions in windows...
C for the system then D for the DATA...
just like that...

---

### Post by TNT1 on 2010-09-13
Run the garphical installer from a live cd, when you get to the partition choices, select manually configure, and you can size the partitions as you need them. Remember, ubuntu doesn't use drive letters:

[LIST]
[*]IDE drives are marked hdX, where X is one of the four letters a-d.         hda is the primary master, hdb is the primary         slave, hdc is the secondary master, and hdd is the         secondary slave.
[*]SCSI / SATA drives are marked by sdX, where X is any which letter.
[/LIST]
If you want to use gparted from the live cd before installing, use this guide:

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Nytram on 2010-09-13
> **delanri said:**
> Hey i'm new to ubuntu...
i want to install ubuntu using specifically manual partition...
i have 80 GB HDD and 2GB RAM, and could you tell me how should i make my partition?
Thanks

I would create 3 partitions for your Ubuntu install:

1. Your root folder also known as / which will store the OS and any applications you install. I would set the size between 10-20 Gb.

2. A home folder otherwise known as ~ to hold your personal data, documents, videos, music etc. Give this one the most space. Note: it's not mandatory to have a seperate home partition but it's useful in case you need to reinstall Ubuntu.

3. A swap partition - similar to virtual memory on windows. I would give this the same as your amount of ram 2Gb.

---

