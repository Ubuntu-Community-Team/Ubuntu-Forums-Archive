---
title: "32 bits Vs 64 bits"
date: 2009-12-30
forum: General Help
---

### Post by henry83 on 2009-12-30
Hi folks! I'm about to buy a new laptop, the first thing I'll do when it is on my hands is to install Ubuntu over windows 7, of course. I want to know If this would be a good chance to install the Ubuntu 64 bit version, I have always used the 32 bit version and so far so good, but what about going up? what would you suggest? What are the main advantages and disadvantages of the 64 bit version? Please let me know every peace of advise will be great! Thanks in advance.

---

### Post by oldos2er on 2009-12-30
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

---

### Post by benfindlay on 2009-12-30
That decision very much depends upon what you use your operating system for.

Once of the main sticking points I have seen is the lack of 64bit packages available for specific software, an issue which (theoretically) gets less of an headache each day. What this means is that if there is a particular program you want to install and run that isn't available in 64 bit you need to install the 32 bit version, which isn't harder to do per se; I'd say its a little more hassle, but only slightly.

Another common sticking point I have come across is wireless and video drivers. They are more problematic again, and they have been known to be not as simple as a few extra steps to get them installed and working.

There's a good thread detailing this all [here]("http://ubuntuforums.org/showthread.php?t=368607").

At the end of the day the best advice I can give you is to check the compatibility and hardware support for whatever make of laptop you choose to buy, and base your decision upon how much of a battle you will have on your hands to get it all working. Alternatively, hunt through the forums for any confirmed 64 bit friendly laptops and make your choice accordingly.

Hope this helps!

---

### Post by henry83 on 2009-12-30
Thank you, I really don't want to be fussing and fighting all the time so, your advices come really handy for my final decision, I expect to receive more posts to end up with this matter! But so far the 32 bits version is my choice...

---

### Post by oldos2er on 2009-12-30
I've been using 64-bit Ubuntu for more than two years. If your hardware is 64-bit capable why choose 32?

---

### Post by Drew Barfield on 2009-12-30
Version 9.10 64-bit works great for me:

**See:** [http://launchpadlibrarian.net/37299838/drew-laptop.xml.bz2]("http://launchpadlibrarian.net/37299838/drew-laptop.xml.bz2")

I have Chrome 64-bit installed and even Limewire works.
As long as Chrome works I'm happy for the most part: I
use Docs, Reader, Gmail, etc.

**One small/odd problem:**

Graphics Card: Nvidia GeForce 8200M G
I'm using my laptop LCD (LGD LP156WH1-TLA3) and an
external LG L1920P

My video card squeals. It doesn't squeal when the hard drive
is running (odd I know). It also doesn't squeal if I change
the resolution of the external monitor to a really high
resolution (weird). I can't use the high resolutions though
because most of the desktop gets clipped. If I change it to a
really low resolution setting it still squeals but at a lower
pitch!

**Update:** Changing configuration from "TwinView" to
"Separate X Screen" seems to have solved the squealing
problem... ain't that weird?

---

### Post by jittopjose on 2009-12-30
I think some applications does not have a 64 bit version. I noticed some while downloading. If you are supposed to use software outside ubuntu repositories, there may be some issues. Thats why i stick with 32 bit even though my hardware support 64bit

---

### Post by michaelzap on 2009-12-30
If you will have 4GB or more of RAM, you should definitely install 64-bit.

It's much faster: [http://goo.gl/R4bN](http://goo.gl/R4bN)

The only issue I've had with 64-bit Ubuntu is the alpha version of Flash 10, so I just run the regular 32-bit version from the Ubuntu repos and it works fine. Oh and Google Gears is not available for 54-bit Linux yet. That's all.

---

### Post by crazyness003 on 2009-12-30
Yup, I was also gonna mention Flash support for 64bit is kinda on the backburner.
I've been using 64bit ever since I started using Linux, back in the Gutsy era. And with every release, support becomes less and less of a problem.

Really, the only REAL reason why you would want to choose 64 over 32 is if you have more than ~3.3 gigs of ram. If you don't have more than, that it's really a question of 'How adventurous are you?'. I currently run 3gb of RAM and the reason why I have 64bit is because I get 30-40% faster boot-up times (albeit it translates to only a couple of seconds :)).

---

### Post by Atzu on 2009-12-30
Well here in [this article]("http://www.omgubuntu.co.uk/2009/12/ubuntu-64bit-really-is-faster-than.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed:+d0od+(Omg!+Ubuntu!)&utm_content=Google+Feedfetcher") from omg! ubuntu! shows that Ubuntu 64bit is faster than 32bit so well i'd give a try and if it doesn't work or something i'd then go back to 32bits

Here there's [another article]("http://www.omgubuntu.co.uk/2009/12/new-adobe-flash-64bit-8th-december.html") talking about a new flash version that may give better support to flash 64bits and here's again [omg! ubuntu! with a PPA for flash 64bits]("http://www.omgubuntu.co.uk/2009/12/64bit-flash-ppa.html")

---

### Post by danastasio on 2009-12-30
I use 64 bit 9.10 and am quite happy with it. I feel that its a bit more responsive now that i'm using my processors full potential. 64 bit has its advantages over 32 bit and vice versa. It depends on what you want to use it for.

---

### Post by oldos2er on 2009-12-31
> **jittopjose said:**
> I think some applications does not have a 64 bit version. I noticed some while downloading. If you are supposed to use software outside ubuntu repositories, there may be some issues. Thats why i stick with 32 bit even though my hardware support 64bit

If you need to run 32-bit software under 64-bit Ubuntu, you can do so with ia32-libs.

---

