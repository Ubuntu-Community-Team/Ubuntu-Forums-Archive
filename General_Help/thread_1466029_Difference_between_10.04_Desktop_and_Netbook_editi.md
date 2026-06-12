---
title: "Difference between 10.04 Desktop and Netbook edition."
date: 2010-04-29
forum: General Help
---

### Post by Linuxperiment on 2010-04-29
I noticed that the Desktop edition is supported for 3 years, while the Netbook edition is supported for 1.5 years (18 months). Why are they supported differently? Also, are there any actual differences between these two other than appearances? I read somewhere that netbook edition is optimized even more for better boot and better battery life than desktop edition, but I don't know if this source was reliable.

Thanks for answering.

---

### Post by ibuclaw on 2010-04-29
Hi,

One question, where did you get that information from? (About the netbook edition being supported for only 1.5 years).

---

### Post by Mike_IronFist on 2010-04-30
> **Linuxperiment said:**
> I noticed that the Desktop edition is supported for 3 years, while the Netbook edition is supported for 1.5 years (18 months). Why are they supported differently? Also, are there any actual differences between these two other than appearances? I read somewhere that netbook edition is optimized even more for better boot and better battery life than desktop edition, but I don't know if this source was reliable.

Thanks for answering.

That doesn't seem accurate at all! The Netbook Edition is exactly the same as the desktop edition except for some key optimizations to make it run better on netbooks. (Different desktop interface, certain apps pre-installed for Netbook users' convenience.)

The Netbook Edition, if I'm not mistaken, is considered a subset of the Desktop release, so it should be supported for the exact same amount of time.

---

### Post by Linuxperiment on 2010-04-30
[http://it-chuiko.com/3538-ubuntu-1004-lts-3-years-of-support-an-online.html](http://it-chuiko.com/3538-ubuntu-1004-lts-3-years-of-support-an-online.html)

[http://www.techworld.com.au/article/344943/ubuntu_10_04_lucid_lynx_released_social_desktop_netbook](http://www.techworld.com.au/article/344943/ubuntu_10_04_lucid_lynx_released_social_desktop_netbook)

Also, there was a wikipedia article and finally, there's another source I can't seem to find that listed the information about how long UNE was going to be supported for. I know these aren't reliable resources, but basically, I'm wondering if UNE is much different now. Before, it was just a different user interface, but I'm not sure if they've changed the concept of UNE in 10.04.

---

### Post by Linuxperiment on 2010-04-30
Also, for some reason, it seems like UNE is more "supportive" towards netbooks now. Taken from the Ubuntu site itself:

[http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr)

---

### Post by ibuclaw on 2010-04-30
> **Linuxperiment said:**
> Also, for some reason, it seems like UNE is more "supportive" towards netbooks now. Taken from the Ubuntu site itself:

[http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr)

In a way, UNE is still just a different interface. It also excludes several packages that are present in the mainline distribution for practicality reasons (ie: there is no Compiz or Piviti by default on the UNE image).

And yes, UNE is geared towards Netbooks, (hence the word "Netbook" :)) - and not just the i386 architecture either, but armel is also supported (not sure if they have an lpia release, though would be interested to test if they do).

I think you are confusing UNE with [Ubuntu MID Edition]("http://www.ubuntu.com/products/mobile") mate.

Back to your original question though, take a look at these attached screenies, should give you a vague idea of what UNE looks like - although tbh if you have a spare USB stick lying around, you can test it yourself on any 32bit capable system - even your Desktop (though the resolution of the screen may throw the UI a bit off).


(note: xchat is not bundled with UNE by default, incase you get confused).

---

### Post by snowpine on 2010-04-30
With millions of netbooks on the market now, hardware support (such as for the Intel Atom chip) is built into the "upstream" Linux kernel. I think you will find that all current Linux distros are "optimized" for netbooks, performance-wise, and the main advantage of UNE is its unique "launcher" interface which some users prefer for smaller screens. 

(Personally I visually prefer the same interface as on my desktop and so I am not a UNE user; no performance issues with choosing "regular" Gnome in my experience.)

---

### Post by kiers on 2010-08-09
Hello
I am running the UNE (Lucid) 10.04 on my eee netbook pc. I am STOKED at how much better it is than XP! (i will have to remove the stoopid xp sticker on my netbook and place the ubuntu sticker)

 Question : when i ran this OS for the first few times a set of updates got set up (some 80MB i believe). Is it safe to get this ENTIRE packet of updates for the netbook edition? after all, i don't want the things that are NOT meant specifically for the netbook edition!
(ie. to stay "light"); OR is it the case that these entire updates are meant for UNE already?
any recommendations?

cheers.

---

### Post by snowpine on 2010-08-09
> **kiers said:**
>  Question : when i ran this OS for the first few times a set of updates got set up (some 80MB i believe). Is it safe to get this ENTIRE packet of updates for the netbook edition? after all, i don't want the things that are NOT meant specifically for the netbook edition!
(ie. to stay "light")

Yes, it is safe & recommended to install all available updates. :) 
Only applications that you personally have installed will be updated.

---

### Post by earthpigg on 2010-08-09
> **snowpine said:**
> Yes, it is safe & recommended to install all available updates. :) 
Only applications that you personally have installed will be updated.

that. if you want, however, you can safely choose to *only* accept security updates and not simple software improvements and bug fixes.

but then you will be at the current version of firefox forever, for example, and things that are broken/slow/buggy/not-quite-perfect today will always be broken for you.

---

### Post by kiers on 2010-08-12
thanks pigg and snowpine.  i am running on a monkey of a computer: the eee 900 pc from asus. it has 4gb primary flash drive,and 8gb secondary flash drive, so i have to watch what i eat. btw, that first update after new UNE install was 222mb (not 80 as i misquoted).

---

