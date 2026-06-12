---
title: "System Total Freeze ...Help me guys.!!"
date: 2010-12-20
forum: General Help
---

### Post by jackgow on 2010-12-20
hey guys,
                  I'm having a problem with my Ubuntu 10.10 system. After installing the OS it worked fine. But after one or two restarts it totally freezes i mean NO Ctrl+Alt+Bckspc , NO Ctrl+Alt+F1 and Ctrl+Alt+Del works for me. I have the same problem with Ubuntu 10.04 , 9.10 also. ( **Only Ubuntu version 9.04 Works fine** for me ). But i want to make use the latest one. Please help me to do this guys.

Here is my system config:
[B]
Mercury PI945GCM
Intel Dual Core
2 GB RAM
1 TB HDD[/B]

Is there anything wrong with my configuration??

my partition is like this,

[B][COLOR=DarkRed]58 GB for / (root)
20 GB for /home
20 GB swap[/COLOR][/B]

The Other partitions are NTFS for my **Windows 7 Ultimate**. ( i mean i have dual boot Ubuntu & Windows 7 ).

After Ubuntu fails some time it crush the GRUB loader, so that i can't boot windows either. Any buddy tell me why this happen to me?

I've try to install **Linux Mint 10** also but it freezes while installing..!!

Now I loaded the **openSUSE 11.4 milestone 3.**  It works fine for now but i can't connect to internet , it asks for **"linux-atm-lib" **. i don't know how to do that ..

Still i want to use the Ubuntu 10.10 Please **help me to find my problem**..!!

---

### Post by katykat on 2010-12-20
What video card are you using. 
If chip, is it ATI or Nvidia based?

---

### Post by jackgow on 2010-12-21
> **katykat said:**
> What video card are you using. 
If chip, is it ATI or Nvidia based?
  
I don't have any graphics card i use on board graphics. I mean my motherboard Mercury PI945GCM.

---

### Post by jackgow on 2010-12-25
Hey guys,
             
                  Thanks for your support and replies. But i've solved this problem of my own. Actually i does a simple change in my installation configuration. That in my old configuration i gave 58 GB space for Root (/) , this time i split the 58GB into 24GB and 34GB of partitions and install 24GB for the Root(/) and 34GB for /usr . Now the problem was almost solved for me. My Ubuntu boots, login and i can use it without freeze. But still some times i got freeze. ( for ex. installing/running a heavy software like VMware..etc). Any buddy got idea about this issue ??

---

### Post by zarthon on 2011-01-04
After something is marked solved it usually does not get that much attention.  It's much better if you have solved the main problem but have a lingering issue to post it as a new and completely different issue.

I believe your VM Ware problems could be specific rather than an example of a more general problem.
The problem with VM Ware may be buggy BIOS support for the extended viritualization CPU operations.

Check out this thread:
[http://ubuntuforums.org/showthread.php?t=1303330](http://ubuntuforums.org/showthread.php?t=1303330)

If you need more help I'd post a new thread.

Good luck!

---

