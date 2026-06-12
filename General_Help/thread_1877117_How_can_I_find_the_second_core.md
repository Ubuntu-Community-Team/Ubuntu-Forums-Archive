---
title: "How can I find the second core?"
date: 2011-11-07
forum: General Help
---

### Post by writalnaie on 2011-11-07
I've installed Ubuntu 11.04 -i386 on a two-way machine, for each core there are 8 CPUs (4 real, with Intel Hyperthreading technique). After installation, I can only find the 8 CPUs in the "System Monitor" tool. I think Ubuntu only identify the first core, and how can I find the second core?

I've also installed Ubuntu 11.04-x86_64, and Fedora 9, and "System Monitor" in both the two systems displays 16 CPUs, so I wonder it's the problem of my Ubuntu 11.04-i386.

In fact, when I replaced the kernel in Ubuntu 11.04-i386 and Fedora 9 with 2.6.39.4 compiled by myself (with the same configuration), Ubuntu still can not find the second core, but Fedora can.

So the question is how to make Ubuntu 11.04-i386 finding the second core?

---

### Post by dcstar on 2011-11-08
> **writalnaie said:**
> I've installed Ubuntu 11.04 -i386 on a two-way machine, for each core there are 8 CPUs (4 real, with Intel Hyperthreading technique). After installation, I can only find the 8 CPUs in the "System Monitor" tool. I think Ubuntu only identify the first core, and how can I find the second core?

I've also installed Ubuntu 11.04-x86_64, and Fedora 9, and "System Monitor" in both the two systems displays 16 CPUs, so I wonder it's the problem of my Ubuntu 11.04-i386.

In fact, when I replaced the kernel in Ubuntu 11.04-i386 and Fedora 9 with 2.6.39.4 compiled by myself (with the same configuration), Ubuntu still can not find the second core, but Fedora can.

So the question is how to make Ubuntu 11.04-i386 finding the second core?

[http://ubuntuforums.org/showthread.php?t=832723](http://ubuntuforums.org/showthread.php?t=832723)

---

### Post by writalnaie on 2011-11-08
> **dcstar said:**
> [http://ubuntuforums.org/showthread.php?t=832723](http://ubuntuforums.org/showthread.php?t=832723)

I've solved the problem by recompiling the kernel with "Processor type and features --> Maximum number of CPUs" changed to 16.

The problem lies that, after downloaded from [www.kernel.org]("http://www.kernel.org"), the option above is 8 by default in Ubuntu 11.4 while 32 in Fedora. So although I did not revised the value (thus, I think they are the same), they are different.

Thank you!

---

### Post by dcstar on 2011-11-08
> **writalnaie said:**
> I've solved the problem
..........
Thank you!

Then please read below and mark the thread.

---

