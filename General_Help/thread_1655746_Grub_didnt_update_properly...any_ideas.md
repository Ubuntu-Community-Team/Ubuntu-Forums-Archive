---
title: "Grub didnt update properly...any ideas?"
date: 2010-12-30
forum: General Help
---

### Post by listerdl on 2010-12-30
I removed via synaptic old linux-headers-2.6.32.24 and .25 but for some reason they still appear in the grub boot.

I have a dual boot system.

Any ideas what has happened? I marked them for "completely remove" and let synaptic do its job.

Thanks!

---

### Post by karthick87 on 2010-12-30
Did you update your grub after removal?

```
sudo update-grub
```

---

### Post by listerdl on 2010-12-30
thanks - yes I updated using the same code as per your above post but the linux headers are still there....

Any other ideas?

Thanks!

---

### Post by karthick87 on 2010-12-30
Try removing the entry using, ubuntu-tweak.

---

### Post by listerdl on 2010-12-30
> **karthick87 said:**
> Try removing the entry using, ubuntu-tweak.

is ubuntu tweak in the repositories?

---

### Post by James78 on 2010-12-30
Not that I can see, however their website is located here.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by karthick87 on 2010-12-30
Execute the following in terminal to install ubuntu-tweak..
```
sudo add-apt-repository ppa:tualatrix/ppa
```

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-tweak
```

---

### Post by listerdl on 2011-01-02
EXCELLENT ADVICE

Thanks worked v well.

I will close this thread and recommned to anyone reading this to do what is written above

---

