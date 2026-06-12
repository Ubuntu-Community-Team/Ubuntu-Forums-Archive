---
title: "update problem"
date: 2009-09-13
forum: General Help
---

### Post by 37fleetwood on 2009-09-13
I'm getting a notification that the update information is outdated. when I click on it it starts and then crashes. the same happens for both synaptic in the system/administration menu, and Add/Remove in the Applications menu. any help overcoming this would be appreciated. here is a cap of the notification:
[IMG]http://i14.photobucket.com/albums/a315/hotshot66/puppy/info.jpg[/IMG]

---

### Post by MelDJ on 2009-09-13
what version of ubuntu are you using?

---

### Post by codemyster on 2009-09-13
Try updating from the terminal using apt.

sudo apt-get upgrade

---

### Post by 37fleetwood on 2009-09-13
> **codemyster said:**
> Try updating from the terminal using apt.

sudo apt-get upgrade

I'm running 9.04 (sorry I forgot to add that)
here's what I get from the terminal:
```
scott@scott-desktop:~$ sudo apt-get upgrade
[sudo] password for scott: 
Reading package lists... Done
Segmentation faulty tree... 50%
scott@scott-desktop:~$ 

```

---

### Post by MelDJ on 2009-09-13
try this thread: [http://ubuntuforums.org/showthread.php?t=1010569](http://ubuntuforums.org/showthread.php?t=1010569)

---

### Post by codemyster on 2009-09-13
Apparently that's an odd problem with apt-get exclusively. Try running,

```

sudo -s
cd /var/cache/apt
mv *.bin backup
apt-get update
apt-get upgrade

```

If that doesn't work and/or produces more errors,

```

mv ./backup/*.bin /var/cache/apt

```

Will restore it to the way it was before. Still segfaulting, though.

---

### Post by 37fleetwood on 2009-09-13
> **codemyster said:**
> Apparently that's an odd problem with apt-get exclusively. Try running,

```

sudo -s
cd /var/cache/apt
mv *.bin backup
apt-get update
apt-get upgrade

```

If that doesn't work and/or produces more errors,

```

mv ./backup/*.bin /var/cache/apt

```

Will restore it to the way it was before. Still segfaulting, though.

this seems to have fixed it!
Thanx!!
Scott:D

---

