---
title: "Swapness question"
date: 2010-03-01
forum: General Help
---

### Post by Enigmapond on 2010-03-01
I re-configured my swapness from 60 to 20 and now I go all day long without the swap even being used and only 57-60% max on the RAM is ever used. Is this a good thing?

---

### Post by emanuel.b on 2010-03-01
Well, as long as your not getting RAM exception errors, I think your fine...

---

### Post by Enigmapond on 2010-03-01
No everything runs silky-smooth with no errors. Thank you for your response..:)

---

### Post by Serpher on 2010-03-01
As long as all of your RAM is never used, you don't even need a swap partition.  I just have 2GB of RAM and 2GB of swap and I've never even used that 2GB of RAM.

---

### Post by KegHead on 2010-03-01
Hi!

I went thru this recently.

I got a lot of great advice.

I finally found an Ubuntu doc advising a swappiness of "10".

It works great for me!

KegHead

---

### Post by Enigmapond on 2010-03-01
Thank you. I thought as much and was just making sure. Prior to changing it there was always about 20% of the swap being utilized and the RAM was far from being depleted. Thanks Again!:)

---

### Post by d3v1150m471c on 2010-03-01
yes. ram is easier to read from than swap.

---

### Post by Pjotr123 on 2010-03-02
Lowering the swappiness makes a tremendous difference for computers with low RAM. 

With a swappiness of 10, I could even make Ubuntu 9.10 run pretty well on an old P4 with only 256 MB RAM.... Prior to lowering the swappiness, that computer was excruciatingly slow and kept hammering the hard drive.

For those in search of a how-to:
[http://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Computers-with-relatively-low-RAM-m](http://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Computers-with-relatively-low-RAM-m)

---

### Post by d3v1150m471c on 2010-03-02
> **Pjotr123 said:**
> Lowering the swappiness makes a tremendous difference for computers with low RAM. 

With a swappiness of 10, I could even make Ubuntu 9.10 run pretty well on an old P4 with only 256 MB RAM.... Prior to lowering the swappiness, that computer was excruciatingly slow and kept hammering the hard drive.

For those in search of a how-to:
[http://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Computers-with-relatively-low-RAM-m](http://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Computers-with-relatively-low-RAM-m)

 Increasing the vm.swappiness integer [COLOR=Red]will add more to the swap space and less to the ram. [/COLOR]For machines with less ram you'll need to leave the swap the same or increase the integer.

```

d3v11@d3v11m4ch1n3:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2894       2776        118          0        160       1835
-/+ buffers/cache:        779       2114
Swap:         8479          0       8479
d3v11@d3v11m4ch1n3:~$ sysctl -q vm.swappiness
vm.swappiness = 10

```

---

### Post by dabl on 2010-03-02
Here's a good article on the topic:  [http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that](http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that)

I set my swappiness to 1.  With 4GB of RAM, there's no reason to swap, 99.9% of the time.

---

### Post by Enigmapond on 2010-03-02
Thank you for all your replies. I initially did it as I'm running a rather ancient 9 year old computer with about 750MB of RAM. Since I did the configuration to the swap, it's runs so much better and the swap is never even used.

---

