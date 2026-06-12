---
title: "How to Get More RAM"
date: 2012-06-19
forum: General Help
---

### Post by Bill Z on 2012-06-19
I’m running Ubuntu v10.04LTS on an Acer Asprire AOA 110 with 1.5Gb of RAM. This notebook was not made to add or swap RAM.  

I have a 16GB SD chip inserted in the SD slot that Ubuntu sees as a HD.  

Can I have Ubuntu use some of the SD as RAM or swap space for RAM?  If so, then how do I do that?

---

### Post by lukeiamyourfather on 2012-06-19
Create a swap partition on the SD card or create a swap file. Note that the swap will be several orders of magnitude slower than the memory. If you're doing a memory intensive task and performance is important you'd be better off to upgrade to a system that can accommodate more memory.

[https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F](https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F)

Further down there's a section about adding swap using a file instead of a partition which would probably be easier for you since the system is already installed.

---

### Post by idoitprone on 2012-06-19
> **Bill Z said:**
> I&#8217;m running Ubuntu v10.04LTS on an Acer Asprire AOA 110 with 1.5Gb of RAM. This notebook was not made to add or swap RAM.  

I have a 16GB SD chip inserted in the SD slot that Ubuntu sees as a HD.  

Can I have Ubuntu use some of the SD as RAM or swap space for RAM?  If so, then how do I do that?

sd chip will never replace ram because it tooo dawm slow. sd chip is slower than your harddrive so dont even think about it. Make a swap file  on your harddrive which will be better than your sd card. and besides sd cards cannot sustain write performance.

---

### Post by lukeiamyourfather on 2012-06-20
> **idoitprone said:**
> sd chip will never replace ram because it tooo dawm slow. sd chip is slower than your harddrive so dont even think about it. Make a swap file  on your harddrive which will be better than your sd card. and besides sd cards cannot sustain write performance.

Unless it was purchased with the upgrade it doesn't have a hard disk. The base model has 8 GB of flash memory with similar performance to an SD card.

---

### Post by idoitprone on 2012-06-20
> **lukeiamyourfather said:**
> Unless it was purchased with the upgrade it doesn't have a hard disk. The base model has 8 GB of flash memory with similar performance to an SD card.

exactly, you just identified why that it makes them both not a option for swap. They both have way too many flaws that come by the nature of the controllers and the limited write performance.

here is the performance hierachy

ssd> hdd> flash drives> sd cards

why sd cards is on the bottom is because they have too much latency

Are you confusing flash memory with ssd because it make a huge difference in performance.

---

### Post by Rsjc741 on 2012-06-20
I'm assuming your netbook is pretty old then if it's running on 1.5GB of RAM.

If so, you probably shouldn't be using an OS that precedes it by 6+ years.

If you want to get more out of your old machine, you should look at using an older version of Ubuntu. However, instead of using Gnome, I'd use XFCE,

As the XFCE interface was built with light-weight in mind. This should free up a lot of the memory.

---

### Post by idoitprone on 2012-06-20
> **Rsjc741 said:**
> I'm assuming your netbook is pretty old then if it's running on 1.5GB of RAM.

If so, you probably shouldn't be using an OS that precedes it by 6+ years.

If you want to get more out of your old machine, you should look at using an older version of Ubuntu. However, instead of using Gnome, I'd use XFCE,

As the XFCE interface was built with light-weight in mind. This should free up a lot of the memory.

+1

but i am not sure on xfce because being does not mean its light. If you open lots of problem shared library nature of kde4 will save you lots of ram.

Oh well

i have to say lxde or xfce because their starting ram usage is lower

---

### Post by VCoolio on 2012-06-20
Or you can download free RAM [here](http://www.downloadmoreram.com/) :lolflag:

---

