---
title: "Unable to Detect...?"
date: 2011-03-31
forum: General Help
---

### Post by khoraski on 2011-03-31
When I boot into Ubuntu, the screen stays black for like 2 minutes, and then I get a message "Unable to detect..." but it goes by too fast to read. Then Ubuntu starts up in like a second. 

How could I fix this? If I can, I can boot my PC in less than 10 seconds.

---

### Post by wojox on 2011-03-31
What graphic chip:

```
lspci | grep VGA
```

---

### Post by khoraski on 2011-03-31
> **wojox said:**
> What graphic chip:

```
lspci | grep VGA
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

---

### Post by Rubi1200 on 2011-04-01
You could also try this:

```
dmesg | less
```

Look if there are messages related to "unable to detect" to try and find out what is going on.

---

### Post by khoraski on 2011-04-01
> **Rubi1200 said:**
> You could also try this:

```
dmesg | less
```

Look if there are messages related to "unable to detect" to try and find out what is going on.

These are all the ones I found:

```
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
```
```
[   18.033733] acer-wmi: Unable to detect available WMID devices
```

---

### Post by Rubi1200 on 2011-04-01
Regarding the second message you found, this appears to be a known bug on Acer Aspire models:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560464?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560464?comments=all)

A quick look through the bug report and some threads does not turn up an immediate solution.

What version of Ubuntu are you using?

---

