---
title: "Swap Space always 0 in use"
date: 2010-12-27
forum: General Help
---

### Post by saidbakr on 2010-12-27
Hi,

I have 1 GB of RAM. I have made a single partition for Swap during disk partition. I use applet for System monitor that display some system data such as Memory usage and Swap. The swap always shows 0 in use. I opened many application and it seems to be the same at 0.

Please look at the attached image.

---

### Post by gmargo on 2010-12-27
What is the result of running the **free(1)** command?  That will tell if your swap is enabled.

---

### Post by matt_symes on 2010-12-27
Hi

You have hooked up your swap in fstab?
swap is on using 

```
swapon
```

It might just be the case the Ubuntu does not need swap in normal running on your machine.

You will still need it if you hibernate as memory gets written to the swap area on the hard drive. 

Kind regards

---

### Post by The Cog on 2010-12-27
Have a look at the output of the command **free**. This should tell you how much swap you have and how much is in use:

```
:~$ free
             **total       used       free**     shared    buffers     cached
Mem:       3568864     681344    2887520          0        880     448344
-/+ buffers/cache:     232120    3336744
**Swap:      [COLOR="DarkRed"]5116664          0    5116664[/COLOR]**
```

---

### Post by mcduck on 2010-12-27
> **saidbakr said:**
> Hi,

I have 1 GB of RAM. I have made a single partition for Swap during disk partition. I use applet for System monitor that display some system data such as Memory usage and Swap. The swap always shows 0 in use. I opened many application and it seems to be the same at 0.

Please look at the attached image.

It should also be told that you actually *don't want* to use swap.

It might be necessary to sue it if you need to run a program that requires more RAM than you r computer has available. But using the hard drive instead of RAM to store data is ridiculously slow, and definitely something you want to avoid as long as you possibly can.

So, as long as you have some swap space configured, you can be happy about it not being used. :D

---

### Post by saidbakr on 2010-12-27
> **The Cog said:**
> Have a look at the output of the command **free**. This should tell you how much swap you have and how much is in use:

```
:~$ free
             **total       used       free**     shared    buffers     cached
Mem:       3568864     681344    2887520          0        880     448344
-/+ buffers/cache:     232120    3336744
**Swap:      [COLOR=DarkRed]5116664          0    5116664[/COLOR]**
```

Using free command returns for Swap: 4384760          0    4384760

---

### Post by wojox on 2010-12-27
> **saidbakr said:**
> Using free command returns for Swap: 4384760          0    4384760

So your fine. If it wasn't enabled you'd have 0 0 0.

If you want to try it out, download a torrent file from Ubuntu. While watching youtube in one browser tab and looking at Google Images in another.

---

### Post by saidbakr on 2010-12-27
> **wojox said:**
> So your fine. If it wasn't enabled you'd have 0 0 0.

If you want to try it out, download a torrent file from Ubuntu. While watching youtube in one browser tab and looking at Google Images in another.

Thank you all!:p

---

