---
title: "System freezes when swappiness is 10"
date: 2009-07-17
forum: General Help
---

### Post by tayran on 2009-07-17
Hi,

I am using Kubuntu Jaunty 9.04 on my laptop having 2GB s of RAM. Default swappines is 60 for ubuntu but that time it is using to much swap while all my running applications could easily fit in the RAM themselves. So i decided to reduce this value to 10. On my previous installation i had no swap and it was more responsive but you see there may be a problem when i run out of RAM. It was not frequent but when it happens then the system freezes naturaly :)

So i decided to make the linux use swap only when it runs out of RAM totally. I know that system should use some RAM for caching and buffering purposes. But as far as i have observed it uses almost half of the RAM for this no matter what and i think it is a waste of RAM while it can use it for running processes.

Main problem is i think the kernel protects caching over processes. For example when it uses around 800MBs for caching when i open a new program it first slows then freezes the system because free memory drops below 40MBs and it cannot find enough contigous blocks in the memory space to allocate while there is 800MBs used by caching and buffers!

Is there something wrong with this thinking?

Thanks

---

### Post by nikhilk on 2009-07-17
> **tayran said:**
> I am using Kubuntu Jaunty 9.04 on my laptop having 2GB s of RAM. Default swappines is 60 for ubuntu but that time it is using to much swap while all my running applications could easily fit in the RAM themselves. So i decided to reduce this value to 10. On my previous installation i had no swap and it was more responsive but you see there may be a problem when i run out of RAM. It was not frequent but when it happens then the system freezes naturaly :)

Although all your applications could fit entirely into RAM it will not necessarily increase performance automatically. In case of a kernel with demand paging, it is not necessary for an entire application to be in RAM, only the "parts" of an application that are currently being used need be in RAM, rest can be in swap without any severe performance penalty.

> **tayran said:**
> So i decided to make the linux use swap only when it runs out of RAM totally. I know that system should use some RAM for caching and buffering purposes. But as far as i have observed it uses almost half of the RAM for this no matter what and i think it is a waste of RAM while it can use it for running processes.

Again you do not necessarily require all applications to be in RAM all the time. The problem in this approach is that RAM can get filled with lots of inactive applications and new applications will take more time to launch as they have to use swap. Normally, inactive or less frequently used applications are automatically relegated to swap. This behavior should usually, not cause problems.

> **tayran said:**
> Main problem is i think the kernel protects caching over processes. For example when it uses around 800MBs for caching when i open a new program it first slows then freezes the system because free memory drops below 40MBs and it cannot find enough contigous blocks in the memory space to allocate while there is 800MBs used by caching and buffers!

Is there something wrong with this thinking?

60 is a bit conservative value for most of the new systems with multi-gigabytes of RAM. Start with a higher value than 10 and experiment to find a value that suits your usage patterns.

---

### Post by tayran on 2009-07-17
Thanks for the explanation. I agree with you about the need for paging for unused pages but i don't understand why the system uses half of the RAM for caching while it can use it for applications instead.

For example now the result of free command is like this:

             total       used       free     shared    buffers     cached
Mem:       2052856    2000388      52468          0      30120    1076468
-/+ buffers/cache:     893800    1159056
Swap:      3148700        460    3148240


Now if i open new programs it doesn't reallocate some of the cache for applications. Free memory drops below 50MBs and system's responsiveness is greatly affected by this. Sometimes it totally freezes the system but i know that the total memory usage isnt more than 1.3GBs for example and there should be at least 500MBs free RAM to be used. But instead it prefers to use 700MBs for caching and doesn't give a little amount of this to other applications and system freezes and i need to use REISUB shortcut each time.

While using swappiness as 60 it doesn't freeze the whole system but in a similar manner it allocates 1GBs for caching and uses 2GB of swap space and responsiveness drops. I know it is normal when i keep an application minimized for a long time then the system may think that it is not used and swap it into disk but what i wonder is why does it do this while there is enough space already and it prefers using this space for caching only.

What i would like to see is if the free memory drops below a certain level then the system should reallocate some part of its cache for applications. Actually it works like i said but it isn't generous enough :) and sometimes it doesn't do at all. Of course caching is also necessary for disk operations or network operations but i think it shouldn't be a top priority. There may be a limit for mininum cache size like 1/10th of the whole RAM but now it behaves like there is a limit like half of the RAM.

---

### Post by tayran on 2009-07-20
Is there anyone who can give me a satisfactory answer about my problem? I think i am wrong somewhere but i couldn't receive an answer. It shouldn't be that complicated i guess. Thanks

---

### Post by tayran on 2009-07-21
I found the solution for my responsiveness problem. I put these two lines in my /etc/sysctl.conf file:

# force kernel to use less swap
vm.swappiness=10
# force kernel to use less cache
vm.vfs_cache_pressure=50

Now my laptop is more like a desktop system then a server :)

Default for vm.swappiness is 60 and for vm.vfs_cache_pressure is 100 for ubuntu. I may revert them back to defaults if i want it to run as a server.

---

