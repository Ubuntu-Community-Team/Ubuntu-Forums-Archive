---
title: "Sudden logout on GNOME"
date: 2011-03-26
forum: General Help
---

### Post by Bas1234567 on 2011-03-26
Hello,

Since a month or so, sometimes in the middle of doing something, my screen goes black for a second, and then displays the Ubuntu login screen. When I then login again all my open programs are gone.

Any tip how to troubleshoot this when it happens again? Is there a log or something I can check for a possible cause?

Thanks in advance,

Bas

---

### Post by Frogs Hair on 2011-03-26
It could be video card related. Check your XORG.0.Log in System > Administration > log file viewer right after it happens

---

### Post by Bas1234567 on 2011-04-07
Thanks for the suggestion, I looked into XORG.0.Log and did not see anything suspicious (but I don't know much about it). 

I have put the log from just after it happens at:

[http://pastebin.com/qeQrSNrp]("http://pastebin.com/qeQrSNrp")


It starts to happen more often now, about every hour I get kicked out of my session. Any other suggestions on how to troubleshoot?

Thanks,

Bas

---

### Post by Bas1234567 on 2011-04-07
After checking what I was doing when it happens, it seems to be correlated to doing a google search in firefox. It is not that it happens always when I do that, but when I get logged out, I was always doing a google search.

Is it possible that a firefox crash causes somehow my session to be aborted / ended / crashed ?

Is there any log that I can check for programs doing illegal things or something?

Thanks,

Bas

---

### Post by pi3ch on 2011-05-19
I have similar issue here, sudden logout on ubuntu 11.04. I think it might be related to my wireless driver. I have problem with wireless N connection. also I found this bug [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/778490](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/778490) .

I m using DELL XPS M1330

---

### Post by abelmaio on 2011-06-03
I also have this problem in two different computers.

And I can say it's realling annoying. Imagine you working and a second later all is gone. :(


On of my computers is an Asus eeePC 1001P with Ubuntu 11.04. The other is a Toshiba (can't remember the model now) with Linux Mint 11 (Ubuntu 11.04 based). 

On my netbook I always use a Wireless connection while on the Mint notebook I use a Ethernet connection with the Wireless turned off.

I think this happens when I'm using Chrome. Today, in less than an hour, this problem happened two times no my netbook.


After reading some posts, I don't know if the problem is the browser because some use Firefox, other Chrome. Don't know if the problem is the Wireless driver, because one of my computers use Wireless all the time and the other is turned off, all the time.


I'm just working, almost all the time web-based, and then my screen goes black, some lines appear with a message like "Starting anac(h)ronistic cron anacron" and I have no idea about why this problem is happening.


I really love Linux, and want to use it all the time, but this problem is a very annoying one.


Can someone please help? :(




Thanks
AM


EDIT: One more thing, this never happened in previous versions like Ubuntu 9.10, 10.04, 10.10 and Linux Mint 10.

---

### Post by abelmaio on 2011-06-04
Hello again.


I read a tip that say to install this PPA.

```
https://launchpad.net/~ubuntu-x-swat/+archive/x-updates
```


I already installed and haven't got the problem yet.
But I don't know if it's in fact working.

This problem is so random that makes very difficult to test.


You can test this solution. But I can't garantee that this will solve the problem.

If the problem appears again, the first thing that I'll do is to post here for you knowing that this isn't the solution (at least for me).

If you read this and I haven't posted yet, maybe this can solve. :p



AM

---

### Post by dozycat on 2011-06-04
it looks like you will be need to check all the logs in /var/log which as changed that day with tail, and maybe find a report with the right time.

---

### Post by abelmaio on 2011-06-04
> **dozycat said:**
> it looks like you will be need to check all the logs in /var/log which as changed that day with tail, and maybe find a report with the right time.
Well, I'll do that when the problem happens again.

I tried that in the past but I found nothing. But I'll try again if happens again.

Thanks,
AM

---

### Post by abelmaio on 2011-06-14
Just to tell that this problem happened again... Even after I installed this packages...

And now this happened when I was doing a system update. 


I tryied to search on the /var/log folder but I haven't found anything that might be relevant... And don't know were to exactly search....

Can someone help me? 

Could the problem be because of the Intel Graphic Chip?



AM

---

