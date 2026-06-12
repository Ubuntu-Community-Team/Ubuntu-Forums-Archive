---
title: "unnecessary use of swap space slowing everything down"
date: 2010-02-01
forum: General Help
---

### Post by ireneshusband on 2010-02-01
I have 3GB ram on my laptop, which means that most of the time I can manage fine without needing to use swap memory. However occasionally I have hit the limit and found my machine thrashing itself stupid. Because of this I installed swapd. Unfortunately since doing this the disk seems to be unusually active and my desktop often very unresponsive. And I find that I now have 0.5GB of swap, even when my physical RAM is less than 50% used according to the KDE System Monitor plasmoid (htop however reports physical RAM to be nearly full). Doing a rough sum of the memory usage of the most memory-hungry programs running, the System Monitor plasmoid's lower figure looks to be about right.

I've tried various high and low values for swap file size in /etc/swapd.conf, but it doesn't solve the problem. I've also eliminated all the other possible causes of excessive disk access I can think of, such as misbehaving newly-installed Amarok plugins (by killing Amarok), and file sharing.

What ought to happen is that swap space should not be used at all until memory use hits the threshold specified in /etc/swapd.conf, and swap files should be destroyed once they have not been needed for a certain time (default is 60s). So why am I getting all this unnecessary frantic swapping, or at least why is swap space being used, even when I haven't got much going except KDE, Skype and Firefox?

Many thanks

---

### Post by philinux on 2010-02-01
Maybe some help from here. My system uses no swap unless I hibernate.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by egalvan on 2010-02-01
do you  have a swap **partition**?
if yes, how large?
Is it enabled & functional? Verified to be enabled & functional?
(I have seen a few installs which had swap non-functioning,
usually due to in-correct UUID's,
A quick "free -m" will tell the tale)


If no swap **partition**,
why not? What was/is the reasoning behind "no swap **partition**"?

Why are you using swapd?
Reasoning?

---

### Post by ireneshusband on 2010-02-01
@philinux: Thanks for that. I've specified vm.swappiness=10 in /etc/sysctl.conf. We'll see what happens when I reboot. 

That said, I seem to have more than one thing going on here. I've still been getting a lot of disk activity even after stopping swapd and doing a swapoff -a. It looks like more investigation is in order.

@egalvan: The very short answer is that if it's good enough for Apple and Microsoft, why not for Linux? There is no disadvantage in using swap files with a 2.6 kernel.

---

### Post by Herman on 2010-02-01
Firstly, thanks for letting me know about [swapd]("http://linux.about.com/cs/linux101/g/swapd.htm") , this is the first time I've noticed it, and it looks like and interesting idea. I think I will try that out. That might give me a little more room in my 4GB EeePC SSD installation.

I don't know why your system needs so much swap unless you're doing something very memory intense. It seems like something's definitely set up wrong there. My systems hardly use any swap area at all, even when I do have a lot of apps open.  I don't know much about swapd yet.

I normally just leave swappiness set at the default Ubuntu settings, but when I install in flash memory I like to make a swap file instead of a swap partition (                         [HOWTO: Use swapfile instead of partition and hibernate]("http://ubuntuforums.org/showthread.php?t=1042946&highlight=swapfile")  - by iva2k), and set swappiness to 10 by adding the line vm.swappiness=10 to the bottom of /etc/sysctl.conf and that seems to help performance in flash memory. (at least it seems that way to me).
See: [Performance tuning with 'swappiness']("https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27") - Ubuntu Community Docs.

Apparently swappiness is quite a debatable topic, if you take a few seconds to read the following two links you'll see what I mean, 

[Speed up your system by avoiding the swap file]("http://fosswire.com/post/2009/02/sysctl-swappiness/") - FOSSwire, and [Linux: Tuning Swappiness]("http://kerneltrap.org/node/3000") - Kernel Trap

---

### Post by egalvan on 2010-02-01
> **ireneshusband said:**
> @egalvan: The very short answer is that if it's **good enough for Apple and Microsoft**, why not for Linux?

The short answer would be the design-philosophy differences between the systems.

Even shorter answer would require too much space :)
(ref: Eric Raymond, Richard Stallman, John "Maddog" Hall, FOSS/OSS, Unix Design, Bill Gates, etc)


>  There is no disadvantage in using swap files with a 2.6 kernel.

Absolutely true, but remember, swapd  uses **DYNAMIC** files...
swap partitions and regular swap files are **STATIC**.
Does the research show any difference?


Again, a simple "free -m" will shed much light on the subject.

---

### Post by nanotube on 2010-02-01
i just set my vm.swappiness to 0, that way swap doesn't get used unless it /absolutely has to/. that keeps things nice and fast. 

that setting is especially important on computers with SSD drives (like netbooks), since swap tends to cause a lot of disk activity, while ssds are by nature limited to some number of writes. 

(and while you're at it, set the 'noatime' mount option in fstab, that would reduce useless disk activity even more.)

---

### Post by ireneshusband on 2010-02-01
Setting swappiness to 10 in /etc/sysctl.conf and rebooting has made a world of difference. At the moment it doesn't look like I'll need to go lower than 10, but we'll see.

I'll give noatime a try next time I reboot. Am I right to think that there is absolutely nothing to be lost by using noatime for the average user?

---

### Post by nanotube on 2010-02-02
> **ireneshusband said:**
> 
I'll give noatime a try next time I reboot. Am I right to think that there is absolutely nothing to be lost by using noatime for the average user?

yes indeed.

---

### Post by NightwishFan on 2010-02-02
I use vm.swappiness=100 and my swap is almost never used even though I only have 870mb of RAM. It is not used even when I run a large program like Battle For Middle Earth 2 or Firefox.

---

