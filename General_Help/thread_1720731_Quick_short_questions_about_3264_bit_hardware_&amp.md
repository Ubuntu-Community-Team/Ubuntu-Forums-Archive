---
title: "Quick short questions about 32/64 bit hardware &amp; OS"
date: 2011-04-03
forum: General Help
---

### Post by astrobob.tk on 2011-04-03
Hey guys,

until now I haven't yet installed any 64-bit OS, or so I think. The command ```
uname -a
``` gives me a > i686 GNU/Linux which I believe means 32 bit OS right ?

Moreover, the command ```
cat /proc/cpuinfo
``` gives me > Intel(R) Core(TM)2 Duo CPU     P8700  @ 2.53GHz for the CPU model name which after checking seems 64-bit.

My question is simple & maybe naive; it is safe & recommended to install a 64-bit Ubuntu right ? If so which one should I choose, 64-PC (Intel x86) or bit PC (AMD64) ? I am assuming the first since I assume I've got a 64-bit intel cpu; is my assumption right ?

Another quick question: I usually use the disc that is given with a linux magazine; is it possible to choose to install 64 instead of 32-bit ?

thanks in advance

---

### Post by bodhi.zazen on 2011-04-03
> **astrobob.tk said:**
> Hey guys,

until now I haven't yet installed any 64-bit OS, or so I think. The command ```
uname -a
``` gives me a  which I believe means 32 bit OS right ?

Yes you are running 32 bit

> Moreover, the command ```
cat /proc/cpuinfo
``` gives me  for the CPU model name which after checking seems 64-bit.

My question is simple & maybe naive; it is safe & recommended to install a 64-bit Ubuntu right ? If so which one should I choose, 64-PC (Intel x86) or bit PC (AMD64) ? I am assuming the first since I assume I've got a 64-bit intel cpu; is my assumption right ?

Most people, myself included, would advise you run 64 bit Ubuntu.

> Another quick question: I usually use the disc that is given with a linux magazine; is it possible to choose to install 64 instead of 32-bit ?

thanks in advance

Depends on the install disk. If you do not have the option to install 64 bit, download the and iso from Ubuntu (the amd iso is 64 bit and is for intel and amd).

---

### Post by techunit on 2011-04-03
I would recommend that you let your ram usage decided. How much ram do you have? If you have 4GBs you might consider 64bit. If not stay with what you have.

---

### Post by astrobob.tk on 2011-04-03
i've got 4 GB's of RAM, so I think my next installation would be the amd 64 bit ?

thanks guys :D

---

### Post by techunit on 2011-04-03
Wait until 11.04 comes out though.

---

### Post by bodhi.zazen on 2011-04-03
> **techunit said:**
> I would recommend that you let your ram usage decided. How much ram do you have? If you have 4GBs you might consider 64bit. If not stay with what you have.

That is a common misunderstanding, you can use up to 64 Gb RAM with the PAE kernel.

---

### Post by lithopsian on 2011-04-03
Although you can use more than 4GB with a PAE kernel, I'd hazard a guess that you don't have a PAE kernel.  You should check how much memory is being shown with free -m or dmesg.  You may well not be getting full use out of your 4GB.

The simplest way to address all that memory with a 64 bit CPU is to use a 64 bit OS.  Generally that means downloading the 64 bit version and installing it.  Before you do this you should be aware that it can lead to trouble.  Many applications and drivers do not work well, or at all, with 64 bits.  For these you will have to install a special set of 32 bit libraries that can map to your 64 bit OS and allow 32 bit apps to run.  Some of them are still cranky about the whole thing.

You can also choose a 32 bit kernel compiled to support what is known as high memory.  By default a Linux kernel can only address 1GB of memory.  However kernels are generally configured to address up to 4GB of memory, but with limitations.  Only 3GB are visible to applications and the other 1GB is reserved for the kernel.  The 1GB reserved space can also be configured to 2GB or 3GB for unusual situations.  A typical symptom of these conditions is that free -m will report a total of 3.2GB of memory.

Lastly, a kernel can be compiled with PAE support, which allows addressing memory up to 64GB.  This relies on PAE being supported by the CPU, which yours should, and this feature is not built in to most kernels because it places an extra load on the CPU.  You will have to install a special kernel but you can do this without re-installing your entire system because it is still 32 bit.

Ideally you would run a 64 bit OS because this will give you the best performance.  If you experience problems with some applications or drivers, or you simply aren't confident about messing with the special libraries to get some things working, or you don't want a complete new install, then try a PAE kernel.

---

### Post by techunit on 2011-04-03
Simply up to the user. I would wait until the release of Ubuntu 11.04 to do anything because 64bit Ubuntu should be just about flawless by then.

---

### Post by bodhi.zazen on 2011-04-03
> **techunit said:**
> Simply up to the user. I would wait until the release of Ubuntu 11.04 to do anything because 64bit Ubuntu should be just about flawless by then.

I think it is very reasonable to wait for 11.04, but I think 64 bit is ready now, has been for several years.

I would not hold out 11.04 as being "flawless", there is no such thing as a flawless operating system.

If you want "flawless" or "stable" stay with Ubuntu LTS (10.04) or go with something like Debian, Centos, or Slackware.

---

### Post by astrobob.tk on 2011-04-03
> **lithopsian said:**
> You can also choose a 32 bit kernel compiled to support what is known as high memory.  By default a Linux kernel can only address 1GB of memory.  However kernels are generally configured to address up to 4GB of memory, but with limitations.  Only 3GB are visible to applications and the other 1GB is reserved for the kernel.  The 1GB reserved space can also be configured to 2GB or 3GB for unusual situations.  A typical symptom of these conditions is that free -m will report a total of 3.2GB of memory.

```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          3987       3690        296          0        338       1917
-/+ buffers/cache:       1434       2552
Swap:         4767          0       4767
```

it states a 3.9GB; nearly the same as what Win7 states

> **lithopsian said:**
> Ideally you would run a 64 bit OS because this will give you the best performance.  If you experience problems with some applications or drivers, or you simply aren't confident about messing with the special libraries to get some things working, or you don't want a complete new install, then try a PAE kernel.

Have no idea what a PAE kernel is !!! :S
Anyhow, I think what you just stated made me reluctant about moving to a 64 bit OS. Everything seems to work great for now & I do not want to face problems anytime soon :P I just don't have the time to deal with it hehe

> **techunit said:**
> Simply up to the user. I would wait until the  release of Ubuntu 11.04 to do anything because 64bit Ubuntu should be  just about flawless by then.
 
> **bodhi.zazen said:**
> 
If you want "flawless" or "stable" stay with Ubuntu LTS (10.04) or go with something like Debian, Centos, or Slackware.

Personally I am operating from 10.04 LTS & am in love with it :D

I was thinking of trying 11.04 just for testing (as a first time) for my  new laptop as it doesn't seem to have been tested by anyone yet; my  thoughts are that i will stay working with 10.04 & upgrade to 12.04

---

### Post by techunit on 2011-04-03
> **bodhi.zazen said:**
> I think it is very reasonable to wait for 11.04, but I think 64 bit is ready now, has been for several years.

I would not hold out 11.04 as being "flawless", there is no such thing as a flawless operating system.

If you want "flawless" or "stable" stay with Ubuntu LTS (10.04) or go with something like Debian, Centos, or Slackware.
I didn't mean to say that it would be flawless at all. I was saying that the problems that you might have experienced with 64bit in the past should all be things of the past by then. To say that 11.04 is going to be flawless is not accurate.

---

### Post by Anonymous is Incognito on 2011-04-03
> **bodhi.zazen said:**
> That is a common misunderstanding, you can use up to 64 Gb RAM with the PAE kernel.

To be honest, if you use the PAE kernel, in theory your OS is 36-bit, not 32.

If you have a 32-bits OS the maximum amount of memory will be within 4 GiB

See:
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by techunit on 2011-04-03
> **Anonymous is Incognito said:**
> To be honest, if you use the PAE kernel, in theory your OS is 36-bit, not 32.

If you have a 32-bits OS the maximum amount of memory will be within 4 GiB

See:
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
36bit you say? Never heard it like that. But essentially so. I have heard that PAE kernel doesn't always works the way that it should. However if you are installing Ubuntu 32bit with a network connection and it detects more than 3GBs of ram it automatically installs the PAE kernel.

---

### Post by bodhi.zazen on 2011-04-03
> **Anonymous is Incognito said:**
> To be honest, if you use the PAE kernel, in theory your OS is 36-bit, not 32.

If you have a 32-bits OS the maximum amount of memory will be within 4 GiB

See:
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

Well, sort of, yes and no.

Memory allocation is 36 bit and obviously a bit of a hack.

The underlying kernel / instruction set outside of memory allocation is 32 bit.

I have used the PAE kernel and it is no more or less problematic then a standard 32 or 64 bit kernel (is is not as if the 32 or 64 bit kernel is perfect either, but then it would degenerate into a conversation about what kernel (ie what version) and what application, etc).

With that said, it is probably best to use a kernel that is optimized for your architecture, ie a 64 bit kernel on a 64 bit CPU.

The 32 bit kernel and / or pae kernel would be best used if there were some specific problem with a 6 4bit kernel.

I have personally been running 64 bit kernels without any major (or minor) issues (with the kernel) for several years now, last time I used a PAE kernel was in fact when there was a problem with the 64 bit stuff.

---

### Post by lithopsian on 2011-04-03
> **techunit said:**
> I didn't mean to say that it would be flawless at all. I was saying that the problems that you might have experienced with 64bit in the past should all be things of the past by then. To say that 11.04 is going to be flawless is not accurate.
I don't think Natty will solve the main problems of 64 bits at all.  There will still be applications that aren't available in 64 bit and there will still be tricky messing about getting them to work with 64 bit.  The OS itself works great and has done for years.

Looks to me like you are in the classic "if it ain't broke ..." situation.  You seem to have 4GB available and you are in a stable situation.  Until you need new hardware support, an app that isn't available in Lucid, or something breaks, I'd sit tight and keep smiling.

Your posted uname -a information was a bit short.  There should be more there that might tell us exactly which kernel you're using.    You can also look in /boot/config* at the actual kernel configuration to see if PAE is enabled.  grep for CONFIG_X86_PAE.  You can also look at the HIGHMEM parameters on the few lines before that.

---

### Post by astrobob.tk on 2011-04-03
> **lithopsian said:**
> 
Your posted uname -a information was a bit short.  There should be more there that might tell us exactly which kernel you're using.    You can also look in /boot/config* at the actual kernel configuration to see if PAE is enabled.  grep for CONFIG_X86_PAE.  You can also look at the HIGHMEM parameters on the few lines before that.

here is it
> 2.6.32-30-generic-pae #59-Ubuntu SMP

---

### Post by bodhi.zazen on 2011-04-03
> **astrobob.tk said:**
> here is it

That is the pae kenel FTW !!!

---

### Post by lithopsian on 2011-04-03
You're in!  PAE up and running.  Don't move, don't breathe on anything.  You have that semi-mythical perfect Ubuntu installation :)

---

### Post by astrobob.tk on 2011-04-03
:D but could you please clarify things a bit ?

I tried reading a bit about PAE & the 3G barrier limit; but could you clarify my particular case ?

where am I now ?

---

### Post by bodhi.zazen on 2011-04-03
> **astrobob.tk said:**
> :D but could you please clarify things a bit ?

I tried reading a bit about PAE & the 3G barrier limit; but could you clarify my particular case ?

where am I now ?

You are running a 32 bit kernel, pae enabled.

So you can make use of up to 64 Gb RAM, but no single process can use more then 3 Gb.

Now since it is silly to think any single process is going to use anywhere close to 3 Gb with anything resembling normal usage I think you are good to go.

In other words, despite what some people might say, you do not really have a problem and do not need to fix something that is not broken.

If you has some application or use where you needed a single process to use more then 3 Gb then you would need to install a 64 bit OS.

---

### Post by beringse on 2011-04-03
Informative thread, thanks! After reading about the pae I'm not going to touch my system again :KS

---

### Post by lithopsian on 2011-04-03
> Now since it is silly to think any single process is going to use anywhere close to 3 Gb
I think the limit is actually 4GB per process because the OS doesn't  have to steal space for itself under PAE.  Might be wrong about that though.

Firefox might try to use more than 4GB if you went mad.  Obviously not in your case since you only have 4GB!  I don't know how Firefox reacts in a PAE environment but in general it is quite prepared to use a major proportion of the total available memory which can lead to very high memory use when you open a lot of (graphics intensive) tabs on a system with a lot of memory.

---

### Post by astrobob.tk on 2011-04-03
> **bodhi.zazen said:**
> You are running a 32 bit kernel, pae enabled.

So you can make use of up to 64 Gb RAM, but no single process can use more then 3 Gb.

Now since it is silly to think any single process is going to use anywhere close to 3 Gb with anything resembling normal usage I think you are good to go.

In other words, despite what some people might say, you do not really have a problem and do not need to fix something that is not broken.

If you has some application or use where you needed a single process to use more then 3 Gb then you would need to install a 64 bit OS.

Interesting :D

thanks for the clarification

well for now, I dont think i have any that uses more than that; maybe in the near future when I thoroughly learn Maple &/or Mathematica (which I already have installed & occasionally use) might need more than that, though i highly don't think they will.

thanks again

---

### Post by bodhi.zazen on 2011-04-03
> **lithopsian said:**
> I think the limit is actually 4GB per process because the OS doesn't  have to steal space for itself under PAE.  Might be wrong about that though.

Firefox might try to use more than 4GB if you went mad.  Obviously not in your case since you only have 4GB!  I don't know how Firefox reacts in a PAE environment but in general it is quite prepared to use a major proportion of the total available memory which can lead to very high memory use when you open a lot of (graphics intensive) tabs on a system with a lot of memory.

Firefox is not going to use anywhere near 3 Gb of RAM.

To understand how Linux uses RAM see:

[http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage](http://chrisjohnston.org/2009/why-on-linux-am-i-seeing-so-much-ram-usage)

---

### Post by Anonymous is Incognito on 2011-04-04
> **bodhi.zazen said:**
> Memory allocation is 36 bit and obviously a bit of a hack.

The underlying kernel / instruction set outside of memory allocation is 32 bit.

Ah of course. Btw, I didn't mean to offend your post in any way, so apologies if it seemed so.

---

### Post by bodhi.zazen on 2011-04-04
> **Anonymous is Incognito said:**
> Ah of course. Btw, I didn't mean to offend your post in any way, so apologies if it seemed so.

Alright, thanks. I could not tell from your post if you were serious or joking, lol.

---

