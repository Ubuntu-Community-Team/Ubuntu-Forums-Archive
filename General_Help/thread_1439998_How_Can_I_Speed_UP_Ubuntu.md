---
title: "How Can I Speed UP Ubuntu?"
date: 2010-03-26
forum: General Help
---

### Post by joek71 on 2010-03-26
Hi guys

Is there a way to speed up Ubuntu load time, response time, just over all speed up. 

Thanks

---

### Post by kerry_s on 2010-03-26
use a lighter version:
[http://lubuntu.net/about](http://lubuntu.net/about)
download:
[http://people.ubuntu.com/~gilir/lubuntu-lucid-beta1.iso](http://people.ubuntu.com/~gilir/lubuntu-lucid-beta1.iso)

---

### Post by Enigmapond on 2010-03-26
Maybe this thread will help you stop unused processes at the start...just be careful and if you don't know something...ask first but, this helped me turn off processes I don't use and the boot time accelerated.

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

### Post by steve161 on 2010-03-26
I have done most of those tweaks and , honestly, I have not noticed a difference.  But, depending on your system, turning off unnecessary services could speed things up.  There are some in Ubuntu that most people won't use.  The one thing I noticed that appeared to help is to reduce the swappiness value per:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by clhsharky on 2010-03-26
HI

Im going with kerry_s on this, along with a full or slow hard drive.

Sharky

---

### Post by Enigmapond on 2010-03-26
Right I would also give that a try...

To check the swappiness value

```
cat /proc/sys/vm/swappiness
```To change the swappiness value A temporary change (lost on reboot) with a swappiness value of 10 can be made with

```
sudo sysctl vm.swappiness=10
```To make a change permanent, edit the configuration file with your favourite editor:

```
gksudo gedit /etc/sysctl.conf
```Search for vm.swappiness and change its value as desired. If vm.swappiness does not exist, add it to the end of the file like so:

vm.swappiness=10

Save the file and reboot. 

Good Luck!

---

### Post by oldfred on 2010-03-27
Swap is 10 times slower than memory. If you are using swap a lot you may need to add RAM memory. It is relatively cheap now and it the lowest cost performance improvement you can do regardless of operating system.

---

### Post by steve161 on 2010-03-27
Agreed.  But when I was had swappiness at the default of 60, my system never used it.  I still noticed a difference when I set it to 10.  Granted, I have no benchmarks, and it was just my observation.

---

### Post by Enigmapond on 2010-03-27
Agree to all the above and steve161, here is your benchmark. I have 750MB of RAM. Prior to changing the swapinesss to 10 it was always using at least 20% of the swap and about 65% max of RAM. Since I made the change down to 10, the swap is never utilized and I almost never get above 60% of RAM...so for me...it has made a drastic difference.

Cheers!:)

---

### Post by joek71 on 2010-03-27
Hey I tried the gksudo gedit /etc/sysctl.conf but i dont have vm.
in that file i looked at if few times and i dont have it.

thanks

---

### Post by wojox on 2010-03-27
Just add this at the bottom of the file like Enigmapond said and save it:

```
vm.swappiness=10
```

---

### Post by tkoco on 2010-03-27
In addition to all the good advise, I would also look at which Xorg driver is being used with the graphics card on your system. The performance difference between a basic 2D driver vs an accelerated 3D driver is very noticable.

---

### Post by joek71 on 2010-03-27
Ok guys thank you for all your help.
These are my comp specs:
AMD Opteron 175 + OverClocked to 2.7
2 Gig of RAM OCZ
2 Raptors
7800GT Nvidia card.

Is there a way to make Ubuntu load and run any gaster then I have it now?

---

### Post by wojox on 2010-03-27
Only other thigs I could think of would be Boot Up Manager:

```
sudo apt-get install bum
```

And Bleachbit, to clean out old files stacking up.

```
sudo apt-get install bleachbit
```

---

### Post by joek71 on 2010-03-27
Thanks will try it out.

---

