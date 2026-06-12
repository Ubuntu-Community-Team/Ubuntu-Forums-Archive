---
title: "remove hibernation/suspend from grub"
date: 2011-10-03
forum: General Help
---

### Post by ykanello on 2011-10-03
Hello,
I have been searching in the forums for a relevant answer but nothing similar so far, so I decided to post.

Recently I tried out the hibernation/suspend options in a 10.04 installation. Things didn't work very well because of some encrypted partitions, so I decided that is better idea for my case to complete shutdown/startup the system.

The problem is that each time I boot up, grub2 is trying to boot from some suspended state, which of course cannot read the encrypted partition and fails.

I need to boot it to S1 runlevel, and then bring it to runlevel 5.


Is there any idea out there of how to disable grub to search for saved machine states and try to use them?

Thanks.
Y

---

### Post by Toz on 2011-10-08
Try passing the kernel parameter **noresume** to the kernel. See: [https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot"). This should revert the swap partition back to swap space releasing the hibernate image.

---

### Post by ykanello on 2011-10-10
Yes that's true, and actually this is how I manually boot it. 
My problem is with autoboots, (once I turn on the PDU, the computer turns on -- when I am remotely connected home).
In that case I cannot access the grub menu (the solution of getting a computer with ILO, its out of the question for now, unless someone donates me an ILO card hehehe ).

The 'funny' thing is that last action was a shutdown (init 0), so there should have been no image to resume...
(funny=weird, not funny=haha (c) goonies)

---

### Post by Toz on 2011-10-10
How about manually wiping the swap space (in theory, to get rid of the resume image). Found this link: [http://www.linuxnetadmin.com/2008/11/clear-swap-space-in-linux.html]("http://www.linuxnetadmin.com/2008/11/clear-swap-space-in-linux.html").

Basically, use free to make sure you have enough real memory to hold what is in swap, then:
```
swapoff -a && swapon -a
```

It would be interesting to see what free returns for you - if the recovery image is persisting in the swap space.

---

