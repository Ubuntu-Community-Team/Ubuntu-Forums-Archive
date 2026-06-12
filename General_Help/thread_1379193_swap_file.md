---
title: "swap file"
date: 2010-01-12
forum: General Help
---

### Post by eipapp on 2010-01-12
Trying to create a swap file but when I type the following I get the message: "permission denied"

dd if=/dev/zero of=/swapfile bs=1024 count=1048576

What can I do work around this ?

Thanks,

E

---

### Post by audiomick on 2010-01-12
Hallo.

You probably need "sudo" and a space before the rest of the command.

Bear in mind that I am not familiar with what you are trying to do, but it looks like something you need root privileges for. Sudo gives you that.

You will be asked for a password. It is the one you log in with. You will not see it as you type it. This is normal.

---

### Post by wojox on 2010-01-12
[https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

---

### Post by eipapp on 2010-01-12
Thanks Michael that did help but I wasn't able to resolve my issue.
I can't get my computer into suspend or hibernate mode. I have 2Gb of swap partition and thought adding a swap file would help but so far no luck. I tried the suggestions listed above Re:swap file but that didn't help either unless I'm doing something wrong but trying to follow directions given and nothing seems to work.

Thanks,
E

---

### Post by bolucpap on 2010-01-12
I was having troubles with hibernating when I found this post, hope it helps you too:

[http://ubuntuforums.org/showthread.php?t=1274368](http://ubuntuforums.org/showthread.php?t=1274368)

---

### Post by audiomick on 2010-01-12
> **eipapp said:**
> I can't get my computer into suspend or hibernate mode. I have 2Gb of swap partition and thought adding a swap file would help 

I read somewhere that hibernate needs a swap partition, and can't use a swap file. The swap partition needs to be a fraction larger than RAM. Swap is not relevant to suspend, which keeps the RAM alive for "instant wakeup".

---

### Post by eipapp on 2010-01-12
Thanks, but, nope that didn't work either.
FYI ram is 512Kb, swap partition is 2Gb

Regards,
Bruce

---

### Post by warfacegod on 2010-01-12
Do you really only have 512 *KB* RAM?

Try using gparted to make a swap.

```
sudo apt-get install gparted
```

---

### Post by eipapp on 2010-01-12
I've already done that.
Yes, only have 512 ram this is an old gateway desktop also running Win XP. Have no problems with hibernate or sleep mode in Windows but Ubuntu doesn't seem to want to cooperate. Hard drive is 130GP, have partitioned 18Gb for Ubuntu. 

Bruce

---

### Post by warfacegod on 2010-01-12
> **eipapp said:**
> I've already done that.
Yes, only have 512 ram this is an old gateway desktop also running Win XP. Have no problems with hibernate or sleep mode in Windows but Ubuntu doesn't seem to want to cooperate. Hard drive is 130GP, have partitioned 18Gb for Ubuntu. 

Bruce

In your last post, you 512 kilobytes, I assume, now, that you mean megabytes.

In gparted right click and select swap off. Right click again and select resize. You'll need to make sure there is unallocated space "next to it" for it to resize into.

---

### Post by warfacegod on 2010-01-12
After wards, don't forget to turn swap back on.

---

### Post by eipapp on 2010-01-14
Not sure I understand what you want me to do.  
> You say to resize but to what ? My swap partition is already 2Gb now, surely that is more than enough as I only have 512 Mb of ram.
> What do you mean by make sure you have unallocated space "next to it" to resize into ? I have gobs of space available so that's not a problem. Please forgive my ignorance as I'm new to Linux.
> I only mentioned the swap file as I read somewhere that in addition to having a swap partition U may also need a swap file and I don't know how to create one, if indeed I need it and it will help resolve my issue.

Thanks again for your input.......
Bruce

---

### Post by warfacegod on 2010-01-14
A swap partition is a swap file. Your swap file takes up that entire partition.

---

### Post by warfacegod on 2010-01-14
Go to: System> Admin.> Gparted> right click your Linux-swap partition. If you see it says swap off that means you have a swap file and the system is using it if it needs it. See my attachment as an example.

---

### Post by warfacegod on 2010-01-14
Okay. I get this now. I reread the thread, and you are looking to get Suspend and Hibernate working. I wasn't sure why you were messing with swap. If you have only 512 MB RAM, a 2 GB swap should do nicely. I don't think you'll need to resize it. I don't use either Suspend or Hibernate so my knowledge is thin but basically what happens is the computer puts the contents of Your RAM into the swap. So, considering your swap is 4X bigger than your RAM, there should be no issues from that aspect of the problem. I suggest starting another thread specifically concerning getting your Suspend and Hibernate working properly.

---

