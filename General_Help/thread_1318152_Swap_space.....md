---
title: "Swap space...."
date: 2009-11-07
forum: General Help
---

### Post by tempus on 2009-11-07
what is swap space and do i need to keep it and why. I am tryiong to install 9.04 and 9.10 sis by side and, of course, the 9.04 install does not have enough room for updates. so in the course of trying to create a large enough partition i see swap space.

---

### Post by The Cog on 2009-11-07
Swap space is used as temporary storage when ou run short of RAM. Windows uses what it calles a page file, Linux uses a swap partition. The swap partition is also used for storing what was in memory when you hibernate, so swap should be bigger than RAM.

---

### Post by tempus on 2009-11-07
> **The Cog said:**
> Swap space is used as temporary storage when ou run short of RAM. Windows uses what it calles a page file, Linux uses a swap partition. The swap partition is also used for storing what was in memory when you hibernate, so swap should be bigger than RAM.
OK So if there are 2 swap spaces because there 2 OS's side by side is it possible to know which swap goes with which OS?

---

### Post by XCan on 2009-11-07
I may be wrong, but I think it's possible for both your Ubuntu versions to use the same swap partition. If you did indeed create 2 swap partitions, I guess you should look into /etc/fstab to identify which partition goes to which OS.

---

### Post by falconindy on 2009-11-07
> **XCan said:**
> I may be wrong, but I think it's possible for both your Ubuntu versions to use the same swap partition. If you did indeed create 2 swap partitions, I guess you should look into /etc/fstab to identify which partition goes to which OS.
The above is correct. A single swap partition can be shared among 2 OS's.

---

### Post by The Cog on 2009-11-08
And if there are multiple swap partitions, **swapon -s** will tell you which ones are being used.

---

### Post by slakkie on 2009-11-08
The only problem is that Debian/Ubuntu format swap space during install, which is a bit annoying since Ubuntu uses the UUID and that changes during a format.. Best thing is to use a single swap partion and add it not with the UUID but with the normal disk notation: /dev/sdaX. 

```

sudo $EDITOR /etc/fstab

``` 

```

# swap was on /dev/sda6 during installation
#UUID=48bfd7bc-0ffe-4993-80bf-bb12d810d02a none            swap    sw              0       0
/dev/sda6        none            swap    sw              0       0

```

Best result if this is performed on both installs :).

---

### Post by The Cog on 2009-11-09
> **slakkie said:**
> The only problem is that Debian/Ubuntu format swap space during install, which is a bit annoying since Ubuntu uses the UUID and that changes during a format.. Best thing is to use a single swap partion and add it not with the UUID but with the normal disk notation: /dev/sdaX. 


Good catch. I had never noticed that.

---

### Post by sh4d0w808 on 2009-11-09
Be careful when using the same swap space for more than one system, because of hibernation.

---

### Post by kyuubi777 on 2009-11-09
swap space makes my life all warm and fuzzy-like.. :rheart:

---

