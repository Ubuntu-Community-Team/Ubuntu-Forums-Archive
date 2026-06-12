---
title: "Jittery effect in Ubuntu 10.4"
date: 2010-07-15
forum: General Help
---

### Post by RAHB on 2010-07-15
Hello. Well, after a few year break from Ubuntu, I decided to install the latest version 10.04 the other day, which I must say has impressed me to no end. It immediately supported all of my hardware, save for my graphics card, which I was able to get a restricted driver for in about one minute. I've got all of my required programs running, and I've even managed to get some windows-only ones going in Wine, and overall everything is just fantastic.

Except for one problem. It's hard to describe it. Basically, every minute or two (sometimes the space of time is longer or shorter), I get this "jittery" effect across the whole system. By this I mean, the graphics and mouse stutter, and so does any audio I happen to be listening to, whether through Audacious, Rhythmbox, VLC, or Skype. If I'm switching between windows, the switch is stuttery, the minimizations and maximizations hesitate, etc. This doesn't constantly happen, it goes on and off, and varies in degree of how badly it is every time. 

I've tested it with and without extra effects in Appearance, and shutting them off doesn't seem to affect it. My computer seems to be properly supporting most of the stock compiz effects very competently anyways. 

I'm running an AMD Sempron 3000+ 1.8 GHz Single Core processor, with one GB of ram, Ubuntu running on my 40 GB master drive, and an NTFS slave drive with my data on it, which mounts, unmounts and interacts with Ubuntu just fine. 

Any help would be much appreciated. This isn't an enormous issue as much as an annoyance, and I still don't plan on going back to Windows, but I do frequently work with audio, and so I'm going to need to fix it eventually. Thanks in advance!

---

### Post by ubunterooster on 2010-07-15
It does sound like a CPU load; what is your CPU and RAM loads when this happens?

---

### Post by Jazzy_Jeff on 2010-07-15
Open a terminal and type in top. Keep the terminal open and watch it and see if anything jumps to the top of the list when this happens.

---

### Post by RAHB on 2010-07-15
Going by System Monitor, my RAM usage is staying at a consistent 44.4%. My CPU right now is running at average around 50% (Skype, Firefox, and Xchat running). When it's jittering I see it go up anywhere to 80%. Last night my tower was running very hot, and the CPU at one point was consistently loaded between 85 and 100%, with no programs running, but I've moved it to a cooler location today and I haven't seen it go up that high since. But right now, yes it's spiking up when these jitters happen.

---

### Post by RAHB on 2010-07-15
> **Jazzy_Jeff said:**
> Open a terminal and type in top. Keep the terminal open and watch it and see if anything jumps to the top of the list when this happens.

Ran it, and Xorg and a process called phy0 went to the top, both at about 30%, when I got the jitters. Not sure whether this is indicative of anything in particular.

Edit: Rather, it looks like just phy0 is the one shooting to the top (since Xorg is already one of the top processes to begin with). This process evidently has to do with some sort of internet port, so if it helps, the information on my internet is that I'm currently running a wired ethernet connection. Last night I was going off my wireless card, but I was getting very slow response out of anything internet related, so today I went and got an ethernet cable and the problem there was fixed, though the card is known to be finicky anyways. I still have the card plugged in, and disabled. No idea whether that is relevant or not.

---

### Post by RAHB on 2010-07-15
Okay, I conferred with a fellow Ubuntu user who told me that phy0 was a wireless process. On a hunch I decided to remove the card from my computer. Everything seems to have been fixed now. No jitters, no skipping audio. I do believe this has solved the problem. For anybody who references this in the future, I was using a Belkin F5D7000 Wireless G Desktop Card, which was supported by Ubuntu out of the box. It could simply be that my individual card was causing the issues, since as I said, it has a history of being a horrible piece of trash. Thanks for the help, guys!

---

### Post by Neobuntu on 2010-07-16
It's Java! Eat 92% of my CPU; according to TOP.

---

