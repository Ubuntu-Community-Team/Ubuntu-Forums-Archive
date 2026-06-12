---
title: "allocate memory problem"
date: 2010-04-24
forum: General Help
---

### Post by morvol on 2010-04-24
Hello. When i am trying to install a package i get this error

```
fork: Cannot allocate memory
/lib/lsb/init-functions: fork: Cannot allocate memory
basename: memory exhausted
```

I had the same problem in my website too...When i was trying to access my website i was getting error that cannot allocate memory on a file.

I have a vps with Burstable Memory 512 and Guaranteed Memory 256 if this is something you need to know


thx for your time :D

---

### Post by geirha on 2010-04-24
What does the **free** command say?

---

### Post by morvol on 2010-04-24
```
             total       used       free     shared    buffers     cached
Mem:        524288     248424     275864          0          0          0
-/+ buffers/cache:     248424     275864
Swap:            0          0          0


```

---

### Post by geirha on 2010-04-24
Ok, not sure how that Burstable Memory and Guaranteed Memory works, but I'm guessing you are exceeding that 256MiB of Guaranteed Memory when you get the memory exhausted message.

I suggest you create a swap partition/file. [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by morvol on 2010-04-24
i got this error

```
swapon: /mnt/512Mb.swap: swapon failed: Operation not permitted
```

is there a problem on my vps? or i have to chmod a file?

---

### Post by geirha on 2010-04-24
That last command there must be run as root. Did you run it as root? i.e.
```
**sudo** swapon /mnt/512Mb.swap
```

---

### Post by morvol on 2010-04-24
yes i did

---

### Post by geirha on 2010-04-24
Then it sounds like the VPS has some additional limitations. I'm not familiar with this, and I think it's best to consult the ones that host your VPS to figure out what options you have.

---

### Post by morvol on 2010-04-24
ok :d thx for your support btw

---

### Post by xifer on 2010-04-24
also i don't know about requesting more memory from the host but if you can't then you might try booting into runlevel 3 (i.e. without X11) - install the package from command line then continue and see if it runs

---

