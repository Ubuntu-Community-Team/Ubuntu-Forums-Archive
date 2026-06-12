---
title: "Wireless USB Stick and Linux"
date: 2012-03-14
forum: General Help
---

### Post by Spewed on 2012-03-14
I'm wanting to get a wireless adapter for my desktop so that I can connect wireless using my computer and due away with my ethernet chord. 

I know there are Linux compatible USB wireless adapters available, but my question is can I just pick up any USB Wireless adapter and have it work with Linux? 

Also, what about the PCI versions of wireless adapters, are all of those compatible with Linux?

My main reason for doing this is that I trip of the chord all the time, I'm also sick of the crappy Interent issues I've been having with Ubuntu and finding no resolution. I do however see many resolutions for Wireless versions, so I'm thinking maybe this will help me.

---

### Post by winh8r on 2012-03-14
Just an opinion you might want to consider before embarking on this, you will get a more stable and reliable internet connection if you are hardwired using a good quality cat5 ethernet cable than you will using a wireless connection.

---

### Post by Spewed on 2012-03-14
> **winh8r said:**
> Just an opinion you might want to consider before embarking on this, you will get a more stable and reliable internet connection if you are hardwired using a good quality cat5 ethernet cable than you will using a wireless connection.

Is this a Ubuntu only issue? Because I'll only be about 10 feet 15 feet away from my modem. With today's hardware I think a reliable wireless USB stick is completely within the realm of possibilities. One would think so anyway, or is there specificially a Ubuntu issue with that sort of thing? 

For example my laptop gets just as good of a signal here in my room as does my desktop computer(which I use primarily). 

So are you telling me that using Ubuntu on that laptop would make the connection more unreliable?

---

### Post by winh8r on 2012-03-14
No, what I am saying is that a hard wired connection is better than a wireless connection on any computer using any operating system. The signal is going directly into the machine on a cable, whereas the wirelss signal has to find its way to the machine. It is not Ubuntu specific.

What issues are you having with your ethernet connection (other than tripping over the cable!)?

---

### Post by Spewed on 2012-03-14
> **winh8r said:**
> No, what I am saying is that a hard wired connection is better than a wireless connection on any computer using any operating system. The signal is going directly into the machine on a cable, whereas the wirelss signal has to find its way to the machine. It is not Ubuntu specific.

What issues are you having with your ethernet connection (other than tripping over the cable!)?

The browsing is INCREDIBLY slow at all times, as to where with Windows is blazes. I've disabled IPV7, and tried numerous other things including switching DNS servers(reverted back as no changes were evident). It's just an extreme hassle to browse the Internet with Ubuntu for me. For example, it took me about 2 minutes to beable to reply to you. On windows I could have done this in literal seconds. It's a pain in the *** and bothers the hell out of me and has since day 1 of installing Ubuntu. This USB Stick was going to be my last straw before uninstalling Ubuntu entirely and forgetting about it(even though I prefer it as my primary OS, the Internet issues are far too much to deal with).

I've already posted a thread or two about it, no one has been able to help whatsoever. So I assume my last resort could be a USB stick and giving that a try.

---

### Post by Spewed on 2012-03-14
> **winh8r said:**
> No, what I am saying is that a hard wired connection is better than a wireless connection on any computer using any operating system. The signal is going directly into the machine on a cable, whereas the wirelss signal has to find its way to the machine. It is not Ubuntu specific.

What issues are you having with your ethernet connection (other than tripping over the cable!)?

The browsing is INCREDIBLY slow at all times, as to where with Windows is blazes. I've disabled IPV, and tried numerous other things including switching DNS servers(reverted back as no changes were evident). It's just an extreme hassle to browse the Internet with Ubuntu for me. For example, it took me about 2 minutes to beable to reply to you. On windows I could have done this in literal seconds. It's a pain in the *** and bothers the hell out of me and has since day 1 of installing Ubuntu. This USB Stick was going to be my last straw before uninstalling Ubuntu entirely and forgetting about it(even though I prefer it as my primary OS, the Internet issues are far too much to deal with).

I've already posted a thread or two about it, no one has been able to help whatsoever. So I assume my last resort could be a USB stick and giving that a try. Also from the time I click "Submit" on this post it will be another 2-3 minutes before it actually submits and lets me move on to other things.

---

### Post by Spewed on 2012-03-14
> **winh8r said:**
> No, what I am saying is that a hard wired connection is better than a wireless connection on any computer using any operating system. The signal is going directly into the machine on a cable, whereas the wirelss signal has to find its way to the machine. It is not Ubuntu specific.

What issues are you having with your ethernet connection (other than tripping over the cable!)?

The browsing is INCREDIBLY slow at all times, as to where with Windows is blazes. I've disabled IPV6, and tried numerous other things including switching DNS servers(reverted back as no changes were evident). It's just an extreme hassle to browse the Internet with Ubuntu for me. For example, it took me about 2 minutes to beable to reply to you. On windows I could have done this in literal seconds. It's a pain in the *** and bothers the hell out of me and has since day 1 of installing Ubuntu. This USB Stick was going to be my last straw before uninstalling Ubuntu entirely and forgetting about it(even though I prefer it as my primary OS, the Internet issues are far too much to deal with).

I've already posted a thread or two about it, no one has been able to help whatsoever. So I assume my last resort could be a USB stick and giving that a try. Also from the time I click "Submit" on this post it will be another 2-3 minutes before it actually submits and lets me move on to other things.

---

### Post by winh8r on 2012-03-14
Can you run

```
ifconfig
```

in the terminal and post the results please?

---

### Post by Spewed on 2012-03-14
eth0      Link encap:Ethernet  HWaddr 00:30:67:c3:fc:ba  
          inet addr:192.168.254.111  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::230:67ff:fec3:fcba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15755 errors:0 dropped:15755 overruns:0 frame:15755
          TX packets:14736 errors:0 dropped:86 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13247301 (13.2 MB)  TX bytes:2184013 (2.1 MB)
          Interrupt:43 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18615 (18.6 KB)  TX bytes:18615 (18.6 KB)

---

### Post by winh8r on 2012-03-14
Ok , I see a lot of dropped packets there on eth0, now I am not waving a magic wand here but I think there is an issue with your network card using the wrong driver. If I remember correctly, and I am trying to remember, Realtek drivers have been problematic with the latest kernel.

I think there is a patch for this which cures it.


Check back here in a bit, whilst I go and dig around a bit for more info.


can you post the output of 

```
lspci
```

from the terminal please

---

### Post by kurt18947 on 2012-03-14
I tend to agree with winh8r,  it's far more common to  have wireless connection problems than it is to have wired connection problems.  You could open a terminal and type "ping" and see what numbers are shown.  Then open a "DOS" or "Cmd" window in Windows and do the same thing.  See if the numbers are similar.  There are people on this site that are VERY knowledgeable about diagnosing networking problems.  I'm not one.  Like the proverbial blind hog, I do sometimes get lucky though :). 

I'd suggest changing ethernet ports on the router or changing cables but if they work with Windows,  it's hard for me to believe there's a hardware problem.  Still, it might be worth a trying a hard reset on the router,  that usually involves pressing a recessed button.  Sometimes they get flaky over time and a hard reset solves the problem.  Try a different ethernet port on the back of the router.  If you have two pieces, a 'modem' and a router, you could try plugging directly into the 'modem' to take the router out of the system.

What version of Ubuntu are you running?  If you choose to try a wireless card, Ubuntu version can matter.  I have an old USB G speed adapter that has been plug -n-play with every Ubuntu release I've tried since 9.x.  it uses an rtl-8187b chip set
[http://www.trendnet.com/products/proddetail.asp?prod=265_TEW-424UB&cat=15](http://www.trendnet.com/products/proddetail.asp?prod=265_TEW-424UB&cat=15)

If you're using 11.04 or newer there are faster adapters that have been plug -n-play for me on 11.10 and 12.04 (so far)

[http://www.trendnet.com/products/proddetail.asp?prod=200_TEW-649UB&cat=169](http://www.trendnet.com/products/proddetail.asp?prod=200_TEW-649UB&cat=169)
and its twin that can sometimes be found cheaper on Ebay
[http://www.dlink.com/products/?pid=738](http://www.dlink.com/products/?pid=738)
These both use the rtl-8192SU chipset which had a rough debut on Linux but now seems to work pretty well on newer distros.  Still isn't plug-n-play on 10.10 and older though AFAIK, it requires a firmware download and copy to a certain location.

I've had good luck with this one as well but same deal,  isn't plug-n-play on 10.10 and older.
[http://support.netgear.com/app/products/model/a_id/12995](http://support.netgear.com/app/products/model/a_id/12995)

I hope you're able to solve your problem.

---

### Post by winh8r on 2012-03-14
I found what I was looking for and it seems that my memory did serve me well on this occasion!!!

If you do have a realtek card then go here and follow the instructions and see how it goes for you:

[http://ubuntuincident.wordpress.com/2011/12/15/wired-network-speed-is-very-slow/]("http://ubuntuincident.wordpress.com/2011/12/15/wired-network-speed-is-very-slow/")

If yours is not a realtek then I would still strongly suspect that the card is using the wrong driver as this is often the cause of large amounts of dropped packets, and is confirmed when the system will run well on another OS with different drivers.

Post back and let me know how you get on with it.

---

### Post by Spewed on 2012-03-14
> **winh8r said:**
> I found what I was looking for and it seems that my memory did serve me well on this occasion!!!

If you do have a realtek card then go here and follow the instructions and see how it goes for you:

[http://ubuntuincident.wordpress.com/2011/12/15/wired-network-speed-is-very-slow/]("http://ubuntuincident.wordpress.com/2011/12/15/wired-network-speed-is-very-slow/")

If yours is not a realtek then I would still strongly suspect that the card is using the wrong driver as this is often the cause of large amounts of dropped packets, and is confirmed when the system will run well on another OS with different drivers.

Post back and let me know how you get on with it.

I am following the tutorial. I downloaded the driver, and am trying run the autorun file as per the command stated on the tutorial, and it states "Command not found."

I extract it to my desktop for quick reference, and here is the command I entered giving me the command not found error. 

sudo ./autorun.sh

---

### Post by winh8r on 2012-03-14
Put it in your home folder.

extract it.

open terminal and enter

```
cd ./r8168-8.028.00
```

then enter the

```
sudo ./autorun.sh 
```

that should work.

---

### Post by Spewed on 2012-03-14
> **winh8r said:**
> Put it in your home folder.

extract it.

open terminal and enter

```
cd ./r8168-8.028.00
```

then enter the

```
sudo ./autorun.sh 
```

that should work.

You are a life saver. Thank you. ^_^ That definitely worked. THANK YOU SO MUCH. I've been trying to figure this out for weeks. This seemed to do the trick.

---

### Post by winh8r on 2012-03-15
No problem, glad I could be of some help to you.

(now all you need to do is stop falling over the cable!!!!)

Good Luck.

---

