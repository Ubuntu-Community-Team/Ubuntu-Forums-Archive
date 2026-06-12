---
title: "Can't mount USB at all"
date: 2011-08-31
forum: General Help
---

### Post by SleepCat on 2011-08-31
Yep, I can't mount USB at all. It all started when I tried to find a solution on how to mount iso. I installed two scrips, and then removed them afterwards.

Now I get the message: ```
Error creating moint point: No such file or directory
```

I guess I messed up in nautilus, but I only installed and then removed two scripts? :(

---

### Post by seawolf167 on 2011-08-31
It looks like your mount point doesn't exist - try creating it first

```
mkdir /media/name-of-mount-point
```

or perhaps in

```
mkdir /mnt/name-of-mount-point
```

depending on where you want to mount the device.

What did the scripts do? What were they supposed to do? Where they just some random scripts someone posted on their blog?

---

### Post by SleepCat on 2011-08-31
Doesn't seem to work, though, ```
mkdir /mnt/name-of-mount-point
``` seemed to, but didn't make a difference.

Well, I tried this: [http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

---

### Post by seawolf167 on 2011-08-31
Did you follow all the steps in the instructions exactly as listed? Were there any errors when attempting any of the steps?

Can you mount the .iso files manually? This is described on the link you provided under "Using loop Kernel Module"

---

### Post by SleepCat on 2011-08-31
Yes, I followed it and didn't get any errors.

Hmm. Not sure. I don't think so actually.

---

