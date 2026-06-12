---
title: "Installation Help on 2 HDD's"
date: 2010-11-23
forum: General Help
---

### Post by lifzunik on 2010-11-23
Hi

I have 2 HDD's and want to install only Ubuntu 10.10 64bit.

One HDD is 1TB and the other one is 320GB...

4GB of RAM.

What could be the ideal setup?? for root, swap, and home???

When I searched in web I came to know that I can have /home as seperate partition...

Now my confusion is, if I want to install Ubuntu on 320GB HDD, I can make 20GB as root and 8GB as swap and the rest would be /home....so what the other 1TB HDD would do??? How do I setup second HDD???

---

### Post by itang sanjana on 2010-11-23
> **lifzunik said:**
> .. if I want to install Ubuntu on 320GB HDD, I can make 20GB as root and 8GB as swap and the rest would be /home....so what the other 1TB HDD would do??? How do I setup second HDD ..

8GB for swap is too much, max is 2GB CMIIW
maybe you can use your 1TB as /data partition? understanding fstab is the doorway ..HTH

---

### Post by lifzunik on 2010-11-23
If I use hibernation then I would required atleast of the RAM size and that I mentioned 4GB...so some of them say SWAP we should have atleast 2xRAM...

---

### Post by sikander3786 on 2010-11-23
If you've large amount of RAM, RAM X 2 is not the absolute formula. If you need to hibernate, Swap = RAM would be enough.

> if I want to install Ubuntu on 320GB HDD, I can make 20GB as root and 8GB as swap and the rest would be /home....so what the other 1TB HDD would do??? How do I setup second HDD???

As I see you have plenty of disc space, assign 30 GB to root, 4 GB (or you can have 8 GB but that would be useless) swap and the rest as /home.

You can format the 2nd HDD to ext3/ext4, use it as a data partition and mount it in fstab as already been mentioned.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

