---
title: "No Plymouth splash screen after going GRUB 1.99?"
date: 2012-04-18
forum: General Help
---

### Post by Jamie_Edwards on 2012-04-18
Hi guys,

Before we start I have Ubuntu 11.04 as my primary and only OS! :lolflag:

Before I fiddled with GRUB I had Plymouth giving me the splash screen during bootup/shutdown that all of us may know and love.

Now a couple of days ago I installed/updated GRUB 1.99 which I guess is actually GRUB2? or is it GRUB Legacy? 

I'm digressing a little so anyway, after this, I did the normal restart to find that my lovely Plymouth splash screen has gone ( or not showing ) from both the shutdown and bootup process, showing the disgusting workings of the kernel.

Any idea's what I did? And more importantly... How it can be fixed?

Thanks.

Jamie.

---

### Post by al111 on 2012-04-18
Take a look at -> 

[Super Boot Manager]("http://www.ubuntugeek.com/super-boot-manger-make-easier-and-intuitive-configuration-of-grub-burg-and-plymouth.html")

[Plymouth Manager]("http://www.noobslab.com/2011/07/plymouth-manager-on-ubuntu-1104-natty.html")

---

### Post by Jamie_Edwards on 2012-04-19
> **al111 said:**
> Take a look at -> 

[Super Boot Manager]("http://www.ubuntugeek.com/super-boot-manger-make-easier-and-intuitive-configuration-of-grub-burg-and-plymouth.html")

[Plymouth Manager]("http://www.noobslab.com/2011/07/plymouth-manager-on-ubuntu-1104-natty.html")

Didn't work, still seeing the the startup process :L](*,)

---

### Post by josephmills on 2012-04-19
try this 
in termianl 
```
$ sudo update-alternatives --config text.plymouth

```

pick the one you want to use 
then 

```
$ sudo update-alternatives --config default.plymouth

```

then 


```
 sudo update-initramfs -u

```

then reboot 

anything ?

---

### Post by Jamie_Edwards on 2012-04-19
> **josephmills said:**
> try this 
in termianl 
```
$ sudo update-alternatives --config text.plymouth

```

pick the one you want to use 
then 

```
$ sudo update-alternatives --config default.plymouth

```

then 


```
 sudo update-initramfs -u

```

then reboot 

anything ?

Nope, exact same output as before :L

---

