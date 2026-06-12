---
title: "Why when i press hibernate with LiveUSB of ubuntu it doesn't?"
date: 2011-01-19
forum: General Help
---

### Post by c933103 on 2011-01-19
I was using Ubuntu netbook remix 10.10 liveusb ver. and then someone unplug my power and then i unaware of it and leave it. after serval hours, i find it and the screen go blacke. when i reboot with the LiveUSB, i find it just same as not being used before. although it is what Live USB supposed to do if someone restart the computer with it, but i check the deafult setting when the battery become extremely low it should hibernate install, and why LiveUSB ver. would loss all data after hibernate as same as restart?

---

### Post by cascade9 on 2011-01-19
If you dont have a 'swap' partition, hibernate wont work. 

If dont know if hibernate will work if you have a swap with a liveCD. LiveCDs arent really made for everyday use anyway.

---

### Post by c933103 on 2011-01-19
1. that is liveusb not livecd 2. there are 7xxMB swap on HDD, and i can use the hibernate function on same computer with installed ubuntu 9.04 perviously.

---

### Post by cascade9 on 2011-01-19
LiveCD, liveUSB, no real difference as far as I know

I'd guess that the liveCD/liveUSB doesnt automatically mount your swap partition.

---

### Post by 3Miro on 2011-01-19
I agree about the swap. You can check to see if the swap is enabled either from the System Monitor or by typing:

```
sudo swapon -s
```

---

### Post by c933103 on 2011-01-19
> **3Miro said:**
> I agree about the swap. You can check to see if the swap is enabled either from the System Monitor or by typing:

```
sudo swapon -s
```

system monitor told me that the system is using swap automatically already..

---

### Post by c933103 on 2011-01-19
please help me to delete this reply because it was duplicated.

---

### Post by c933103 on 2011-01-21
Anyone here have any clue on what's wrong?

---

### Post by cascade9 on 2011-01-21
LiveCD/LiveUSB arent really made to be run the way you can run an installed OS. Itrs more for just testing to see if installing should work or not. 

Why not install?

---

### Post by c933103 on 2011-01-21
> **cascade9 said:**
> LiveCD/LiveUSB arent really made to be run the way you can run an installed OS. Itrs more for just testing to see if installing should work or not. 

Why not install?

because at the moment all 4 harddisk on my hand are having too many bad sector so impossible to use them normally...and shouldn't it also simulate the hibernating function?

---

