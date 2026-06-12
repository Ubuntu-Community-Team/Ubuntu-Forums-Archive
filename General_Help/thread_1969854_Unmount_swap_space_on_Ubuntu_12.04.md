---
title: "Unmount swap space on Ubuntu 12.04"
date: 2012-04-30
forum: General Help
---

### Post by maritim on 2012-04-30
Hi all!

I'm a very newbie at linux configuration (all of them) and I need some help with a problem. I installed Ubuntu 12.04 today and I choose Swap Space my D: partition on Windows 7. On this partition I had something pretty important and now I want to unmount it from Swap Space and make it normal partition like before, but I don't know how.

I search the net before posting here and I find that command # swapoff -a may help, but it give me the message "Not superuser" ...

How could I unmount my Swap Partition and recieve all original documents from it (if it's possible)?

Thanks and have a good day!

---

### Post by pqwoerituytrueiwoq on 2012-04-30
sudo swapoff -a
you could do this in [gparted](apt:gparted)

---

### Post by maritim on 2012-04-30
Ok, thanks for help, but now I still have a problem.

I use swapoff from GParted, but I still can't acces my partition. I can't see in Explorer, and I can't access it from terminal. How can I reactivate it?

---

### Post by pqwoerituytrueiwoq on 2012-04-30
i don't think you can use nautilus while gparted is open

what are yuo trying to accomplish?

---

### Post by maritim on 2012-05-01
Thanks a lot for trying to help me, but I give up about recovering the partition.
I format it yesterday and I reinstall Ubuntu on it. I allocated another splited partition for swap space.
I know that was not the best solution, but it was the only one that I thought at that moment.
However, it is okay. I recover a part of the data from another sources...

Thanks for help and have a good day!

---

