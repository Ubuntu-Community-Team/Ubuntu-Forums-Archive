---
title: "error on update"
date: 2010-08-16
forum: General Help
---

### Post by caro on 2010-08-16
Lately I sometimes get the error message:

```
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
```

when I try to update.  I get this using both the Update Manager or using 

```
sudo apt-get update
sudo apt-get upgrade
```

Any ideas?

---

### Post by wojox on 2010-08-16
It usually means you have more then one package manager open. Are you running apt-get with synaptic or software center open? Try logging out and back in.

---

### Post by caro on 2010-08-16
I only had the Upgrade Manager open, but I'll give it a shot.

Update:  No luck.  Same error message as before.

---

### Post by wojox on 2010-08-16
Try running

```
sudo dpkg --configure -a
```

and 

```
sudo apt-get install -f
```

---

### Post by caro on 2010-08-16
For whatever reason, after leaving my computer for a few minutes, the update ran with no problem.  I noticed that all the updates had completed downloading in the background when it ran successfully so don't know if that had something to do with it.  

Thanks everyone.

---

### Post by Yumi on 2010-08-16
You get the same error message when you have Nautilus File Manager or Synaptic Package Manager open. Must close those to run Update Manager

Michael

---

### Post by caro on 2010-08-17
> **Yumi said:**
> You get the same error message when you have Nautilus File Manager or Synaptic Package Manager open. Must close those to run Update Manager

Michael

Neither of these were open.  All that I had running were the Update Manager and Firefox.  The computer had only been booted up for less than an hour and the only other program launched was Thunderbird.

---

