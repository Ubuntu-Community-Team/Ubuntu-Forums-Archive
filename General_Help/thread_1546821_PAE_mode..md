---
title: "PAE mode."
date: 2010-08-05
forum: General Help
---

### Post by Mr_VeRiTy on 2010-08-05
Hi, I have 4GB of RAM in my machine, and I am using 32Bit  Ubuntu Lucid, I was wondering if there were any disadvantages of using the PAE mode version of the kernel, as that would allow me to use the whole of my memory instead of 2.9 GB.

---

### Post by Mr_VeRiTy on 2010-08-07
*bump*

---

### Post by DeMus on 2010-08-07
> **Mr_VeRiTy said:**
> Hi, I have 4GB of RAM in my machine, and I am using 32Bit  Ubuntu Lucid, I was wondering if there were any disadvantages of using the PAE mode version of the kernel, as that would allow me to use the whole of my memory instead of 2.9 GB.

I use:

Linux Ultimate 2.6.32-24-generic-pae #39-Ubuntu SMP Wed Jul 28 07:39:26 UTC 2010 i686 GNU/Linux

And I have the full 4GB available. I see no disadvantages at all, just the advantage of having the complete 4GB of memory.

---

### Post by Mr_VeRiTy on 2010-08-07
> **DeMus said:**
> I use:

Linux Ultimate 2.6.32-24-generic-pae #39-Ubuntu SMP Wed Jul 28 07:39:26 UTC 2010 i686 GNU/Linux

And I have the full 4GB available. I see no disadvantages at all, just the advantage of having the complete 4GB of memory.
And also do I have to un-install the non-PAE version first?

---

### Post by worksofcraft on 2010-08-07
Individual applications will still be limited to a 32 bit virtual address space, so PAE helps for having multiple applications concurrent and not for one application handling lots of data in memory.

There are rumors that several hardware drivers, especially ones that use DMA can get confused by the extra memory.

I get impression that PAE causes extra over head in managing memory page tables which in some cases might actually degrade overall system performance. I also gather that PAE is now superseded with 64 bit architectures.

Well ignoring these rumors, objective benchmark tests have been done e.g. [http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

My conclusion is that PAE is not worth the bother but 64 bit is :)

---

### Post by Mr_VeRiTy on 2010-08-07
> **worksofcraft said:**
> Individual applications will still be limited to a 32 bit virtual address space, so PAE helps for having multiple applications concurrent and not for one application handling lots of data in memory.

There are rumors that several hardware drivers, especially ones that use DMA can get confused by the extra memory.

I get impression that PAE causes extra over head in managing memory page tables which in some cases might actually degrade overall system performance. I also gather that PAE is now superseded with 64 bit architectures.

Well ignoring these rumors, objective benchmark tests have been done e.g. [http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

My conclusion is that PAE is not worth the bother but 64 bit is :)
Will most applications still work with 64 bit? For instance armagetron advanced?

---

### Post by speedwell68 on 2010-08-07
> **DeMus said:**
> I use:

Linux Ultimate 2.6.32-24-generic-pae #39-Ubuntu SMP Wed Jul 28 07:39:26 UTC 2010 i686 GNU/Linux

And I have the full 4GB available. I see no disadvantages at all, just the advantage of having the complete 4GB of memory.

As do I.  When I upgraded my ram I did a full reinstall and it automatically installed the PAE kernel. Although you can manually install it.  Personally I have had problems in the past with 64 bit Ubuntu.

---

### Post by worksofcraft on 2010-08-07
There have been some teething problems with 64 bit and I don't know about armagetron.

Lately all the applications that I use have been working relaibly on my AMD quad core and several bench tests show that even with the same 4Gb of physical memory the 64 bit version nearly doubles system performance. I think it is the way forward.

---

### Post by xx58 on 2010-08-07
I have Ubuntu 9.10 and Ram memory 3.9 GB, but if I had Ubuntu 10.04 Ram Memory was only 3 GB.

---

