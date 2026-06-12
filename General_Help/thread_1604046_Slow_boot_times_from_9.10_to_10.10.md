---
title: "Slow boot times from 9.10 to 10.10"
date: 2010-10-23
forum: General Help
---

### Post by liquidcross on 2010-10-23
I'm running 10.10 on an IBM Thinkpad R60 with 3GB RAM. I did a clean install of 9.10 and 10.04, and recently upgraded to 10.10. With all three, I'm noticing something rather strange; after passing the PC's BIOS screen, I get a flashing cursor for about 20-30 seconds before Ubuntu starts booting. When I did the clean installs, I completely erased the hard drive, so I'm not sure what's causing it. The hard drive activity light is on when this happens, as well. It's very strange, as I have an old Dell Dimension 4550 with a slower hard drive and less RAM than the Thinkpad...yet it boots up faster, with no flashing cursor.

Any advice? Thanks in advance...

---

### Post by zasq on 2010-10-24
Hello.
I have exactly the same problem on a Dell Inspiron 1501. I updated from 10.04. Some days ago there was a text about a bug after bios showed, but that disappeared now. Booting time (between bios and showing the ubuntu splash is still very long. If there is any more information I can provide to solve this, please let me know.

---

### Post by ChadiM on 2010-10-24
I also have the same problem, hp pavilion dv3 2270ev.

---

### Post by liquidcross on 2010-10-27
I tried updating the BIOS on my laptop to the latest version, but that didn't help. Still got the blinking cursor and the slow loading.

---

### Post by lavinog on 2010-10-27
Install bootchart and post the bootchart (located in /var/log/bootchart)

I wonder if there may be an issue with old ureadahead data from lucid.
You can purge the ureadahead data with the following command:
```

sudo rm -v /var/lib/ureadahead/*pack*

```
It will regenerate on the next boot.

Also if you have a slowness issue, please specify if you upgraded from 10.04 or if you did a clean install, and if you are using proprietary drivers such as the nvidia or fglrx driver.

---

### Post by liquidcross on 2010-10-27
Bootchart log image is attached. I am not using any proprietary drivers. I did an upgrade from 10.04 to 10,10, but as I stated earlier, I had the slowdown problem when I did clean installs for 9.10 and 10.04.

---

### Post by lavinog on 2010-10-28
I am not able to read the bootchart because of the autoresize feature of the forum.  Can you zip it then upload it.

---

### Post by liquidcross on 2010-10-28
Sorry about that. Try it now?

---

### Post by lavinog on 2010-10-29
Your bootchart shows a 25s boot time which is not bad.

The disk activity appears to stall during the ureadahead phase.

How full was your drive when you updated?
```

df -f

```

---

### Post by liquidcross on 2010-10-29
> **lavinog said:**
> Your bootchart shows a 25s boot time which is not bad.

The disk activity appears to stall during the ureadahead phase.

How full was your drive when you updated?
```

df -f

```
I got **df: invalid option -- 'f'** when I tried that.

Anyway, the only thing on there when I upgraded was Ubuntu itself, a few text documents, and one or two small programs like Thunderbird. The disk was mostly empty.

---

### Post by lavinog on 2010-10-29
Not sure what I was thinking.
I meant ```
df -h
```

Usually the boot splash will not display until ureadahead reads all of the pack data, which looks like it takes about 10 seconds.

you can use the following to list the contents of the ureadahead pack files and see if there are some files that require a lot of data to be read.

```

sudo ureadahead --dump

```

For instance, I just found this entry:
```

/usr/lib/libclamav.so.6 (8885 kB), 13 blocks (8184 kB)
  [@#########################################################################]
  [##########################################################################]
  [############################################.....................@########]
  [##########################################################################]
  [##########################################################################]
  [##########################################################################]
  [##########################################################################]
  [################################.@########################################]
  [##########################################################################]
  [#############################################################.@###########]
  [####################...@##################################################]
  [#####################################################################.....]
  [......@###############################################..........@#########]
  [##########################################################################]
  [##########################################################################]
  [########.....................@###############################......@######]
  [#########################...@#############################################]
  [##########################################################################]
  [##########################################################################]
  [##########################################################################]
  [##########################################################################]
  [####################..@###################################################]
  [#############################################......@######################]
  [##########################################################################]
  [##########################################################################]
  [##########################################################################]
  [##########################################################################]
  [###################################.......................................]
  [....................................................@#####################]
  [##########################################################################]
  [##                                                                        ]

	8699904, 401408 bytes (at 2034757632)
	0, 786432 bytes (at 2046820352)
	872448, 1380352 bytes (at 2047692800)
	2256896, 720896 bytes (at 2049077248)
	2981888, 131072 bytes (at 2049802240)
	3125248, 491520 bytes (at 2049945600)
	3661824, 196608 bytes (at 2050482176)
	3899392, 679936 bytes (at 2050719744)
	4665344, 131072 bytes (at 2051485696)
	4820992, 131072 bytes (at 2051641344)
	4964352, 1482752 bytes (at 2051784704)
	6455296, 397312 bytes (at 2053275648)
	6877184, 1449984 bytes (at 2053697536)


```

It belongs to clamav's freshclam and I don't run clamav that often, so I just removed it.  I just apt-get remove clamav and did an apt-get autoclean afterward.

---

### Post by liquidcross on 2010-10-30
Results of df -h are as follows:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   28G   40G  41% /
none                  1.5G  260K  1.5G   1% /dev
none                  1.5G  252K  1.5G   1% /dev/shm
none                  1.5G   88K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
none                  1.5G     0  1.5G   0% /lib/init/rw
```
How can I get that ureadahead command to output to a file? I ran it, but the results scrolled offpage and I can't see the entire output.

---

### Post by liquidcross on 2010-11-08
Has anyone been able to figure this out yet? I'm still stumped.

---

### Post by vladcambridge on 2010-11-08
I had a similar issue, uninstalled compiz and the system seems to have started working faster, you could try giving it a shot.

---

### Post by liquidcross on 2010-11-08
What's compiz?

---

