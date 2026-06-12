---
title: "CPU-Z for  Ubuntu"
date: 2012-08-06
forum: General Help
---

### Post by Penfold1971 on 2012-08-06
Has anyone used an up to date version of CPU-Z for Ubuntu on 12.04?

I have found references to it and CPU-G, but the info might be out of date as there is no mention of 12.04.

---

### Post by Frogs Hair on 2012-08-06
What I found suggests that CPU-G was used on 11.04 or 11.10 based on the date posted, but find no direct reference to 12.04. System profler & Benchmark is in the software center if you want system info. I know CPU-Z can be used as an overclock tool in Windows but have no idea if CPU-G was or is used for the same purpose.  

[http://howtoubuntunews.blogspot.com/2011/05/install-cpu-g-yet-another-cpu-z-on.html](http://howtoubuntunews.blogspot.com/2011/05/install-cpu-g-yet-another-cpu-z-on.html)

---

### Post by SlugSlug on 2012-08-06
Do you know you can get all that info via

```
sudo lshw |more
```

---

### Post by Penfold1971 on 2012-08-06
> **SlugSlug said:**
> Do you know you can get all that info via

```
sudo lshw |more
```

I had found the command
```
lshw
```
and ran it only to get the warning message that it should be run as super-user. It seemed to work anyway(?).

I like the ```
|more
``` bit at the end.  :)  Thanks.

I had the idea that the CPU-Z (or CPU-G) would tell me the actual speed of the processor, rather than the speed it's advertised as running at. Maybe I've got a ****-eyed understanding of what I'd read.

---

### Post by Penfold1971 on 2012-08-06
> **Frogs Hair said:**
> What I found suggests that CPU-G was used on 11.04 or 11.10 based on the date posted, but find no direct reference to 12.04. System profler & Benchmark is in the software center if you want system info. I know CPU-Z can be used as an overclock tool in Windows but have no idea if CPU-G was or is used for the same purpose.  

[http://howtoubuntunews.blogspot.com/2011/05/install-cpu-g-yet-another-cpu-z-on.html](http://howtoubuntunews.blogspot.com/2011/05/install-cpu-g-yet-another-cpu-z-on.html)

Thanks. I downloaded System profiler & Benchmark.

One of the things that occurs to me as a new user of Ubuntu (I've only been one since the 25th of June, so have no knowledge of Ubuntu prior to 12.04) is that a lot of what's out there to read up on isn't necessarily appropriate for the current version. Hence my original query.

If I decide I want to uninstall 'S p & B', what commend will I use?

---

### Post by Frogs Hair on 2012-08-06
You can remove it from the software center or with the following. ```
sudo apt-get remove hardifo 
```

---

### Post by tora201 on 2012-08-20
Terminal: 

```
wget https://launchpad.net/~phantomas/+archive/ppa/+files/cpu-g_0.9.0_amd64.deb 
sudo dpkg -i cpu-g*.deb 
```

64-bit version works fine on my Asus ux31e

P.S Sorry can't remember where I got it from off the top of my head. Hope it helps!

---

### Post by topet2k12001 on 2012-09-17
> **Penfold1971 said:**
> Has anyone used an up to date version of CPU-Z for Ubuntu on 12.04?

I have found references to it and CPU-G, but the info might be out of date as there is no mention of 12.04.

Hi Friend,

Have you given i-Nex a shot (Linux alternative as well for CPU-Z)? I used to do some overclocking (not into benchmarking, just 4GHz to 4.5GHz max stable/regular use) and indeed, it's quite an adjustment to do it in Linux for someone new.

However, there are indeed built-in tools in Linux/Ubuntu that offer the same functionality, but without the bells-and-whistles of a graphic application (mostly command line, but does the job just the same). You may want to check this link out: [http://www.upubuntu.com/2012/06/list-of-best-system-monitoring.html](http://www.upubuntu.com/2012/06/list-of-best-system-monitoring.html). i-Nex is also listed there. :)

---

### Post by ericpeac0ck79 on 2012-12-13
> **tora201 said:**
> terminal: 

```
wget https://launchpad.net/~phantomas/+archive/ppa/+files/cpu-g_0.9.0_amd64.deb 
sudo dpkg -i cpu-g*.deb 
```

64-bit version works fine on my asus ux31e

p.s sorry can't remember where i got it from off the top of my head. Hope it helps!

thanks!!!!!!!!

---

