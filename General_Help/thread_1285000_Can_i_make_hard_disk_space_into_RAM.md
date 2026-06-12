---
title: "Can i make hard disk space into RAM?"
date: 2009-10-07
forum: General Help
---

### Post by Jedi_Knight on 2009-10-07
If so, how do i do this in Ubuntu?

---

### Post by snowpine on 2009-10-07
Yes; it is called a "swap partition" and the Ubuntu installer creates one during the install process.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by khelben1979 on 2009-10-07
And the technique itself is called [virtual memory]("http://en.wikipedia.org/wiki/Virtual_memory").

---

### Post by doas777 on 2009-10-07
so short answer no.
long answer, it's been done for you already, you just can't really control it.

---

### Post by snowpine on 2009-10-07
> **doas777 said:**
> so short answer no.
long answer, it's been done for you already, you just can't really control it.

????

You can make your swap partition as large or small as you want.
You can turn your swap on or off at will.
You can adjust your "swapiness" too.

I really don't understand your comment...

---

### Post by doas777 on 2009-10-07
> **snowpine said:**
> ????

You can make your swap partition as large or small as you want.
You can turn your swap on or off at will.
You can adjust your "swapiness" too.

I really don't understand your comment...

I'm saying that swap operations are run by the system with no user intervention. you will not start paging until the system says so. there is no real configuration beyond turning it on and formatting a size.  thats all. it sounds like the op wants to "***do*** something", and there really isn't anything to do.

---

### Post by snowpine on 2009-10-07
> **doas777 said:**
> I'm saying that swap operations are run by the system with no user intervention. you will not start paging until the system says so. there is no real configuration beyond turning it on and formatting a size.  thats all. it sounds like the op wants to "***do*** something", and there really isn't anything to do.

You didn't read my link in post #2... here is a direct link to the relevant section:

[https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27](https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27)

There are 100 different values for swapiness... how much more "fine grained" can the configuration be? :confused:

---

### Post by doas777 on 2009-10-07
> **snowpine said:**
> You didn't read my link in post #2... here is a direct link to the relevant section:

[https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27](https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27)

There are 100 different values for swapiness... how much more "fine grained" can the configuration be? :confused:

process by process.  setting a int that is somehow representative of the amount of time a page stays in ram is kinda silly on a system level. the trick would be to know what to swap and what to leave resident, which swapiness does not account for. hence the system makes the decision about which processes data to swap when.

---

### Post by snowpine on 2009-10-07
> **doas777 said:**
> process by process.  setting a int that is somehow representative of the amount of time a page stays in ram is kinda silly on a system level. the trick would be to know what to swap and what to leave resident, which swapiness does not account for. hence the system makes the decision about which processes data to swap when.

I understand now. Thanks! :)

---

### Post by jamesy on 2009-10-07
You can make temporary swap, have a look at

[http://www.linuxjournal.com/video/emergency-swapfile-when-your-memory-fills](http://www.linuxjournal.com/video/emergency-swapfile-when-your-memory-fills)

I don't know if it's the best/most efficient way but works for me...

---

### Post by abhilashm86 on 2009-10-07
> **Jedi_Knight said:**
> If so, how do i do this in Ubuntu?

see the output of this.....
```
sudo blkid
```
it shows how much swap has been assigned, also some tell swap should be almost same as your ram, so paging becomes more effective and faster..........

---

