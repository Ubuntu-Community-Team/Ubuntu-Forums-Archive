---
title: "Low powered ubuntu torrent server"
date: 2009-09-15
forum: General Help
---

### Post by wardy277 on 2009-09-15
Hi,

I am looking into setting up a low powered ubuntu setup that i can use as a torrent and file server.

I was thinknig of egtting a cheap box and setting it up in my loft or soemthing that can be used to store all my movies, photoes etc.

I am quite familiar with ubuntu and the command line interface. What i was thinknig of is using ubuntu in a command line only setup.

I know  you can use deluge in command line. What i want is to boot up the very minimum (no gnome or any window manager). I want it to be a simple, low powered server that will download torrents and act as a shared point for streaming movies and tv shows.

What is the best way to start?
Should i install server or desktop?
Can Deluge's web interface work when started as command line?
Is there already another distro that is built for this?

Chris

---

### Post by Mighty_Joe on 2009-09-15
I built something along those lines.  Have a look at my posts in [this topic]("http://ubuntuforums.org/showthread.php?t=1244304&highlight=torrent") for the details.  I use transmission as my torrent client and it works fine via the command line or web browser.

---

### Post by Boondoklife on 2009-09-15
Well this is not really ubuntu but the WesterDigital MyBook World Editions can be hacked to allow shell access and from there you can do all kinds of goodies (install transmission and the web interface). I Personally use mine as a torrent server, media server, website testing bed, and file server.

[Hacking WD MyBook World Ed: Recent Forum Posts]("http://mybookworld.wikidot.com/forum:recent-posts") 

Again its not ubuntu, but if you are going only commandline then not a big deal.

---

### Post by wardy277 on 2009-09-15
Wow, those links look really inspiring. I think my main worry now is compatible hardware. I have never head of via's C3 processor. What is the compatibility for linux and small processors?

Its been a while since i have build a pc, and those were all high powered power hungry and quite hot. I dont really know where to start with looking for cool MB/CPU combos that require little power.

Since i am not going to be using a display, no X is needed. What sorft of spec CPU and RAM would i need to run a torrent and fileserver effitiently?

Chris

---

### Post by Mighty_Joe on 2009-09-15
> **wardy277 said:**
> I have never head of via's C3 processor. 


[Via processors]("http://en.wikipedia.org/wiki/VIA_C3") are x86.  As I posted on the other topic, my appliance is running Ubuntu Server 8.04 without any alterations.
There are other low-power X86 options, like Intel Atom and AMD Geode.  I chose the cheapest at the time :D

> **wardy277 said:**
> I dont really know where to start with looking for cool MB/CPU combos that require little power.

[Here]("http://blogs.zdnet.com/Ou/?p=275") is a general-interest article about building appliances.  [Here]("http://www.mini-box.com/site/index.html") and [here]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=446&name=Motherboard-CPU-VGA-Combo") are a couple of vendors.

> **wardy277 said:**
> What sorft of spec CPU and RAM would i need to run a torrent and fileserver effitiently?
That depends, of course.  I don't download or seed more than a couple torrents at a time.  I have Tomcat running, but just to display pictures of my kids.  I use SSH on that box to tunnel around the firewall at work. The CPU is 99% idle.  I have 512Mb RAM on that machine and right now, 370Mb are free.  So you don't need much CPU or memory at all (makes you appreciate how much power those window managers and gui applications need, eh?).

---

### Post by wardy277 on 2009-09-15
Thanx for your quick reply. I will look into those links and give it a go.

I cant believe how much the GUI takes up. I was looking at a few with 1-2 Gb RAM!! 

Chris

---

