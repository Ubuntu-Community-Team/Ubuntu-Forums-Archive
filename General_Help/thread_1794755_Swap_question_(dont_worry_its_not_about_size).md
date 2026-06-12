---
title: "Swap question (dont worry its not about size)"
date: 2011-07-01
forum: General Help
---

### Post by jan-90 on 2011-07-01
So i installed ubuntu in hard disk "A" and because i read that having the swap on a HDD that is not used frequently is beneficial (makes sense after all). During installation i could not partition a swap on the HDD B so i installed without a swap.
Now if a partition a swap in HDD B (via acronis in windows set a linux swap) will ubuntu automatically detect and use it or do i need to do anything.
thanks

---

### Post by WorMzy on 2011-07-01
I believe that you'll need to create an entry for it in fstab.

Pretty simple, just open fstab:
```
gksu gedit /etc/fstab
```
add:
```
UUID=##################################### swap swap defaults 0 0
```

on a new line at the bottom of the file. Replace #####(etc) with the UUID of the swap partition, which you can find out by running
```
sudo blkid -c /dev/null
```

---

### Post by jan-90 on 2011-07-01
ok thanks i will try to do that. i should have done it with the install =/

---

### Post by jan-90 on 2011-07-05
i did that, easier than expected thanks to your steps, now is there a way to check if the OS is using it?

---

### Post by mcduck on 2011-07-05
> **jan-90 said:**
> i did that, easier than expected thanks to your steps, now is there a way to check if the OS is using it?

run "free -m" in a terminal and you should see some swap space being available.

---

### Post by WorMzy on 2011-07-05
Also,

```
swapon -s
```

will list all currently mounted swaps

---

### Post by jan-90 on 2011-07-07
thanks guys

---

