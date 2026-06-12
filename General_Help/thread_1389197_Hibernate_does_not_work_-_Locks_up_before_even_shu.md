---
title: "Hibernate does not work - Locks up before even shutting down."
date: 2010-01-24
forum: General Help
---

### Post by indstr on 2010-01-24
I am using Xubuntu 9.10, 2.6.31-17-generic kernel. Video driver: "ati"

 I have only been using Linux for less than a year now but I have never been able to get hibernate mode working. Had the same problem on previous kernels and with Nvidia drivers. Tonight I tried removing all traces of any nvidia drivers hiding in my system (I recently changed to an ATI card), and also upgrading to grub 2. Still no luck.

If I use the "hibernate" option from the shutdown menu, I just get a black screen with a blinking cursor. If I use s2disk, I get a little bit more of a hint, but still not very helpful:  

"Looking for splash system... none"
"s2disk: snapshotting system"

Then it just locks up after that....  Power is still on and it never shuts down. I have a 6 gig swap partition set up that is enabled, so it is definitely not a swap issue.

Anybody have any idea what is going on?

Any help is appreciated

---

### Post by akhilbehl on 2010-01-24
hey.. i am new to linux and ubuntu.. but i think there are some packages that need to be installed before your system can hibernate..

are you sure that you have them installed..

try sudo apt-get install hibernate.. it will pick up the dependencies itself..

may be someone more experienced can help you if it does not work..

all the best!

---

### Post by indstr on 2010-01-24
I just tried that. Interestingly, I did not already have the package installed. Unfortunately, it didn't work. It still hangs and does the exact same thing. 

:(

---

