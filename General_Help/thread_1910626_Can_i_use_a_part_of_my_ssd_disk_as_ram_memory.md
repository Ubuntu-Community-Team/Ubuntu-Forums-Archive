---
title: "Can i use a part of my ssd disk as ram memory?"
date: 2012-01-17
forum: General Help
---

### Post by pennypuzza on 2012-01-17
Hi All,

I've got a (maybe the unique, nowadays out of production) smartbook: the Toshiba ac100 with ubuntu 10.10.

It's a great solution to write and surf the web in movement, but the only problem is the amount of ram memory: only 512 mb. So, here the hard question, is there any way to use a little part (1 or 2 gigs) of my ssd disk as ram memory?

Thanks a lot!

---

### Post by snowpine on 2012-01-17
What you are describing is called "swap." If you chose "guided partitioning" when you installed Ubuntu, you should automatically have a swap partition by default (you can double-check this with your system monitor).

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by gsgleason on 2012-01-17
You can use some swap space, which actually should already be there.

Please show the output of 'free'

---

### Post by chipbuster on 2012-01-17
You would need to designate part of the disk to be "swap" or hard drive space that can act like RAM. Swap and RAM are treated slightly differently, however (RAM gets preference over swap most of the time) so I'm not entirely sure how to make the drive space act exactly like RAM. With an SSD, it might not even make a difference.

[http://tldp.org/LDP/sag/html/swap-space.html](http://tldp.org/LDP/sag/html/swap-space.html)

---

### Post by Grenage on 2012-01-17
Well to look at it an easier way, increased swappiness would store more on the drive.  You can specify partitions easily enough, including their capacity.

---

### Post by Mark Phelps on 2012-01-17
> **pennypuzza said:**
> ... is there any way to use a little part (1 or 2 gigs) of my ssd disk as ram memory?

If your question is about allocating system memory to the SSD, sorry, the answer is NO.  

You can use it for Swap, as already mentioned, but stuff is moved in and out of Swap using system memory, so you may not see any realtime improvement.

---

### Post by mcduck on 2012-01-17
> **chipbuster said:**
> You would need to designate part of the disk to be "swap" or hard drive space that can act like RAM. Swap and RAM are treated slightly differently, however (RAM gets preference over swap most of the time) so I'm not entirely sure how to make the drive space act exactly like RAM. With an SSD, it might not even make a difference.

[http://tldp.org/LDP/sag/html/swap-space.html](http://tldp.org/LDP/sag/html/swap-space.html)

You can't make hard drive space act *exactly* like RAM, as it's far too slow for that Even if you have SSD drive, or even some insane RAID stack of SSD drives, it's still too slow compared to RAM and the computer needs to move the data into RAM for the CPU to be able to use it effectively.

...and for the same reason using swap will never increase your performance, it does exactly the opposite. It however allows your system to operate even when it runs out of the actual RAM, and in that situation a fast drive or SSD would of course be better than a slow drive. It still won't perform anywhere as good as if you just had enough RAM, but at least the performance hit caused by swapping would be a bit smaller.

---

### Post by dcstar on 2012-01-18
Probably the best way to prematurely kill a SSD is to use it for Swap on a system with insufficient RAM.

Doing this sort of thing is so close to insane that people should probably have their computers confiscated.

---

