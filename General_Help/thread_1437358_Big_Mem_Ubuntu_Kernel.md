---
title: "Big Mem Ubuntu Kernel?"
date: 2010-03-23
forum: General Help
---

### Post by beastrace91 on 2010-03-23
I want to run 32bit Ubuntu with 4gigs of RAM. Is there a precompiled "big mem" kernel lurking around in the Ubuntu repos under a different name that I can install to enable this? Coming back from Debian and it was a nice extra package they had.

Regards,
~Jeff

---

### Post by dcstar on 2010-03-23
> **beastrace91 said:**
> I want to run 32bit Ubuntu with 4gigs of RAM. Is there a precompiled "big mem" kernel lurking around in the Ubuntu repos under a different name that I can install to enable this? Coming back from Debian and it was a nice extra package they had.


The Server kernels have PAE enabled, otherwise all that happens is you miss out on ~400MB of RAM using the non-PAE kernels.

There's nothing wrong with the 64-bit versions of Ubuntu.

---

### Post by -kg- on 2010-03-24
> There's nothing wrong with the 64-bit versions of Ubuntu.

+1

I'm running 64-bit Karmic on both of the computers I run Ubuntu on, and it's pretty much undistinguishable from 32-bit.

If you just *must* run 32 bit Ubuntu for some reason, then you could install Server (with PAE) and then install the Gnome Desktop Environment (or whatever Desktop Environment you want) on top of it, I suppose.

---

### Post by beastrace91 on 2010-03-24
> **dcstar said:**
> The Server kernels have PAE enabled, otherwise all that happens is you miss out on ~400MB of RAM using the non-PAE kernels.

There's nothing wrong with the 64-bit versions of Ubuntu.

Any idea how I can install an autopackage 32bit installer on a 64bit system? I need my [SMART board](http://smarttech.com/) software to work on my system...

Regards,
~Jeff

---

### Post by zvacet on 2010-03-24
In synaptic search for linux-image-generic-pae and install it.

---

### Post by mcduck on 2010-03-24
Just install the **linux-generic-pae** package and that will bring you 32-bit PAE-enabled kernel. :)

---

### Post by beastrace91 on 2010-03-24
> **zvacet said:**
> In synaptic search for linux-image-generic-pae and install it.

Thanks! Thats what I needed.

~Jeff

---

### Post by slidersv on 2010-11-28
> **dcstar said:**
> There's nothing wrong with the 64-bit versions of Ubuntu.

I hate responses like that, especially when one is looking for answers.
It's not a question of something being wrong with the architecture, but with app support. Many business apps are horribly written and it's a huge pain having to do hacks for every third one. Just as big as having too little memory and having your SSD swap the heck out of it, slowing down your day.

---

### Post by beastrace91 on 2010-11-29
[img]http://i306.photobucket.com/albums/nn272/NaturalBornBoy/holy_thread_resurrection_batman.jpg[/img]

~Jeff

---

### Post by Yellow Pasque on 2010-11-29
> **slidersv said:**
> I hate responses like that, especially when one is looking for answers.
I don't like responses like yours, but I can just IGNORE them instead of necromancing a thread to add nothing to it..

---

### Post by bamajr on 2011-02-03
I know this thread basically died in March 2010, but I'm going to post anyway.

Many times, system hardware does not allow the 64-bit Ubuntu to be installed. For instance...

You can read [http://www.theforcefield.net/forums/index.php?topic=4407.0]("http://www.theforcefield.net/forums/index.php?topic=4407.0")

I have a series of servers with Tyan Tiger i7501R (S2735-8M) motherboards. These are dual CPU motherboards, they support up to 12GB of RAM (I have 6GB installed) and have built in 64-bit PCI slots.

However, the processor used on all these boards is the 32-bit Intel Xeon SL8TK.

A couple quick commands to check whether or not [the CPU is 64-bit Capable]("http://bamajr.com/2011/02/02/kubuntu-how-to-tell-if-the-cpu-is-64-bit-capable/"):

```
cat /proc/cpuinfo | grep flags
```

and...

```
sudo lshw
```

...verify that while there are four processor cores being identified from two physical processors, they are, in fact only 32-bit processors.

I have several of these machines and they were all running Debian GNU/Linux 5.0 with the BigMem kernel. All 6GB of RAM are able to be identified and used by the OS.

I'm running Kubuntu 10.10 on my production workstation, so I thought I'd try Ubuntu 10.04 LTS server out. I was shocked to find it does not have a BigMem kernel option.

Now, if Debian finds a BigMem kernel necessary, why doesn't Ubuntu, especially in their server variants?

---

