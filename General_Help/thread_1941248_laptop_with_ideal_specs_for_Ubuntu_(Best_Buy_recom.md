---
title: "laptop with ideal specs for Ubuntu (Best Buy recommendations?)"
date: 2012-03-15
forum: General Help
---

### Post by joemartin on 2012-03-15
Hi,

Hoping someone with a lot better hardware knowledge than I can recommend a model of laptop (at Best Buy for example) that is ideal for installing Ubuntu 11.10.

I checked out Systems 76 and may end up going with them but it seems that I can spend far less by buying a Windoze machine at Big Box store and do the OS installation myself. 

Thanks for your knowledge.

---

### Post by 3Miro on 2012-03-15
System76 machines are not cheap, but for the money it would be hard to find a better deal in terms of hardware and Ubuntu support. Other machines may be cheaper, but they will not stand one-on-one vs System76.

Nobody can guarantee that Ubuntu will run on a specific laptop until someone has tried it. However, there are some general guidelines.

The most important issue is the video, as it causes most trouble under Linux. ATI video cards have great support, but ATI laptops are often times hard to find. Do not buy any machine with Nvidia below GTX560, anything below GTX560 is Optimus and you can expect big trouble. Intel graphics are weak, but they do have the best Linux support as well as battery life. For Intel graphics, it may also be a good idea to wait couple of month for their next generation Ivy Bridge, it will come with even better graphics and better battery life.

Other than that, Intel wireless has the best overall support for Linux. I used to have Broadcom and it ran fine, but it was a hassle messing with the proprietary drivers all the time. 

If you can go to the store, see if you can try a live CD on the machine before you buy it. Make sure both video and wireless work.

---

### Post by Mark Phelps on 2012-03-15
Also, when you're looking at the laptop specs, be sure to avoid anything that has Hybrid (or Switchable) Graphics.  That doesn't work well in Linux.

---

### Post by rg4w on 2012-03-15
This list of machines certified by Canonical may help:
[http://www.ubuntu.com/certification](http://www.ubuntu.com/certification)

---

### Post by 3Miro on 2012-03-15
@Mark Phelps: I think the new AMD proprietary driver would support hybrid AMD graphics, however, I am not sure if it has been released yet or if it will be included in 12.04. Hybrid AMD graphics may be a viable option, but more research needed. One should avoid Hybrid Nvidia, some people have managed to get some Optimus to sort-of work, but it is hardly worth the trouble.

@rg4w: it is good to look at lists like that, however, I just looked at System76 and the models included are very out-of-date.

@joemartin: I own a System76 Pangolin and I am very happy with it. If I am getting a laptop right now and money was an issue, I would personally buy the Lemur, there is even a discount right now. That's the best advice that I can give.

Note: it is possible that the Lemur discount it there simply to get rid of the old models and replace them with newer Ivy Bridge ones. However, this is just a speculation on my part.

---

### Post by garyed on 2012-03-15
What I did was I bought a laptop at a place that gave me a few days to return it for any reason if I didn't like it. I figured if I couldn't get it working with a live CD I'd just take it back. I took it home & put in 11.10 CD & everything seemed to work O.K. so I made a set of Windows recovery CD's,repartitioned the drive & installed Ubuntu for good. This way I could get what I thought was the best bang for my buck & then see if the computer will run good with Ubuntu with the option to return it within the given time line.

---

### Post by gordintoronto on 2012-03-15
I have an HP G62 which works perfectly with Ubuntu 11.10. Sadly, it's 18 months old, so it's no longer for sale. It has an AMD 2.1 GHz processor and ATI graphics. Webcam and wireless work "out of the box." It was the least expensive real laptop available at the time I bought it.

I am surprised that some of the current crop of laptops are actually slower, and not much cheaper.

---

### Post by jerome1232 on 2012-03-15
> **3Miro said:**
> 
The most important issue is the video, as it causes most trouble under Linux. ATI video cards have great support, but ATI laptops are often times hard to find. Do not buy any machine with Nvidia below GTX560, anything below GTX560 is Optimus and you can expect big trouble.

I'm curious about the warning about nvidia below GTX560, why do you caution against those cards? I have a GTS450 in my desktop and it works fantastically.

---

### Post by 3Miro on 2012-03-15
> **jerome1232 said:**
> I'm curious about the warning about nvidia below GTX560, why do you caution against those cards? I have a GTS450 in my desktop and it works fantastically.

I mean 5xx series, but lower than 560. I don't think they sell 4xx series anymore.

On the laptops, anything below 560 is Optimus, which means that the system has two graphics cards (Nvidia and Intel) and it switches between them depending on whether or not you have plugged the power. When you are plugged in an outlet, you use the powerful Nvidia, when you are on battery, you work with the weaker Intel that gives you longer battery life. The idea is good, but Nvidia doesn't provide Optimus driver for Linux, hence Ubuntu will not work on it.

In recent months, people have managed to get some things working, but it is still hassle to setup and simply not worth it.

Nvidia GTX560 and higher come as stand-alone and work great. The only issue is that those will not give you much of a battery life.

PS: Optimus is on laptops only, Nvidia desktops work fine.

---

### Post by philinux on 2012-03-15
Acer with Intel onboard works very well. I have an acer 1410. Hdmi out too.

Not too expensive either.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-03-16
> **philinux said:**
> Acer with Intel onboard works very well. I have an acer 1410.

Sadly, not every Acer with Intel on board works with Ubuntu. I have an Aspire TimelineX 5830TG and there's a number of issues which can be fixed after installing Ubuntu (hotkeys, brightness, battery life, graphic drivers), and another number which have yet to see the fixes. Foxconn Bluetooth adapter on my computer isn't recognized by Linux Kernel at all, so Bluetooth isn't usable. Also, it's got switchable Intel/nVidia graphic set, which of course doesn't work either, so in order to have a normal battery life, nVidia GPU needs to be disabled in BIOS. Thank God there is at least an option for that. Without it, my TimelineX, advertised to have 9+h battery life would drain the battery in no more than 1,5h, with significant noise increase.

---

### Post by kurt18947 on 2012-03-16
I don't know how they would fit your budget, but Thinkpads generally "just work" with Linux, it seems.  The 'problem children' as others have alluded to are hybrid graphics and certain wireless chipsets; Broadcom seems most prominent there.  I took a risk and bought an X61 off Ebay.  It was plug -n- play, no issues, $127 :).  I'm an AMD fan with desktops, I guess it's a root-for-the-underdog thing. For laptops where it's impractical to swap a component if necessary, I think all-Intel is the safe route.

---

