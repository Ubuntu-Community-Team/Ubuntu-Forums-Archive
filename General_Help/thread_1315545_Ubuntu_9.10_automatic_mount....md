---
title: "Ubuntu 9.10 automatic mount..."
date: 2009-11-05
forum: General Help
---

### Post by jiapei100 on 2009-11-05
Whenever I plugin my external hard drive to my laptop with Ubuntu 9.10, I managed to mount it to

```
/media/"UUID of the external hard drive"
```

I seriously hate this UUID because I've got accustomed to mount it to something like

```
"/media/disk"
```


I know that I can manage to mount it manually. I even changed fstab or mtab.

But, I would like to finish the task like

```
"Whenever I plugin my external hard drive 
(not the case I plugin first and then reboot my computer, no ), 
I would like my external hard drive can be 
automatically mount to "/media/disk" ".
```

So, how can I do that please?

Best Regards
JIA

---

### Post by Giblet5 on 2009-11-05
When you create a filesystem on any drive, you have the option of applying a "label" to that volume.

```
man mkfs
```

I'm a recovering pun addict, so I always set my volume label to some form of volume measurement:

Gallons
Decibels
Loudness
Litres
Quartz (double pun fix)

When automounting a volume, HAL will use the volume label if one is present.

---

### Post by alphaniner on 2009-11-05
You can also apply a label to an existing filesystem, can't you?

---

### Post by jiapei100 on 2009-11-05
Thank you so much for your prompt reply !!!

But in my case, I've alreay have this external hard drive at hand and I really dont' want to recreate the filesystem for my external hard drive, can I add a "label" to this volume afterwards?

Best Regards
JIA

> **Giblet5 said:**
> When you create a filesystem on any drive, you have the option of applying a "label" to that volume.

```
man mkfs
```

I'm a recovering pun addict, so I always set my volume label to some form of volume measurement:

Gallons
Decibels
Loudness
Litres
Quartz (double pun fix)

When automounting a volume, HAL will use the volume label if one is present.

---

### Post by jiapei100 on 2009-11-05
Perfect, I got it.

[http://ubuntuforums.org/showthread.php?t=423245](http://ubuntuforums.org/showthread.php?t=423245)

```
e2label device <labelname>
```

thanks man !!!

---

### Post by Giblet5 on 2009-11-05
You're quicker than I am!

And you're welcome.

---

