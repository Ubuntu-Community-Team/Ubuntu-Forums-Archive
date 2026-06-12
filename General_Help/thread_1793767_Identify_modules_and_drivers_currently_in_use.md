---
title: "Identify modules and drivers currently in use?"
date: 2011-06-30
forum: General Help
---

### Post by Bucky Ball on 2011-06-30
Hi all,

Is there anyway of identifying which modules and drivers are being used on my machine? A log or app?

I have a minimal install and what to install another, this time with only the hardware drivers/modules my machine needs (for instance, I don't need software for Xeon processors as I don't have one, therefore don't want that stuff hanging around serving no purpose). 

I'm looking to get barebones as possible with only what I need to work on the install.

Cheers. ;)

---

### Post by sandman887 on 2011-06-30
You can type the command: 

```
lsmod | more
```

That shows all the modules that the kernel is currently using.

---

### Post by arius13721 on 2011-06-30
I don't know if it's worth noting, but as it stands now, your system only loads the drivers/modules it requires, so really, at best, you'll probably only save a few MB by trying to customize for your exact hardware.

---

### Post by Bucky Ball on 2011-06-30
> **arius13721 said:**
> I don't know if it's worth noting, but as it stands now, your system only loads the drivers/modules it requires, so really, at best, you'll probably only save a few MB by trying to customize for your exact hardware.

I'm with ya. Just interested to install only the ones I need in the first place and have no (or little) bloat whatever. A phase I'm going through; probably work my way through it ... ;)

---

### Post by Gyokuro on 2011-06-30
Or you can compile your own kernel - however you have always to do it yourself in case there are kernel updates get pushed out via updates (or you use a vanilla kernel from kernel.org). More information to do it the Ubuntu way you can find here: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile) 

an Ubuntu kernel config file will you find in /boot or start from scratch via a make menuconfig :-)

---

### Post by Bucky Ball on 2011-06-30
The menuconfig is the way but not sure what to choose in the process which is why I was wondering if there was a way I could find out what is being used now so I only select and install those during the menuconfig.

---

### Post by andrewthomas on 2011-06-30
Take the results of lspci -n and paste them at the following site: [http://kmuto.jp/debian/hcl/](http://kmuto.jp/debian/hcl/)

For more information, visit:

[http://www.kernel-seeds.org/working.html](http://www.kernel-seeds.org/working.html)

If you are looking for a minimal system that is optimized for what you have, then take the plunge and install Gentoo.

---

### Post by SeijiSensei on 2011-07-01
You can delete all the modules you want, but if there's a kernel upgrade, you'll get them all over again.

On my 10.10 system, /lib/modules/2.6.35-28-generic comes in at about 140 MB.  On modern systems with enormous hard drives, that's a drop in the bucket.

I often read postings here where people are trying to reduce "bloat" by deleting files, usually applications.  Unless you're starved for hard drive space, that seems a pretty fruitless enterprise to me.  Having more objects stored on the hard drive doesn't slow down performance, which is what I think most people mean when they speak of "bloat."

---

### Post by Bucky Ball on 2011-07-01
> **andrewthomas said:**
> Take the results of lspci -n and paste them at the following site: [http://kmuto.jp/debian/hcl/](http://kmuto.jp/debian/hcl/)

For more information, visit:

[http://www.kernel-seeds.org/working.html](http://www.kernel-seeds.org/working.html)

If you are looking for a minimal system that is optimized for what you have, then take the plunge and install Gentoo.

Cheers. Great info. Just what I was looking for. The list from the first link would be handy for the menuconfig I'm thinking. The second link I am currently investigating and will try working with a 'seed' tomorrow. The plunge into Gentoo is an ocean too deep at this point ... :)

SeijiSensei: Program bloat, yes, but I'm thinking more of getting rid of the heap of device drivers (all there in case you have the hardware, like the stuff to make a P4 processor work, but I don't have one).

See this as an exercise rather than much else. I hear and know what you're saying ... ;)

---

