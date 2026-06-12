---
title: "Ram Limit?"
date: 2010-01-27
forum: General Help
---

### Post by Forbees on 2010-01-27
where does 64bit linux cap out with ram?

32 bit was at  4gig

theoretically 64bit would be

17179869184 GB

can 64bit linux harvest all this ram? (assuming you can build a pc that can hold it)

---

### Post by t4thfavor on 2010-01-27
Probably arount 128GB or so, I don't know exactly, but thats where windows x64 is currently capped.

---

### Post by llawwehttam on 2010-01-27
Hmm I heard some servers ( very custom) managed to take 256 GB RAM. I have no idea how they did it though.

---

### Post by Forbees on 2010-01-27
sounds about right to me, but it'd be nice if someone could find some evidence . . . i tried googling and found nothing.

my professor was interested since we talked about ram caps and he knowing i play w/ ubuntu thought i might know the linux cap

---

### Post by egalvan on 2010-01-27
First, Linux had PAE options in the kernel for quite some time.
I use a PAE-enabled 32-bit Hardy on 8GB RAM.
Windows always was much more limited.

Now...
theoretical limit -- 16 exabytes  of RAM

AMD chips -- AMD64 architecture currently has a 52 bit limit on physical memory and only supports a 48-bit virtual address space.
This is 4 petabytes and 256 terabytes, respectively


I don´t have info in Intel chips to hand...

But the motherboard, RAM chip sizes and your wallet will provide the limit :p

At the moment, 16GB is the general upper limit for consumer-level hardware.


Also, Microsoft usually has artificial (read $$$) limits on RAM sizes, so using it as a yardstick is not a good idea ;)

---

### Post by egalvan on 2010-01-27
Oy ve....

here is some googling results !!

[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

---

### Post by Forbees on 2010-01-27
see those are all the theoretical limits .. 

i'm talking, if i built a comptuer with inifinate ram, how much would linux be able to detect? can it actually read all 4 petrabytes?

---

### Post by bodhi.zazen on 2010-01-27
> **egalvan said:**
> First, Linux had PAE options in the kernel for quite some time.
I use a PAE-enabled 32-bit Hardy on 8GB RAM.
Windows always was much more limited.

Now...
theoretical limit -- 16 exabytes  of RAM

AMD chips -- AMD64 architecture currently has a 52 bit limit on physical memory and only supports a 48-bit virtual address space.
This is 4 petabytes and 256 terabytes, respectively


I don´t have info in Intel chips to hand...

But the motherboard, RAM chip sizes and your wallet will provide the limit :p[/code]

More likely then not your motherboard will set the limit.

[quote]At the moment, 16GB is the general upper limit for consumer-level hardware.


Also, Microsoft usually has artificial (read $$$) limits on RAM sizes, so using it as a yardstick is not a good idea ;)

Depends on what you consider "consumer-level", 128 Gb of RAM is not *that* difficult.

64 Gb is easily done (assuming you can afford the RAM).

On a practical level, unless you are doing something that is RAM intense such as virtualization, most Desktop users will not use more then 2 GB of RAM, and most of that will be "cached".

So do not buy more RAM then you anticipate you will actually use, Linux is not Windows ;)

---

### Post by t4thfavor on 2010-01-27
[http://lkml.indiana.edu/hypermail/linux/kernel/0812.2/00292.html](http://lkml.indiana.edu/hypermail/linux/kernel/0812.2/00292.html)

---

### Post by Forbees on 2010-01-27
> **t4thfavor said:**
> [http://lkml.indiana.edu/hypermail/linux/kernel/0812.2/00292.html](http://lkml.indiana.edu/hypermail/linux/kernel/0812.2/00292.html)

we have a winner!

:)

---

### Post by egalvan on 2010-01-29
> **bodhi.zazen said:**
> Depends on what you consider **"consumer-level",** 128 Gb of RAM is not *that* difficult.

64 Gb is easily done (assuming you can afford the RAM).

Dick & Jane User, who buy an HP or Acer at Best Buy, or from Dell :)

> So do not buy more RAM then you anticipate you will actually use, Linux is not Windows ;)

Absolutely, *nix uses RAM much more efficiently.

But a Shell-Shocker at Newegg is efficient!!!
4GB of DDR2 RAM (two 2GB sticks) for $34, shipped!
How could I have resisted that?
I bought six sets (12 sticks) and maxed out four of my computers.
The "older" 512M & 1GB sticks migrated out to other machines.
So I ended up "maxing" out 7 machines.
(the lowly 256M sticks were donated; they upgraded machines that only had 128M or 256M RAM)

---

### Post by egalvan on 2010-01-29
> **t4thfavor said:**
> [http://lkml.indiana.edu/hypermail/linux/kernel/0812.2/00292.html](http://lkml.indiana.edu/hypermail/linux/kernel/0812.2/00292.html)

+10

bookmarked and saved for future "use" :)

Thanks!

---

### Post by bodhi.zazen on 2010-01-29
> **egalvan said:**
> Dick & Jane User, who buy an HP or Acer at Best Buy, or from Dell :)

Oh, that consumer, :lolflag:

---

### Post by t4thfavor on 2010-01-30
> **egalvan said:**
> +10

bookmarked and saved for future "use" :)

Thanks!

It's because I have awesome Google Skillzzzz. 

Sorry I couldn't resist.

So that was the correct answer? Is this marked Solved?

Just send me the check.

---

