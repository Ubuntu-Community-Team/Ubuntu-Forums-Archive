---
title: "Lubuntu swap file"
date: 2012-07-01
forum: General Help
---

### Post by hans12345 on 2012-07-01
I have an old Dell Laptop (Latitude C610), 256 Meg RAM, 20 G HD which I want to set up for my wife to do simple stuff. I have 3 PCs with Ubuntu and 2 years experience

I installed 12.04 Lubuntu and it works - for a while.

When I start the Chromium browser it works for a while. As soon as I have a few tabs open, it starts thrashing the disk. I imagine VM >> RAM. Or maybe it is just looping. Often this is so bad that the PC is unusable and I have to force a power off (no normal shutdown possible).

Questions:
1. Can 256 Meg RAM usefully run Lubuntu?
2. When I look at the HD, there is no swap file. Is this standard in Lubuntu? If not, how big a swap partition do I need? Once the swap partition is in place, how do I make the system use it?

Your help appreciated. :p

---

### Post by kc1di on 2012-07-01
Hi hans12345,

according to the Lubuntu wiki here are the system requirements.

your 256 mb should work.

> System Requirements
A Pentium II or Celeron system with 128 MB of RAM is probably a bottom-line configuration that may yield slow yet usable system with Lubuntu. It should be possible to install and run Lubuntu with less memory, but the result will likely not be suitable for practical use.

If you install with the default I don't think it makes the swap partition for you the old saying is you should have a swap partition of 2X the size of your ram so I would make a 600mb or so one see if it helps.

---

### Post by sudodus on 2012-07-01
> **hans12345 said:**
> 
Questions:
1. Can 256 Meg RAM usefully run Lubuntu?

Well, Lubuntu 12.04 really needs more to work well
> 
2. When I look at the HD, there is no swap file. Is this standard in Lubuntu? If not, how big a swap partition do I need? Once the swap partition is in place, how do I make the system use it?

Your help appreciated. :p

You certainly need swap, I would say 1 GB. The normal install will create a swap partition. But if you have encrypted home folders, the swap area will be converted to encrypted swap. Check if that is the case for you!

I think that encrypted swap will make your slow computer even slower. So my advice is to have 1 GB swap and and to avoid encrypted folder. Probably the easiest thing would be to reinstall Lubuntu

... or try another distro, that needs less RAM. See the following thread, where I suggested Knoppix, and it solved the problem for the OP.
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=2011055_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2011055")

---

### Post by sanderj on 2012-07-01
> **hans12345 said:**
> I have an old Dell Laptop (Latitude C610), 256 Meg RAM, 20 G HD which I want to set up for my wife to do simple stuff. I have 3 PCs with Ubuntu and 2 years experience

I installed 12.04 Lubuntu and it works - for a while.

When I start the Chromium browser it works for a while. As soon as I have a few tabs open, it starts thrashing the disk. I imagine VM >> RAM. Or maybe it is just looping. Often this is so bad that the PC is unusable and I have to force a power off (no normal shutdown possible).

Questions:
1. Can 256 Meg RAM usefully run Lubuntu?
<snip>

You can run Lubuntu itself, but you cannot run Chromium in 256MB RAM (as you've experienced). Maybe, maybe you can run Midori, but that is a very basic web browser.

My advice: get more memory (if possible). Preferably 1GB.

---

### Post by hans12345 on 2012-07-01
Thanks all for your quick help.

I'll set up the swap file and look at uncrypting the home folder.

I'll report back

:-)

---

### Post by GreatDanton on 2012-07-02
> **sanderj said:**
> 
My advice: get more memory (if possible). Preferably 1GB.

With 1Gb ram your laptop will fly (however laptop memories are really expensive in my opinion). If you are not satisfied with the speed,  then you can try Knoppix, or Puppy Linux.

I prefer Knoppix, because it is very good with hardware recognition, and also have the same terminal commands like ubuntu/debian.

---

### Post by hans12345 on 2012-07-04
Report so far:

I reinstalled Lubuntu carefully and I now have a swap file. I find the alternative CD installation very confusing when it comes to the partitioning of the HD, and this time I only managed to get a swap file of 384 Meg, when I had wanted one twice that size.

I cannot tell if my problem is fixed or not, because now I have a worse problem! My mouse.

Anyone wanting to help, please look at:

[http://ubuntuforums.org/showthread.php?p=12074197#post12074197](http://ubuntuforums.org/showthread.php?p=12074197#post12074197)

When I get the mouse problem fixed, I'll return to this one and give a final report.

---

### Post by hans12345 on 2012-07-05
The problem has mutated a little. The mouse problem has disappeared, good news.

But I have the original CPU looping / disk being thrashed problem still.

It happens when I start running the browser (in Lubuntu it is Chromium) with 3 or 4 tabs open.

When I look at the task manager, the CPU used is 100%, but none of the visible tasks are using more than single digits of the CPU. Sometimes the biggest task user is taking just 5% of the CPU, but CPU usage is 100%. And the disk is very active.

The task manager reports that the total memory is 243 MB, and used is around 212 MB.

What is using the CPU?
Is 212 used out of a total of 243 acceptable?

(the problem having changed somewhat, should I open a new thread?)

---

### Post by sudodus on 2012-07-05
> **hans12345 said:**
> The problem has mutated a little. The mouse problem has disappeared, good news.

But I have the original CPU looping / disk being thrashed problem still.

It happens when I start running the browser (in Lubuntu it is Chromium) with 3 or 4 tabs open.

When I look at the task manager, the CPU used is 100%, but none of the visible tasks are using more than single digits of the CPU. Sometimes the biggest task user is taking just 5% of the CPU, but CPU usage is 100%. And the disk is very active.

The task manager reports that the total memory is 243 MB, and used is around 212 MB.

What is using the CPU?
Is 212 used out of a total of 243 acceptable?

(the problem having changed somewhat, should I open a new thread?)
I think it is busy swapping. Can you watch how much swap that is used with [FONT="Courier New"][SIZE="3"]**top**[/SIZE][/FONT] and if is changing?

If you want to run like that with more than one web page open, you need a smaller operating system, for example Knoppix or Puppy. It would definitely help with more RAM, I'd say at least a total of 512 MB.

---

### Post by hans12345 on 2012-07-07
> **sudodus said:**
> I think it is busy swapping. Can you watch how much swap that is used with [FONT="Courier New"][SIZE="3"]**top**[/SIZE][/FONT] and if is changing?

If you want to run like that with more than one web page open, you need a smaller operating system, for example Knoppix or Puppy. It would definitely help with more RAM, I'd say at least a total of 512 MB.
I agree that it looks like a swap file problem. The swap file I have is too small. How do I re-partition? I have been looking for grub or for parted but cannot find Lubuntu versions. 

There should be a grub on the live CD, but I cannot find it.

Help!

---

### Post by sudodus on 2012-07-07
> **hans12345 said:**
> I agree that it looks like a swap file problem. The swap file I have is too small. How do I re-partition? I have been looking for grub or for parted but cannot find Lubuntu versions. 

There should be a grub on the live CD, but I cannot find it.

Help!
I suggest that you use ***gparted*** to repartition your drive. And it is one the Lubuntu install iso file, so you have it when you run a live session. But ***backup*** first!!!

But I think that the main problem is that you have too little RAM. You need an operating system with more light-weight software or to change your habits and only have very few applications and files open, or get more RAM.

---

### Post by hans12345 on 2012-07-08
> **hans12345 said:**
> I agree that it looks like a swap file problem. The swap file I have is too small. How do I re-partition? I have been looking for grub or for parted but cannot find Lubuntu versions. 

There should be a grub on the live CD, but I cannot find it.

Help!
I got a new Gparted and gave myself a bigger swap file (now 3*256 M RAM size).

free and top show swap file is big enough. Indeed, the pervious 380 M size was probably big enoungh.

Top shows chromium-browser as the main user of memory. 

So it looks like:
1 - try a different browser, or
2 - buy more RAM

---

### Post by sudodus on 2012-07-09
> **hans12345 said:**
> I got a new Gparted and gave myself a bigger swap file (now 3*256 M RAM size).

free and top show swap file is big enough. Indeed, the pervious 380 M size was probably big enoungh.

Top shows chromium-browser as the main user of memory. 

So it looks like:
1 - try a different browser, or
2 - buy more RAM
OK, it is worthwhile to try a lighter browser, but there are smaller OS's too, that might leave more RAM left for browsing.

Before you buy RAM, check if you can get second-hand ram-sticks, or a trashed computer, where you can find the right kind of RAM.

---

### Post by hans12345 on 2012-07-23
The new 512 M RAM arrived today, making 768 in all, and the old Dell hums along! 
Moral: 256 M is not enough for Lubuntu + Chromium. 768 sure is.

Now I only have the mouse drift problem.

Thanks everyone

---

### Post by hans12345 on 2012-07-23
If anyone can help on the mouse drift / Jump problem, look at :
[http://ubuntuforums.org/showthread.php?t=2016162](http://ubuntuforums.org/showthread.php?t=2016162)

---

