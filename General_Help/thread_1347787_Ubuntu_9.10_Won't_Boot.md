---
title: "Ubuntu 9.10 Won't Boot"
date: 2009-12-06
forum: General Help
---

### Post by silvershadow169 on 2009-12-06
I've been using Ubuntu for more than a month now and it worked fine. But now, everytime that I want to boot into Ubuntu, a black screen with "GNU GRUB verion 1.97~beta4" appears. Anyone got any idea for fixing this?

Thanks

---

### Post by thomas.b.pringle on 2009-12-07
I think this is similar to the problem discussed here:

[http://ubuntuforums.org/showthread.php?p=8457539&posted=1#post8457539](http://ubuntuforums.org/showthread.php?p=8457539&posted=1#post8457539)

and i filed a bug here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/493733](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/493733)

Tom

---

### Post by Dubras on 2009-12-18
Is there any fix for this problem yet? 

Thanks.

---

### Post by skyme on 2010-01-09
I have the same problem. I installed updates and now it won't boot past that same message. This is the reason why Ubuntu is so frustrating. I like it and I have recommended it to my friends who in turn install it on their systems and then it starts doing stuff like this. I have reinstalled it 3 more times to see if I can get it to boot and it does not work. I guess it's off to Windows 7 and no more recommending it to anybody else. When you ask for help, no one ever seems to respond. Whoever in the world decided to release updates to make it do this obviously doesn't really know what they are doing and should stop sending out updates.

---

### Post by Leppie on 2010-01-09
> **silvershadow169 said:**
> I've been using Ubuntu for more than a month now and it worked fine. But now, everytime that I want to boot into Ubuntu, a black screen with "GNU GRUB verion 1.97~beta4" appears. Anyone got any idea for fixing this?

Thanks

boot with your livecd, then open a terminal and issue the following command and post the output:
```
sudo blkid
```

---

