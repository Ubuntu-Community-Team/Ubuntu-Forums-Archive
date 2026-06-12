---
title: "Extra RAM not recognized"
date: 2010-06-02
forum: General Help
---

### Post by gerases on 2010-06-02
I just installed 4 gigs of RAM and though my BIOS sees it all, Ubuntu doesn't. Here's my uname -a

Linux office 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

Ideas?

---

### Post by oldos2er on 2010-06-02
You may need to install the PAE kernel, or switch to 64-bit Ubuntu.

---

### Post by xfearxnxloathing on 2010-06-02
> **gerases said:**
> I just installed 4 gigs of RAM and though my BIOS sees it all, Ubuntu doesn't. Here's my uname -a

Linux office 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

Ideas?

thats because the OS itself takes what it needs for itself and wont show what is has deemed it needs to run with the rest available.

i've got 4 gigs and mine shows 3.7.  on a previous install i had 4 gigs but showed 2.somethig gig, really close to 3gig.

---

### Post by sandyd on 2010-06-02
```

sudo apt-get install linux-image-generic-pae

```

---

### Post by gerases on 2010-06-02
Thank you all! Will try to check out the PEA kernel tomorrow...

---

### Post by xfearxnxloathing on 2010-06-02
> **oldos2er said:**
> You may need to install the PAE kernel, or switch to 64-bit Ubuntu.

> **carlee said:**
> ```

sudo apt-get install linux-image-generic-pae

```


heh. maybe i had a problem before.  from what i've told you, does my ram sound alright?

---

### Post by gerases on 2010-06-03
I downloaded the pae kernel, but then it occurred to me:

why doesn't my Kernel recognize at least up to 4GB if this is well within 32 bits?

Isn't my generic kernel pae ready?

Thanks,
 Sergei

---

### Post by uOpt on 2010-06-03
> **gerases said:**
> I downloaded the pae kernel, but then it occurred to me:

why doesn't my Kernel recognize at least up to 4GB if this is well within 32 bits?


Because the area below 4 GB is taken by PCI device space and disabled by the BIOS.

And to actually get 4 GB if you have 4 GB of RAM you don't only need a 64 bit or PAE kernel. You also need working remapping in the BIOS to get the RAM in that area to appear in the 4-5 GB area. Not all BIOSes can do that and Intel even had the audacity to market mainboard chipsets for socket 775 that physically don't have that capacity.

---

