---
title: "Definition of kvec"
date: 2010-04-21
forum: General Help
---

### Post by Sikandar on 2010-04-21
I need to clarify kernel_sedmsg function which sends tcp packets over network, for that i need to know the definition of struct kvec...
i searched it a lot on google..but just getting its use and not definition....
i even wrote definition of struct kvec in google but invain..
Can someone also give me some tricks to search the exact things on google and fast as well...
Most of the times i end up wasting lot of time but still dont get the results on google ...u may also suggest me some other BETTER search engine....
My disro is UBUNTU 9.04
kernel version:2.6.30
Thank you.

---

### Post by Sikandar on 2010-04-21
Hey,
I finally got its definition in linux-2.6.30/include/linux/uio.h
I used grep command to find it out.
But i have another doubt regarding why to use __kernel_size_t; as it is defined same as size_t in /usr/include/linux/types.h

---

