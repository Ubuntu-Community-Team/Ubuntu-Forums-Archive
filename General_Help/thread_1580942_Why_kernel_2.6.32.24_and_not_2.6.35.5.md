---
title: "Why kernel 2.6.32.24 and not 2.6.35.5?"
date: 2010-09-24
forum: General Help
---

### Post by pdkta on 2010-09-24
Why ubuntu updating to kernel 2.6.32-24 and not 2.6.35.5? Isn't the last kernel model supposed to be the best one? (Sorry my English are not very good)

---

### Post by dcstar on 2010-09-24
> **pdkta said:**
> Why ubuntu updating to kernel 2.6.32-24 and not 2.6.35.5? Isn't the last kernel model supposed to be the best one? (Sorry my English are not very good)

Ubuntu releases only have the kernel version used when originally released for stability and compatibility.

Ubuntu is **not** a "bleeding edge" distro that is continually updated with the latest package versions. There are plenty of other alternatives available if you want that.

---

### Post by halj32 on 2010-09-24
there is no reason not to use the 2.6.35.* kernels, I use them in Ubuntu (Dell laptop)& the only problem I had was with the BCM wifi you need to do 2 patchs. If you do a search of my posts you will learn how to do it.

---

### Post by snowpine on 2010-09-24
Next month's Ubuntu 10.10 will have the 2.6.35 kernel. :)

---

### Post by CoolJohnB on 2010-09-24
I am using Ubuntu 10.10 Beta and that has the 2.6.35-22 kernel, works great.

---

### Post by SlugSlug on 2010-09-24
> **halj32 said:**
> there is no reason not to use the 2.6.35.* kernels, I use them in Ubuntu (Dell laptop)& the only problem I had was with the BCM wifi you need to do 2 patchs. If you do a search of my posts you will learn how to do it.


without reading a massive change log -- is there much difference?

---

### Post by Frogs Hair on 2010-09-24
There is most likely a reason Lucid is not running the latest kernel , but thats not to say that using it will cause a problem.

---

### Post by mikewhatever on 2010-09-24
> **pdkta said:**
> Why ubuntu updating to kernel 2.6.32-24 and not 2.6.35.5? Isn't the last kernel model supposed to be the best one? (Sorry my English are not very good)

I am currently using 2.6.31 - Karmic. Any reason to switch?

---

### Post by snowpine on 2010-09-24
> **Frogs Hair said:**
> There is most likely a reason Lucid is not running the latest kernel

The reason is that Lucid was released April 2010 (that's what the "10.04" designates) and uses the stable kernel as of that date.

---

### Post by sh4d0w808 on 2010-09-24
Ubuntu doesn't change main versions of any software within a release (except Firefox). Of course, can download a new kernel source, configure and compile it, it will work, but then you have to update it manually.

---

### Post by philinux on 2010-09-24
> **dcstar said:**
> Ubuntu releases only have the kernel version used when originally released for stability and compatibility.

Ubuntu is **not** a "bleeding edge" distro that is continually updated with the latest package versions. There are plenty of other alternatives available if you want that.

Looks like there is a kernel update pending for lucid. Most likely bug or security update.

2.6.32-25.44
[http://people.canonical.com/~ubuntu-archive/pending-sru.html](http://people.canonical.com/~ubuntu-archive/pending-sru.html)

---

### Post by halj32 on 2010-09-24
> **SlugSlug said:**
> without reading a massive change log -- is there much difference?

apart from the bcm wifi on my laptop it boots a little quicker & uses a little less memory also the GUI seems brighter & sharper.

---

### Post by pdkta on 2010-09-28
the kernel 2.6.32-24 had some incompatibility with the ati proprietary driver fglrx. I hope it solved in 2.6.32-25

---

### Post by JoelOl75 on 2010-09-28
There is a good reason... well two actually, why the 2.6.32 line is being used in Lucid.  

The main one is that Lucid is a LTS and checking on kernel.org the 2.6.32 kernel will receive driver backports for an extended period of time, even longer than newer kernels.

Also once the release is frozen, only bug fixes will find their way into the kernel, not new features (Which may break that much-needed-to-be-rock-solid server running LTS) 

Hard to explain but these articles may help:

Mainly why the 2.6.32 kernel IS THE ONE TO STAY WITH:
[http://www.phoronix.com/scan.php?page=news_item&px=Nzg5MQ](http://www.phoronix.com/scan.php?page=news_item&px=Nzg5MQ)

Also:
[http://www.linux-magazine.com/Online/News/Kernel-Plans-for-Ubuntu-10.04](http://www.linux-magazine.com/Online/News/Kernel-Plans-for-Ubuntu-10.04)


There is also discussion on actually backporting newer release kernels to the LTS versions:  (Sounds like a bad idea IMO, can be done but will be messy pulling dependencies needed for newer kernels back to an LTS) 

[http://www.linux-magazine.com/Online/News/Kernel-Plans-for-Ubuntu-10.04](http://www.linux-magazine.com/Online/News/Kernel-Plans-for-Ubuntu-10.04)
[https://wiki.ubuntu.com/KernelTeam/Specs/KernelMaverickNewKernelOnLTS](https://wiki.ubuntu.com/KernelTeam/Specs/KernelMaverickNewKernelOnLTS)
[https://blueprints.launchpad.net/ubuntu/+spec/kernel-maverick-new-kernel-on-lts](https://blueprints.launchpad.net/ubuntu/+spec/kernel-maverick-new-kernel-on-lts)

---

### Post by cottfcfan on 2010-09-28
The problem is of course, is that for people like myself and others, kernel 2.6.32... has been extremely buggy, with frequent lock ups and freezes.
Kernel 2.6.35.. appears to have resolved these problems for many.

---

