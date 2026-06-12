---
title: "Not recognizing all my memory (64 bit)"
date: 2010-01-07
forum: General Help
---

### Post by tkinney on 2010-01-07
I have 6gb Ram.  Bios is recognizing all of it.  Ubuntu 9.10 i368 is only recognizing 2.5 of it.  I am new to linux and have no idea what the problem might be.  I have run hardinfo and it only sees 2 gb as well.

My specs:
NVIDIA 680i
intel core 2 quad extreme
6 gb corsair 800mhs (2x1 and 2x2)
Geforce 8800gts 320mb sli'ed with a 9800 with 1gb
Running Ubuntu 9.10 i368

I will gladly post any info you need, but you may need to walk me through how to get to it.

---

### Post by ibuclaw on 2010-01-07
Install the PAE Enabled kernel, as 32bit kernels have issues with addressing memory > 4GB. (This is all OS's, even Windows) ;) 

```
sudo apt-get install linux-generic-pae
```

Regards
Iain

---

### Post by amauk on 2010-01-07
either that, or reinstall Ubuntu using the 64bit disk

---

### Post by tkinney on 2010-01-07
DOh!  I actually thought I had loaded the 64 bit version.  Got the answer I needed after asking the wrong question.  Thanks guys.

---

