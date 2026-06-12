---
title: "Is there a 64 bit Intel distribution?"
date: 2010-11-13
forum: General Help
---

### Post by lone_wolfII on 2010-11-13
I just bought a computer from a company that was having a fire sale. 

Anyway I figured that I'd give Ubuntu another shot. I installed 10.10 yesterday without any real idea of what was in the box. 

I ran ```
sudo lshw -html > hardware.html
```

I've got an Intel E6600, which is 64 bit. I've installed Ubuntu 10.10 desktop. 

Is this the right distro for this box? I'm not sure if the distro is 64 bit. There's an AMD64 version, but is that only for AMD chips? 

How do I tell if I'm running a 64 bit or 32 bit distro?

Thanks.

---

### Post by amauk on 2010-11-13
The AMD bit is a bit misleading

AMD64 is for both AMD & Intel 64bit CPUs

(AMD beat Intel to market with a x86_64 CPU, so they got to name the architecture)

---

### Post by lone_wolfII on 2010-11-13
Awesome. I'll start downloading the 64 bit version now. 

I'm guessing there's not an easy way to install the 64 bit version without losing what I've currently got installed, is there? 

I've got /home as a separate partition, but that's about it.

---

### Post by amauk on 2010-11-13
> **lone_wolfII said:**
> Awesome. I'll start downloading the 64 bit version now. 

I'm guessing there's not an easy way to install the 64 bit version without losing what I've currently got installed, is there? 

I've got /home as a separate partition, but that's about it.

Unless you format /home, you won't "lose" anything

All your personal files & settings are stored in /home

Just reinstall (while preserving /home), and everything will be the same

---

### Post by i.r.id10t on 2010-11-13
I've not felt the need to upgrade to a 64bit Linux OS yet... using the -pae kernel, my full 8gb of ram is recognized, and I don't have to go thru the hassle of 64bit driver support, plugin support, etc.  Of course, I've got the hardware so when it pretty much just works in 64bit land I'll be able to move over...

---

### Post by amauk on 2010-11-13
PAE is fine for most things, but it is a hack to overcome the inherent limitations of the 32bit architecture

Under PAE, while the OS can "see" above 4Gb of RAM, no single process can use more than 3Gb at a time.
You also can't memory-map more than 3Gb either.

Under 64bit, there are no such limitations

---

### Post by TheForkOfJustice on 2010-11-13
> **i.r.id10t said:**
> I've not felt the need to upgrade to a 64bit Linux OS yet... using the -pae kernel, my full 8gb of ram is recognized, and I don't have to go thru the hassle of 64bit driver support, plugin support, etc.  Of course, I've got the hardware so when it pretty much just works in 64bit land I'll be able to move over...

Seriously, go 64-bit.

I use it with no issues, as do other, with no driver issues at all.  If you install it on a separate partition you can decide whether or not to fully migrate after you install all of the drivers.

---

