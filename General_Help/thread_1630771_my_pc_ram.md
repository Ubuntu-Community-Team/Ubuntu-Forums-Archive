---
title: "my pc ram"
date: 2010-11-25
forum: General Help
---

### Post by astm on 2010-11-25
[SIZE=4]hello guys
my pc 2 GB ram ddr2
but **[COLOR=Red]i see it in ubuntu only 1 GB[/COLOR]   **](*,)
why ???????????? #-o

also you must know 
my linux partition is 10 GB and the swap partition is 1 GB 
you can see my hard partitions from this image
[/SIZE]
[IMG]http://img714.imageshack.us/img714/5552/101109144006.jpg[/IMG]
[SIZE=4]

also i want to ask about how to be the administration (root)
to open my root folder in the system files  :lol:
[/SIZE]

---

### Post by astm on 2010-11-26
:oops: [-( :-k :-\"

---

### Post by sikander3786 on 2010-11-26
Colourful bump :-)

Please post the output of

```
free
```

From Applications > Accessories > Terminal.

Root account is disabled by default (for security reasons) and you need to use **sudo** in front of any command that needs root privileges.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by astm on 2010-11-28
[SIZE=4]
hello sikander3786
you can see my print screen :confused: its only 1 GB  
how i can solve this problem ? [/SIZE]

[IMG]http://desmond.yfrog.com/Himg696/scaled.php?tn=0&server=696&filename=screenshotbq.png&xsize=640&ysize=640[/IMG]

---

### Post by sikander3786 on 2010-11-28
Yes that's showing 1 GB only.

> my pc 2 GB ram ddr2

How are you sure there is 2 GB? Please check in the Bios menu and see how much RAM is detected there. Might be just a Module or Memory Bank ran bad...

---

### Post by astm on 2010-11-28
but some one told me that the swap partition must be twice the ram 
so the swap  must be 4 GB not 1 GB

---

### Post by sikander3786 on 2010-11-28
> **astm said:**
> [SIZE=4]
but some one told me that the swap partition must be [/SIZE][SIZE=4]twice the ram 
so the swap  must be 4 GB not 1 GB [/SIZE]
So what is the actual problem? Swap is not equal to RAM X 2? Or the system is not detecting the amount of RAM you actually have? I can't understand...

---

### Post by deserthowler on 2010-11-28
> **astm said:**
> [SIZE=4]
but some one told me that the swap partition must be [/SIZE][SIZE=4]twice the ram 
so the swap  must be 4 GB not 1 GB [/SIZE]

Well, that has never happened on my set-up.  On the machine I'm using I have 2 GB ram and 1.4 GB swap.  Is that some kind of Windows rule?  :confused:  I run 6 Linux installs on machines with 2 GB RAM and have about 1.4 GB swap on all of them.  In the past few years I did about 50 installs of Linux and I don't remember any installs with the swap twice RAM.  

Earl

---

