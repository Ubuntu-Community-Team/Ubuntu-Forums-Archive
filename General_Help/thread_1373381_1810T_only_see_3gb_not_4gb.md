---
title: "1810T only see 3gb not 4gb"
date: 2010-01-05
forum: General Help
---

### Post by linuxcss on 2010-01-05
I have installed karmic on a 1810T with 4GB of memory ... looking at system monitor  ... system tab
it reports only 2.9GB installed but bios and memtest shows 4GB ....

How do i get Karmic to see all 4gb .... I installed 32bit Karmic

---

### Post by howefield on 2010-01-05
> **linuxcss said:**
> How do i get Karmic to see all 4gb .... I installed 32bit Karmic

Use the PAE enabled kernel or install the 64 bit edition.

---

### Post by linuxcss on 2010-01-05
using synaptic what do I specify to have all that is needed for the PAE installed?

or better yet ... what do I specify to have all that is needed vi using cmd line  aptitude???

thanks

---

### Post by dcstar on 2010-01-06
> **linuxcss said:**
> using synaptic what do I specify to have all that is needed for the PAE installed?


Install the Server kernel.

---

### Post by linuxcss on 2010-01-15
that worked thanks

---

### Post by dcstar on 2010-01-16
> **linuxcss said:**
> that worked thanks

There also should be generic kernels with **pae** in their name available.

---

