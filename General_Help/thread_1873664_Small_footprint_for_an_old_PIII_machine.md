---
title: "Small footprint for an old PIII machine"
date: 2011-11-01
forum: General Help
---

### Post by notuo on 2011-11-01
Hi.  I am new here in the linux environment.  

I like to revive a pentium III (733Mhz, 384MB) in order to have a local web server, nothing else.

Is there any suggestions for this?

Thanks in advance,

---

### Post by LowSky on 2011-11-01
Damn Small Linux, Puppy Linux, Debian.. maybe a few more

---

### Post by wolfen69 on 2011-11-01
Check out [Deli(cate)]("http://delicate.tavvva.net/") linux. DeLi(cate) is a fork of DeLi Linux 0.8 targeted to very old and low RAM computers (486 -> Pentium III).

---

### Post by cariboo on 2011-11-01
If all you want is a web server, install the server iso, be aware that the Ubuntu server doesn't come with a gui of any sort, but once things are set up you can just shove the server under a desk, or in a corner and access it remotely.

With the low resources of the system you intend to install on, you won't be very happy serving dynamic web pages, so I'd suggest using nginx, available in the repositories to serve your static web pages.

---

### Post by Dragonbite on 2011-11-02
Should be good enough for a web server.  I've been running on P3s @ 700 MHz just fine.

At first I started without a GUI, then I added one.  Not the best move, it dragged things down some (mostly bootup but you don't necessarily use that much with a server).

---

### Post by Lars Noodén on 2011-11-02
You might look at nginx instead of Apache.

---

### Post by philinux on 2011-11-02
Moved to General Help.

---

### Post by snowpine on 2011-11-02
Ubuntu server is a fine choice and you may find this guide helpful:

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

As a footnote I recently replaced both of my PIII's with low-price Atom hardware; performance is quieter, cooler, etc. and the small footprint cleaned up my desk area significantly.

---

### Post by Dragonbite on 2011-11-02
> **snowpine said:**
> Ubuntu server is a fine choice and you may find this guide helpful:

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

As a footnote I recently replaced both of my PIII's with low-price Atom hardware; performance is quieter, cooler, etc. and the small footprint cleaned up my desk area significantly.

I would love to swap out my servers for Atom hardware and even my desktop (I'm not doing anything intensive).  My problem, though, is two-fold.[LIST=1]
[*]Cost of buying new Atom hardware
[*]Being able to let go of "it's still usable..." hardware :lolflag:
[/LIST]

---

### Post by notuo on 2011-11-02
Thank you all for your answers.

I have now a lot to research and investigate.

Best regards to all.

---

### Post by lykwydchykyn on 2011-11-02
Debian Stable has never let me down on old equipment like that.

I'd go with lighttpd for the web server, especially if you're working with some heavy CMS or big php scripts.

---

### Post by snowpine on 2011-11-02
I hear that Dragonbite (funds are tight here too). I think I paid around $100 for my barebones Atom at Newegg, plus a little extra for RAM and hard drive, total price well under $200. Not a ton of money but then every dollar counts these days.

There is a big difference however between keeping a trusty old PIII install running  (as in your situation) vs. starting a new project (as in the OP's situation). I would not personally choose the PIII *as the platform for starting a new project* unless I had absolutely no choice. 

For example if it hypothetically costs 10 extra hours of my time to refurbish the old PIII, then $200 for new, reliable, efficient Atom hardware is a no-brainer.

---

### Post by notuo on 2011-11-02
What is this Atom hardware?. 

I don't live in US, so I never heard of it.

Thanks

---

### Post by snowpine on 2011-11-02
> **notuo said:**
> What is this Atom hardware?. 

I don't live in US, so I never heard of it.

Thanks

It is a low-power-consumption Intel processor used in netbooks (like the ASUS EEE), nettops, servers, etc.

[http://en.wikipedia.org/wiki/Intel_Atom](http://en.wikipedia.org/wiki/Intel_Atom)

(edit) And I apologize for taking the thread slightly off-topic. Ubuntu Server should work fine on your Pentium 3, there is no need to buy new hardware if you are satisfied with the old.:)

---

### Post by mörgæs on 2011-11-02
If you are new to Linux, begin with a full installation of Lubuntu. It runs well on your hardware. 

When that works and you are familiar with it, you can install the LAMP server with one command. 

I am sad to see that Damn Small Linux is still being recommended. This is doubtful advice, especially to a beginner, since the project has been abandoned for several years.

---

