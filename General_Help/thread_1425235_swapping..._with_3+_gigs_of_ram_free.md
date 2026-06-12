---
title: "swapping... with 3+ gigs of ram free?"
date: 2010-03-08
forum: General Help
---

### Post by FreezWay on 2010-03-08
Occasionally, my computer will start swapping with 3 or more gigs of ram free. Why? how do I fix this.

---

### Post by patchwork on 2010-03-08
To reduce the occurence of swapping, you can add the line:

```
vm.swappiness = 10
``` to the bottom of your /etc/sysctl.conf

This is a value between 0 and 100, where 100 indicates a near constant swap usage and 0 indicates (zero? extremely limited?) swap usage.

---

### Post by jmszr on 2010-03-08
FreezWay,

About 2/3 of the way down SwapFaq: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) , there is a section "What is swappiness and how do I change it?" that may be pertinent to your issue. It looks like changing your swappiness to 10 might help.

Worth a try.

---

### Post by SaintDanBert on 2010-03-08
Programs execute from physical ram. Years ago, someone invented "virtual memory" that lets progams **load** even though they are larger than the available physical ram. In **multi-process** systems, more than one program loads at the same time putting even more demand on available physical ram.

Typically there is a partition dedicated to "swapping space". Alternately, there is a "swap file" instead of a partition. When the kernel needs more space, it will copy the not-recently-used contents of ram onto swap space. Later when that program needs to use code that is "swapped out", the kernel reads the needed section into ram. Of course, it might need to swapped out something else.

Usually this is not a problem. However, if there is so much going on and physical ram is in very short supply, the kernel will spend more time moving things to and from swap space and not very much time letting those thing execute. We call this "thrashing."

Now that ram is cheap, it is not unusual to have 3,4,...more gigabytes of physical ram. You may have very little need for kernel managed swapping. There are tools that let you see what is going on and manage (swappiness option) how much or often swapping happens. There may be cases when it is simply easier to move something out of the way completely, load and execute a program, and then bring the other parts back.

[highlight]A word of caution:[/highlight]  If you don't configure swap space at all, other features like suspend-to-ram (sleep) and suspend-to-disk (hibernate) might not work because they lack somewhere to write the data needed on reboot.

Cheers,
~~~ 0;-Dan

---

### Post by dcstar on 2010-03-08
> **FreezWay said:**
> Occasionally, my computer will start swapping with 3 or more gigs of ram free. Why? how do I fix this.

That is nothing that need "fixing" as it is normal behaviour and not any sort of fault, but you can change it as specified in the previous posts.

I have vm.swappiness set to 0 on my 64-bit system with 4GB RAM, and nothing goes to swap except under extreme memory load (like when I run about 5 VMs simultaneously).

---

