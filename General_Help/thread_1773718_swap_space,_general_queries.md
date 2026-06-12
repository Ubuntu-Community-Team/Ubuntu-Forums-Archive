---
title: "swap space, general queries"
date: 2011-06-02
forum: General Help
---

### Post by iclestu on 2011-06-02
hey guys, I wondered what the deal is with swap space if any knowledgeable peeps care to indulge me....

My understanding so far:

any operating system loads applications into memory as and when we launch them. Applications need memory space to run and the more applications we run and, in particular, the more resource-heavy apps we run the more memory is needed. If we get to the stage where we load too many apps for our physical ram the OS offloads some by writing it to disk - the portion of disk space used for this task is swap space. That right so far or do I have misconceptions?

Ok - now the questions....

1. Linux uses a swap partition whereas windows uses a 'pagefile'(?) for this purpose, yeah? What are the advantages of the partition? To my (horrendously ill trained) eye it just seems to be much less flexible... Windows can presumably increase/decrease the file's size as needed but we need to specify the amount of swap space we are going to use at installation... is this a small disadvantage of linux or have i missed the point or am I unaware of other benefits to the partitioning system that outweigh any inflexibility?

2. What happens if my swap space and memory get full? Taking the above (no doubt too simplistic) view to the extreme.... I crash linux if I use enough resources to overload my physical ram and my swap partition whereas if I boot into windows I have to fill up all the free space on my hdd before it fails?

3. In the hypothetical situation where a user knows they will never run out of disk space should they just set the swap partition obscenely high on the basis that memory is more valuable to them than disk space or is there a speed/performance disadvantage to setting swap space too high?

---

### Post by MagneticFlux on 2011-06-02
Only a single Windows install can use a pagefile but any linux can use the swap partition, including live CD's (They run faster on my machine after I made a swap partition) On windows, you limit the use of disk by pagefile to a percentage, but I'm not sure if that can be disabled, I need to check when I boot into Windows.

---

### Post by oldfred on 2011-06-02
Does not windows have both a page file and a hiberfile?

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

Ubuntu boots fast enough, that I see no advantage to hibernation. I prefer sleep and shutdown to hibernate.

---

### Post by oldos2er on 2011-06-02
Linux can use a swap file rather than a partition if you need it to: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Determining a good swap size depends on how much physical RAM you have, whether you're using a laptop or desktop machine (with a laptop you would want to use hibernation), and how many programs you intend to run concurrently. Most of this is covered in the faq.

---

### Post by iclestu on 2011-06-02
> **oldfred said:**
> Does not windows have both a page file and a hiberfile?

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

Ubuntu boots fast enough, that I see no advantage to hibernation. I prefer sleep and shutdown to hibernate.

nice link.... never knew about 'swappiness'! :)

---

### Post by MagneticFlux on 2011-06-02
> **oldfred said:**
> Does not windows have both a page file and a hiberfile?


Yes, hiberfil.sys is used for hibernation and the pagefile is used as an extension to the memory. Linux uses a swap partition for both of these (as far as I know)

---

### Post by 5149.5 on 2011-06-02
If you leave the windows pagefile set to to dynamic sizing, it will fragment. The performance of the pagefile gets progressively worse as the fragmentation increases.

---

### Post by Sergio_ on 2011-07-21
> **oldfred said:**
> Does not windows have both a page file and a hiberfile?

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)



I read the whole Faq, and I did exactly what it said there, but when I tried to set swappiness I get this error

[http://imageshack.us/f/225/pantallazoerrorsetswapp.png/]("http://imageshack.us/f/225/pantallazoerrorsetswapp.png/")

whats Can i DO?

---

### Post by oldos2er on 2011-07-21
Try ```
gksu gedit /etc/sysctl.conf
```

---

