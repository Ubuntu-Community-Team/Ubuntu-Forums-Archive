---
title: "Need help connecting Moto L2 to (K)Ubuntu"
date: 2009-10-19
forum: General Help
---

### Post by D'raekmus on 2009-10-19
Hi, I'm a long time user of Ubuntu (I love Kubuntu, been using it since the release of 8.04, and have used every new distro ever since), but this is the first time I've posted in the forums.  I'm currently trying out the beta of Kubuntu Karmic, and I have a question regarding bitpim and moto4lin.

I currently have a Motorola L2 (SLVR I think), and I'm trying to connect it via Moto4lin.  I just want to transfer some simple files in between.

Moto4lin recognizes that it's there, and I can connect to it, sort of.  When it tries to update the listing of it, it errors out with "unable to connect"  I'll try reproducing the error, but it seems to not want to even try connecting.  I've tried the P2ktest, and it for whatever reason will not connect via P2k, it errors out, though it recognizes that the phone is P2k-capable.  

Kmobiletools says it cannot connect, and it locks up when I sudo it.

I have tried it as a sudoer, and as root.  same problem.  

I've seen where people have been able to connect their L2's to their computers, but they conveniently leave out HOW to connect it.  My question is, How do you get ubuntu to connect to it?

PS. I've custom-compiled Moto4lin from the source, so it's the most recent (relatively speaking)

and I'm sorry if this is the wrong forum to post this in.

---

### Post by P4man on 2009-10-19
I had never heard of moto4lin but it seems to have been abandoned judging by the fact the latest update is 3,5 years ago :s

At the very least Id check if you phone is on the list of supported phones. But you'll probably have more luck with another program. What is your phone?

---

### Post by D'raekmus on 2009-10-19
Thanks for your answer.

Anyway, my phone is a Motorola L2

[http://en.wikipedia.org/wiki/Motorola_l2](http://en.wikipedia.org/wiki/Motorola_l2)

I've already tried the supported models, and, well, it doesn't mention it specifically, but, since it's based off a SLVR, it might work as one.

I've also seen other posts (albeit older posts) where they managed to get it to work, but, conveniently left out how they did it.

I'd really like to not have to boot into Vista just to use phone tools for this phone.

---

### Post by P4man on 2009-10-19
Perhaps you can PM or email those who got it working?
Did you try any of the other tools in synaptic? [http://gnokii.org/](http://gnokii.org/) seems to support motorolla too to name just one.

---

### Post by D'raekmus on 2009-10-19
never mind, I found the problem.

For the reference, for you Motorola L2 users out there, I had to manually find my phone's path.

Mine was /dev/ttyUSB0

That should help some of you all out.

Now, I'm going to go use moto4lin to put pictures on my L2.

Note that for whatever reason, Moto4lin won't let root have settings, yet they can be altered by a normal user, which root then uses.  a permissions issue possibly?

---

