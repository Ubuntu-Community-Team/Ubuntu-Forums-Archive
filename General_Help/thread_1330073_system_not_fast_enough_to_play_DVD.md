---
title: "system not fast enough to play DVD?"
date: 2009-11-18
forum: General Help
---

### Post by pearldrums on 2009-11-18
Hi. I know a few things about computers, but I don't know a lot. I know what a processor does, but i don't know how good of one you might need to get things done. I'm trying to play a DVD on my MSI Wind netbook. It has the 1.6 ghz dual-core atom processor in it, 1 gig of ram, and a HDD hard drive. I do not run the netbook remix, but at rest the computer doesn't use too much of the processing power. When I try to play a DVD ISO file in movie player the system simply cant handle it. I find myself thinking... really?! I know the thing is limited, but couldn't you play DVD's on computers years ago when a 1.6 ghz processor might not have been so out of line.

mostly i'm just wondering if I should accept that it isn't going to happen, or if I should try to modify my physical system, or modify my OS, or what?

thanks.

---

### Post by anaconda on 2009-11-18
I think DVD-playback requires about 500MHz processor, so even an atom processor should be enough.

But why do you even want to play a DVD iso in a machine that doesn't have a DVD-drive (unless you have an external one).

HOw about channging the movieformat to something lighter with eg. acidrip? (eg. xvid.or ogg would be fine)

---

### Post by dcstar on 2009-11-18
> **pearldrums said:**
> Hi. I know a few things about computers, but I don't know a lot. I know what a processor does, but i don't know how good of one you might need to get things done. I'm trying to play a DVD on my MSI Wind netbook. It has the 1.6 ghz dual-core atom processor in it, 1 gig of ram, and a HDD hard drive. I do not run the netbook remix, but at rest the computer doesn't use too much of the processing power. When I try to play a DVD ISO file in movie player the system simply cant handle it. I find myself thinking... really?! I know the thing is limited, but couldn't you play DVD's on computers years ago when a 1.6 ghz processor might not have been so out of line.

mostly i'm just wondering if I should accept that it isn't going to happen, or if I should try to modify my physical system, or modify my OS, or what?


If you do not have 3D video drivers installed, then you may struggle to keep up with the frame rate.

---

### Post by 3rdalbum on 2009-11-18
> **dcstar said:**
> If you do not have 3D video drivers installed, then you may struggle to keep up with the frame rate.

The vast majority of Atom netbooks have Intel 3D. The video driver is preinstalled on Ubuntu.

Make sure you're using Ubuntu 9.10 rather than 9.04; the driver on 9.04 has some performance problems. Also, try turning off Compiz (visual effects) while playing DVDs.

---

### Post by P4man on 2009-11-18
Id try VLC to play back those rips, though I suspect the problem might be in the rip rather than anywhere else, assuming video acceleration is working properly.

BTW, while your machine should be fast enough to play back DVDs, make no mistake about how slow Atom cpu's are. Dont be fooled by the clockspeed. 1.6 GHz sounds pretty fast but for many tasks an AthlonX2 or Core2 cpu could well be faster running at just 600 MHz
[http://www.anandtech.com/systems/showdoc.aspx?i=3321&p=7](http://www.anandtech.com/systems/showdoc.aspx?i=3321&p=7)

Atoms are also incapable of playing back HD content without a decent GPU acceleration. But again, regular DVD ought to be possible without problems, so this is all slightly OT.

---

### Post by pearldrums on 2009-11-18
> **anaconda said:**
> 
But why do you even want to play a DVD iso in a machine that doesn't have a DVD-drive (unless you have an external one).

HOw about channging the movieformat to something lighter with eg. acidrip? (eg. xvid.or ogg would be fine)

Well my concept is that even though the machine doesn't have a cd/dvd drive it virtually has whatever I would like it to. I'm watching rented or borrowed TV shows in remote locations so its pretty easy to rip them on my main computer and transfer them over the network when I'm not busy, then watch them in my down time on campus. (if your concerned about the morality of this I don't think its illegal if I'm in possession of the original disk and don't keep a copy, which I don't have space to keep tons of ISOs around). I've never really ripped movies down to another format, but I would assume there would be a little bit of video editing if I didn't want to have to search for the beginning of my show each time, so I figured it was just easier to use the ISO as a virtual disk.

> **3rdalbum said:**
> Make sure you're using Ubuntu 9.10 rather than 9.04; the driver on 9.04 has some performance problems. Also, try turning off Compiz (visual effects) while playing DVDs.

I do have 9.10 installed. I tried turning compiz off by going into appearance and clicking none. Is that effective or do I have to actually diable it somewhere? It didn't help, but I will remember that if I'm doing anything intense to shut it down.

> **P4man said:**
> Id try VLC to play back those rips, though I suspect the problem might be in the rip rather than anywhere else, assuming video acceleration is working properly.

BTW, while your machine should be fast enough to play back DVDs, make no mistake about how slow Atom cpu's are. Dont be fooled by the clockspeed. 1.6 GHz sounds pretty fast but for many tasks an AthlonX2 or Core2 cpu could well be faster running at just 600 MHz
[http://www.anandtech.com/systems/showdoc.aspx?i=3321&p=7](http://www.anandtech.com/systems/showdoc.aspx?i=3321&p=7)

Atoms are also incapable of playing back HD content without a decent GPU acceleration. But again, regular DVD ought to be possible without problems, so this is all slightly OT.

Hey thanks for that! VLC is working just great now. What exactly does that say about the ISO? Also, I hope you guys have gathered that I know enough to assemble a machine, and such that most people seem to think I'm a genius, but in reality I know just enough to realize how much I have to learn. It was interesting to look at the performance charts for the different processors.

---

