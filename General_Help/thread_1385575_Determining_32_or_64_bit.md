---
title: "Determining 32 or 64 bit?"
date: 2010-01-19
forum: General Help
---

### Post by Ted3929 on 2010-01-19
Just got a Lenovo laptop from a guy who butchered his installation of Super OS and ended up with a mishmash.

Problem is the Lenovo 3000 N200 series came as both a 32 bit and 64 bit system but the difference depends upon what the original buyer opted for.

Owner thinks he installed the 64 bit Super OS version but is there anyway of telling off the menu?  I've been poking around but haven't been too lucky yet.  I know it's Super OS 9.10.

In case you don't know, Super OS 9.10 is nothing but Karmic Koala with some tweaks and extra programs.

Thanks!

---

### Post by howefield on 2010-01-19
Do you want to know what is installed or if the processor is 64 bit ?

If the latter, type the following into a terminal

```
cat /proc/cpuinfo
```

Look at the clfush size, and also "lm" in the flags signifies 64 bit processor.

If the former, type this instead

```
uname -a
```

---

### Post by audiomick on 2010-01-19
Hallo.
In the terminal
```
uname -a
```
gives me
```
mick@ubuntu-desktop:~$ uname -a
Linux ubuntu-desktop 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 [COLOR="Red"]x86_64[/COLOR] GNU/Linux

```
which I think is all you need to know, isn't it?

---

### Post by Ted3929 on 2010-01-19
yes, that should do it!  thanks!

---

### Post by steveneddy on 2010-01-19
sudo lshw -c cpu

for more cpu info

---

