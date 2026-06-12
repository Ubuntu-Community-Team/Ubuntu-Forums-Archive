---
title: "ubuntu 32/64 bit help"
date: 2010-03-17
forum: General Help
---

### Post by linden940 on 2010-03-17
ok I am build this computer and not sure if I should put the 32bit on..but idk if i COULD run it with 64bit...when i was looking around i found this on ubuntu [http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/) and I saw this "PC (Intel x86) desktop CD" 

anyway what I am asking is what ver do you all think i should use to get the best out of this custom build i'm doing...here is the list of parts that are going into it.

MSI G31TM-P21 LGA775 mATX Motherboard
   Info,
Intel G31 Chipset, Supports Intel Core 2 Quad CPUs, Dual DDR2 800, PCI Express x 16, SATA 3 Gb/s, with 10/100 Fast Ethernet, 7.1 Ch Audio.

Intel Celeron E3300 Dual-Core CPU
	Speed, 1M Cache, 2.50 GHz, 800 MHz FSB
	Voltage Range, 0.85V – 1.362V

Mushkin 4GB
  info,
240-Pin DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory 996580, 4-4-4-12, Unbuffered

Palit GeForce GT220 HD video
Equipped with GDDR3 memory, Palit GT220 Sonic Overclocking edition provides the better performance. Graphics processing has become an essential ingredient to the modern PC. Nowadays, we simply demand more from our PCs to deliver gorgeous graphics, fantastic video, crisp responsive photo editing 

there is other hardware but i dont think you all need to know that..this build tho...is full SATA (did not see a good reason to stay with IDE so i spent the money to get sata)

if any more info is needed plez let me know.

---

### Post by oldos2er on 2010-03-17
64-bit, of course.

---

### Post by linden940 on 2010-03-17
ok thats what i was thinking but i was not sure if the 4gb worth of ram would be to low and would be a ram hog

I never ran a 64 bit yet so idk if it will burn up more ram than the 32

---

### Post by oldos2er on 2010-03-17
1 GB RAM would be too low, possibly. 64-bit will use more RAM than 32-bit, given the same tasks.

---

### Post by linden940 on 2010-03-17
ok thanks for the info

---

### Post by audiomick on 2010-03-17
for your info, from my 64 bit machine ( which also has an  MSI mother board) with Firefox, Evolution and one instance of Nautilus running

```
mick@ubuntu-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3962       1082       2880          0         79        462
-/+ buffers/cache:        540       3421
Swap:         6110          0       6110

```the command "free -m" reports how much RAM and SWAP is in use. The numbers are in MB. You can see that I have 4GB of RAM (mem: Total) of which about 1GB is in use and about 400MB are cached.
I practically never get into the swap, no matter what I am doing (but I don't do things like editing large video files that really require a lot of RAM)

---

### Post by linden940 on 2010-03-17
ok great..

one thing i would like to know..on my laptop *one i am using now* its runing ubuntu 32bit but the ram is abit low...is there a ez way of me setting up virtual ram for this to boots the ram like you can on windows xp?

---

### Post by audiomick on 2010-03-17
> **linden940 said:**
> ok great..

one thing i would like to know..on my laptop *one i am using now* its runing ubuntu 32bit but the ram is abit low...is there a ez way of me setting up virtual ram for this to boots the ram like you can on windows xp?
I don't think so. I have never read about anything like that. Effectively, that is what the swap space is: when the RAM gets full, the system starts juggling between RAM and swap. I don't see how any kind of "virtual RAM" would be any different or any faster than that.

---

### Post by linden940 on 2010-03-17
> **audiomick said:**
> I don't think so. I have never read about anything like that. Effectively, that is what the swap space is: when the RAM gets full, the system starts juggling between RAM and swap. I don't see how any kind of "virtual RAM" would be any different or any faster than that.

virtual ram = swap space...its the same thing its just has more than one name

on my laptop i have a big hard drive and i never will fill it up...but i can ezly fill up my ram..so i would like to take some of that harddrive space and help the ram out alittle

---

### Post by whiskeylover on 2010-03-17
> **linden940 said:**
> virtual ram = swap space...its the same thing its just has more than one name

on my laptop i have a big hard drive and i never will fill it up...but i can ezly fill up my ram..so i would like to take some of that harddrive space and help the ram out alittle

Ideally you want as less swap usage as possible.

---

### Post by linden940 on 2010-03-17
> **whiskeylover said:**
> Ideally you want as less swap usage as possible.

that i know...well just look at this

```

             total       used       free     shared    buffers     cached
Mem:          2960       2015        944          0        130       1377
-/+ buffers/cache:        507       2453
Swap:         8714          0       8714


```

my ram is not all that big so I dig into my swap when i am trying to do some things...so if i can make it bigger..that would be great...and again this is a laptop..so if i dont have to open it to put ram chips in...i rather not lol

*dont know how to put ram chips in a laptop....desk top yea..i have built a few so desktop i'm cool will...laptops..alot of small parts lol*

---

### Post by whiskeylover on 2010-03-17
> **linden940 said:**
> that i know...well just look at this

```

             total       used       free     shared    buffers     cached
Mem:          2960       2015        944          0        130       1377
-/+ buffers/cache:        507       2453
Swap:         8714          0       8714


```my ram is not all that big so I dig into my swap when i am trying to do some things...so if i can make it bigger..that would be great...and again this is a laptop..so if i dont have to open it to put ram chips in...i rather not lol

*dont know how to put ram chips in a laptop....desk top yea..i have built a few so desktop i'm cool will...laptops..alot of small parts lol*

Its not that difficult. On my Dell Inspiron, there is a small lid on the back of the laptop, that when opened, allows easy access to the RAM chips.

---

### Post by linden940 on 2010-03-17
hmmm ok i'll look into that...last thing i want is 2 kill my laptop lol

---

### Post by audiomick on 2010-03-17
> **linden940 said:**
> that i know...well just look at this

```

             total       used       free     shared    buffers     cached
Mem:          2960       2015        944          0        130       1377
-/+ buffers/cache:        507       2453
Swap:         8714          0       8714


```my ram is not all that big so I dig into my swap when i am trying to do some things...so if i can make it bigger..that would be great...and again this is a laptop..so if i dont have to open it to put ram chips in...i rather not lol

*dont know how to put ram chips in a laptop....desk top yea..i have built a few so desktop i'm cool will...laptops..alot of small parts lol*

As has been mentioned, it isn't that hard to add new RAM to a laptop as a rule. However, you already have 3GB, and the machine _might_ not be able to handle more. You should research that before you do anything.

Your output also shows a lot of cached memory. I expect that the machined had been running a while when you did "free -m". The system accumulates cache with time. Mine, for instance, had 462MB cached when I posted and hour ago, and now it has 485MB or so, and I actually wasn't at the computer for most of the intervening time.
The important point is, this memory is not un-available. It is reclaimed as RAM as soon as it is needed. Read this
[http://www.linuxatemyram.com/index.html](http://www.linuxatemyram.com/index.html)

You have a very large swap space already. I think the relevant thing is not how much RAM is being used, but how much swap, and how often. The output you posted shows that the machine is using none of the swap, and I wouldn't expect it to, given the rest of the figures.

---

### Post by linden940 on 2010-03-17
oooo kk think i am understandin alittle more here...

started to use Linux some time ago...still learning

---

