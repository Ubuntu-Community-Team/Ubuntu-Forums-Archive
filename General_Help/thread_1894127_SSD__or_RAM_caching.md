---
title: "SSD  or RAM caching"
date: 2011-12-11
forum: General Help
---

### Post by SuperFreak on 2011-12-11
I have noticed that Intel and other SSD manufacturers are offering SSD caching in combination with mechanical hard drives. These appear to be Windows only applications that accelerate boot times and application usage. Is this technology going to be available with future versions of Ubuntu or is that entirely up to the SSD manufacturers?
I apologize if this topic has been covered I did do a quick search of the forum but got unrelated hits.

---

### Post by aztektum on 2012-01-01
[Bcache]("http://bcache.evilpiepirate.org/") is a kernel module working towards being a viable Linux SSD caching option.

I have not used it and cannot speak to its capability.

---

### Post by dcstar on 2012-01-02
> **aztektum said:**
> [Bcache]("http://bcache.evilpiepirate.org/") is a kernel module working towards being a viable Linux SSD caching option.


Or simply use a "Hybrid" drive and allow it to automatically cache the most used data blocks into its SSD storage. I have been using one for over a year and am impressed with it:

[http://www.seagate.com/www/en-us/products/laptops/laptop-hdd/](http://www.seagate.com/www/en-us/products/laptops/laptop-hdd/)

---

### Post by SuperFreak on 2012-01-02
I am a little hesitant to invest in a mechanical HD with prices as high as they are and I am led to believe that Seagate is not using a large enough 
NAND chip yet.

[HTML]Unfortunately while we were impressed with the net results, our initial misgivings were proven to be well found. To be blunt, while Seagate obviously have put a lot of time and effort into refining and improving the efficiency of their algorithms, they have hobbled the Momentus with an insufficient amount of high speed NAND. Eight gigabytes may be twice what the original had, but by today’s standards this just isn’t enough to accelerate a large number of your most-used programs. Remember, while Seagate’s new hybrid may start out with 8GB of NAND, a portion of it is dedicated towards speeding up system boot rather than reducing actual program load times.

The real heart of the issue is that forward thinking is great in principle but in practice it can become a double edged sword. In this case there was no reason to add lower capacity, higher priced SLC NAND on the off chance that write caching may be implemented at some nebulous time in the future. Sure, there is only room for one NAND chip on such a small PCBbut if this drive had taken advantage of quad die package MLC NAND Seagate could have easily increased this capacity to 16GB or 32GB without obliterating the XT’s intended price point. [/HTML][http://www.hardwarecanucks.com/forum/hardware-canucks-reviews/48726-seagate-momentus-xt-750gb-hybrid-hard-drive-review-11.html](http://www.hardwarecanucks.com/forum/hardware-canucks-reviews/48726-seagate-momentus-xt-750gb-hybrid-hard-drive-review-11.html)

---

### Post by dcstar on 2012-01-02
> **SuperFreak said:**
> I am a little hesitant to invest in a mechanical HD with prices as high as they are and I am led to believe that Seagate is not using a large enough 
NAND chip yet.

[HTML]Unfortunately while we were impressed with the net results, our initial misgivings were proven to be well found. To be blunt, while Seagate obviously have put a lot of time and effort into refining and improving the efficiency of their algorithms, they have hobbled the Momentus with an insufficient amount of high speed NAND. Eight gigabytes may be twice what the original had, but by today’s standards this just isn’t enough to accelerate a large number of your most-used programs. Remember, while Seagate’s new hybrid may start out with 8GB of NAND, a portion of it is dedicated towards speeding up system boot rather than reducing actual program load times.

The real heart of the issue is that forward thinking is great in principle but in practice it can become a double edged sword. In this case there was no reason to add lower capacity, higher priced SLC NAND on the off chance that write caching may be implemented at some nebulous time in the future. Sure, there is only room for one NAND chip on such a small PCBbut if this drive had taken advantage of quad die package MLC NAND Seagate could have easily increased this capacity to 16GB or 32GB without obliterating the XT’s intended price point. [/HTML][http://www.hardwarecanucks.com/forum/hardware-canucks-reviews/48726-seagate-momentus-xt-750gb-hybrid-hard-drive-review-11.html](http://www.hardwarecanucks.com/forum/hardware-canucks-reviews/48726-seagate-momentus-xt-750gb-hybrid-hard-drive-review-11.html)

If you want to listen to the quibbles of a bunch of tech-heads who want **everything** then fine. Especially since they themselves said:
```
It can offer near- SSD real world performance while maintaining a relatively high capacity and does so while offering a completely seamless user experience.
```
You basically have 3 choices:
[LIST=1]
[*]Install a large (and expensive) SSD; or
[*]Install a SSD and a rotational drive and stuff around trying to manually optimise things; or
[*]Install a reasonably priced Hybrid drive and get 95% of the benefits of a SSD with no operational or installation issues whatsoever.
[/LIST]

---

### Post by SuperFreak on 2012-01-03
True, but the article also suggests that Seagate will be producing a 3.5" Hybrid with a larger NAND chip (16-32 GB) so I will likely wait a bit and hopefully Hard Drive prices will fall in the interim. Right now SSD drives are looking quite attractive.

---

