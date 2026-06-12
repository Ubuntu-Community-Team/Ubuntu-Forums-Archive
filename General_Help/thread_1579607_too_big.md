---
title: "too big"
date: 2010-09-22
forum: General Help
---

### Post by petrasflorin on 2010-09-22
so I've installed ubuntu 4 days ago, it's installed in dual-boot mode along with windows 7.

windows 7 is in C:
ubuntu installed in D:

however, when going back to windows, in the ubuntu folder there's one SINGLE big file, root.disk - 19.8 GB.

Whoever told me Ubuntu is small lied.

No, there is NOTHING installed and no music/movies downloaded.
I even removed some of the programs I didn't use.

anyone care to enlighten me ? why the size?!

---

### Post by baddog144 on 2010-09-22
I don't know for sure, but I'd guess that file is all the space you could potentially use with your install. Wubi doesn't expand it as you need more space, I'd guess.

---

### Post by petrasflorin on 2010-09-22
what does that mean ? it takes 20 GB "just in case" ?! lol.

---

### Post by Elfy on 2010-09-22
Did you not get asked how big to make the wubi install during the install? If not possibly wubi uses a percentage of the free space - that though is a guess.

I have to say that I only tried looking at wubi once and can not remember.

---

### Post by mcduck on 2010-09-22
> **petrasflorin said:**
> what does that mean ? it takes 20 GB "just in case" ?! lol.

It does it to give you some room to actually have some files and install some programs in Ubuntu. If the virtual filesystem Wubi creates would be the exact size of Ubuntu & included programs you wouldn't even be able to create a single-word text file in there, as you'd have no space to store it.

By the way, you *didn't * install Ubuntu as dual-boot, you installed it inside Windows, using Wubi. So you are not looking at the size of Ubuntu, you are looking at the size of the virtual filesystem Wubi created for you, inside your Windows filesystem. (In the same way if you install Windows on a 500GB  hard drive you are using the 500GB of drive space, but that doesn't mean that Winsows would need 500GB, only that that's how much space you gave it)

---

### Post by nothingspecial on 2010-09-22
> **petrasflorin said:**
> 

Whoever told me Ubuntu is small lied.



No they didn`t :)
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             9.2G  2.8G  6.0G  32% /
```

I seem to be wasting 6G of space.

---

### Post by petrasflorin on 2010-09-22
What ubuntu are you using ?
That can't be right.

A 2.8 gig /
... come on man !

ok im reinstalling. just ubuntu. no windoze.

making 10g / , 6g swap (double the ram, right ?) and /home for the rest.

anyway... space isn't a problem im running on a ws 1 TB black edition but I just didn't understand how'd it get so BIG

---

### Post by nothingspecial on 2010-09-22
> **petrasflorin said:**
> What ubuntu are you using ?
That can't be right.

A 2.8 gig /


Sorry, your right, that`s my lubuntu partition, my ubuntu one on /dev/sda1 takes a whopping 3.3G

Again, sorry for the confusion:)

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             9.2G  2.8G  6.0G  32% /
none                  493M  280K  492M   1% /dev
none                  497M  104K  497M   1% /dev/shm
none                  497M  116K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
/dev/sda6             126G   18G  102G  15% /home
[COLOR=Red]/dev/sda1             9.2G  3.3G  5.5G  38% /media/disk[/COLOR]
```

---

### Post by Chame_Wizard on 2010-09-22
And it's even not installed?
19.8 GiB is enough to do a fully install of *Buntu.:popcorn:

---

### Post by SlugSlug on 2010-09-22
> **petrasflorin said:**
> What ubuntu are you using ?
That can't be right.

A 2.8 gig /
... come on man !

ok im reinstalling. just ubuntu. no windoze.

making 10g / , 6g swap (double the ram, right ?) and /home for the rest.

anyway... space isn't a problem im running on a ws 1 TB black edition but I just didn't understand how'd it get so BIG


6gig swap is crazy!

I have 4GB ram and 2gb swap -- swap never uses 100MB+


Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb6             9.8G  3.7G  5.6G  40% /
/dev/sdb3             9.9G  2.4G  7.0G  26% /home

---

### Post by mcduck on 2010-09-22
> **SlugSlug said:**
> 6gig swap is crazy!

I have 4GB ram and 2gb swap -- swap never uses 100MB+


If you want to suspend the machine, though, you'll need at as much swap space as the data currently in RAM takes (excluding buffers & cache).

On the other hand I bet most people having more than 2GB of RAM will never actually use all of it for anything else than cache, so something around 2 or 3 GB of swap should be enough for suspending the machine. Having as much swap as you have RAM would of course make it absolutely sure that suspend works in every situation, and considering the cost of a GB of disk space even that shouldn't be a problem for most people. But I agree that the old swap=2xRAM rule is a thing of past and should be ignored.

---

### Post by SlugSlug on 2010-09-22
> **mcduck said:**
> If you want to suspend the machine, though, you'll need at as much swap space as the data currently in RAM takes (excluding buffers & cache).

On the other hand I bet most people having more than 2GB of RAM will never actually use all of it for anything else than cache, so something around 2 or 3 GB of swap should be enough for suspending the machine. Having as much swap as you have RAM would of course make it absolutely sure that suspend works in every situation, and considering the cost of a GB of disk space even that shouldn't be a problem for most people. But I agree that the old swap=2xRAM rule is a thing of past and should be ignored.


ahh yer..  I dnt use suspend

---

### Post by petrasflorin on 2010-09-22
I use suspend - not hibernate.
Suspend is kinda the same thing but faster - saves energy - meh I'm running a plugged in 24/7 Desktop anyway.

ok I'll do a 4GB swap then.
and by the looks of it, 10GB for the root seems to be... enough.

---

