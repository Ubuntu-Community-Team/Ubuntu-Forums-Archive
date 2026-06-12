---
title: "Ubuntu on ultra small config: What is the best distribution?"
date: 2010-03-05
forum: General Help
---

### Post by zelegolas on 2010-03-05
Hi 

I will bought this configuration:
[QBOX-1010]("http://www.quanmax.com/product/product_detail.aspx?pd_root_type=6&pd_type=10&pd_id=99")

On this configuration I will just install:
- Apache 
- Postfix
- Dovecot (with Sieve plugins)
- RoundCube
- Some other web stuff.

I don't need graphic interface. 

I'm looking for the best Linux distribution to run on this configuration. The distribution must be optimized for this hardware (Intel Atom N270)

With Ubuntu do we have a version could be fit with my needs?

---

### Post by dcstar on 2010-03-05
> **zelegolas said:**
> Hi 

I will bought this configuration:
[QBOX-1010]("http://www.quanmax.com/product/product_detail.aspx?pd_root_type=6&pd_type=10&pd_id=99")

On this configuration I will just install:
- Apache 
- Postfix
- Dovecot (with Sieve plugins)
- RoundCube
- Some other web stuff.

I don't need graphic interface. 

I'm looking for the best Linux distribution to run on this configuration. The distribution must be optimized for this hardware (Intel Atom N270)

With Ubuntu do we have a version could be fit with my needs?

Any of the Server versions.

---

### Post by HPD2 on 2010-03-05
With out compiling the kernel and operating system your not gonna have an operating system optimized for a specific hardware set. However ubuntu server or cli installs would be the best thing to fit your needs from the sound of it. Ubuntu will automatically select the correct or best drivers for your system and install them. Note that proprietary (ati and nvidia) drivers you will have to install on your own, although ubuntu will install a free and open source driver to begin with.

---

### Post by snowpine on 2010-03-06
Intel 945 does not require proprietary graphics drivers. Atom 270 is well supported too. That machine basically looks like a "netbook in a box." Ubuntu Server should run fine.

---

