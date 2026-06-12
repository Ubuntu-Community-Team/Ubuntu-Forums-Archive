---
title: "GRUB leaves win7 unable to boot"
date: 2011-01-02
forum: General Help
---

### Post by vacco on 2011-01-02
I am able to get into GRUB and boot Linux, but whenever I select Windows, all I get is an error about a missing boot loader.

After the Windows install disk failed to repair it, I reinstalled the Windows system and then used the Ubuntu live-CD to restore GRUB in order to be able to boot into Linux again. Now I have the same problem as when I started (although the error screen is somewhat different now).

Does anyone know how to break this "evil circle" of mine? :-k

I am using the 10.10 (GRUB 2 in other words).

---

### Post by Bucky Ball on 2011-01-02
Open a terminal (Applications->Accessories->Terminal) and paste this:

```
sudo update-grub
```

---

### Post by bludgard on 2011-01-02
Back up whatever you may have.
 
Wipe the entire disk
 
Install Windows.
 
Shrink Widows Partition to your liking.
 
Install Ubuntu to the unused partition (or portion thereof).
 
From within Ubuntu,via Synaptics PackageManager,install Startup Manager.
 
Run Startup Manager,select which OS to default boot.
 
Easiest way I've found.Reliable so far.
 
One

---

### Post by vacco on 2011-01-03
update-grub did the job. Windows boots nicely now, although listed with the wrong partition in the GRUB menu. After a closer look at my partition table I realize the 100 MiB Windows 7 boot partition is missing, which is probably the reason for all this.

---

### Post by bludgard on 2011-01-03
> **Bucky Ball said:**
> Open a terminal (Applications->Accessories->Terminal) and paste this:
 
```
sudo update-grub
```
 
Thank you for a simple and straight-forward solution.Now I know as well.

---

### Post by Bucky Ball on 2011-01-03
> **vacco said:**
> update-grub did the job. Windows boots nicely now, although listed with the wrong partition in the GRUB menu. After a closer look at my partition table I realize the 100 MiB Windows 7 boot partition is missing, which is probably the reason for all this.

Great news and well spotted! Enjoy! ;)

> **bludgard said:**
> Thank you for a simple and straight-forward solution.Now I know as well.

Pleasure. Glad OP didn't dive in and wipe the lot! :)

---

