---
title: "Space Requirments?"
date: 2012-06-09
forum: General Help
---

### Post by Ubun2to on 2012-06-09
I want to experiment to see if I can install Ubuntu 12.04 on a flash drive (not as a live install-I mean a full OS that I can run from any computer, and not have any installer), and I want to know how much space a full install of Ubuntu requires (since I intend to do a complete install and have room for games, multimedia, documents, and applications). I want to see if I can install it on a flash drive since I could (in theory) boot to it on any computer I want.
TLDR; how much space does a full install Ubuntu 12.04 take up? I want to try to install it on a flash drive.

---

### Post by Paqman on 2012-06-09
You'll need at least an 8GB stick. You might just get it onto a 4GB one, but you'd run out of room quickly.

---

### Post by snowpine on 2012-06-09
5gb is the recommended minimum according to: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by Ubun2to on 2012-06-09
> **Paqman said:**
> You'll need at least an 8GB stick. You might just get it onto a 4GB one, but you'd run out of room quickly.

For a full installation?
I thought I saw 32 GB as the biggest size on Wubi.
> **snowpine said:**
> 5gb is the recommended minimum according to: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Note that I said a FULL install-not just system files and a GUI. I mean all the programs included by default.

---

### Post by drs305 on 2012-06-09
> **Ubun2to said:**
> Note that I said a FULL install-not just system files and a GUI. I mean all the programs included by default.

It should be less than 5GB with the default apps. On my desktop, a new installation of 12.10 is around 4GB with the default apps plus a few extras. Of course, you will have to add space for any data you plan on keeping in /home.

---

### Post by snowpine on 2012-06-09
> **Ubun2to said:**
> For a full installation?
I thought I saw 32 GB as the biggest size on Wubi.


Note that I said a FULL install-not just system files and a GUI. I mean all the programs included by default.

I understood the question, and the answer is 5gb. :)

---

### Post by Ubun2to on 2012-06-09
> **snowpine said:**
> I understood the question, and the answer is 5gb. :)

Then why does Wubi offer 32 GB? Is that a partition size? (Although that would be a poor partition size if you have a 1 TB drive like me.)

---

### Post by snowpine on 2012-06-09
> **Ubun2to said:**
> Then why does Wubi offer 32 GB? Is that a partition size? (Although that would be a poor partition size if you have a 1 TB drive like me.)

I don't think WUBI is the right tool for your project; I recommend using the regular Ubuntu installer (ubiquity).

Make sure you install GRUB  to the correct drive. If you don't know what that means, then I recommend you disconnect your internal hard drive to avoid human error.

---

### Post by Ubun2to on 2012-06-09
> **snowpine said:**
> I don't think WUBI is the right tool for your project; I recommend using the regular Ubuntu installer (ubiquity).

I meant when I installed Ubuntu on my desktop through Windows.

---

### Post by snowpine on 2012-06-09
> **Ubun2to said:**
> I meant when I installed Ubuntu on my desktop through Windows.

You don't believe the official Ubuntu documentation or Ubuntu Forums staff that the correct answer is approximately 5gb?

---

### Post by Ubun2to on 2012-06-09
> **snowpine said:**
> You don't believe the official Ubuntu documentation or Ubuntu Forums staff that the correct answer is approximately 5gb?

I was just trying to understand why Wubi told me 32 GB, and it actually takes up 5 GB according to you and the documentation.
I'm a math nerd, so when something like this comes up, it really confuses me and my brain never wants to stop asking why until a reasonable explanation is found.
But, if it's 5 GB, so be it. That means I don't have to get a very large flash drive after all.

---

### Post by snowpine on 2012-06-09
I've never used WUBI before in my life, but I imagine the reason for 32gb is so you have room to install additional applications and store documents, music, video? Personally I have 500gb because I am a musician with lots of audio files.

---

### Post by Ubun2to on 2012-06-09
> **snowpine said:**
> I've never used WUBI before in my life, but I imagine the reason for 32gb is so you have room to install additional applications and store documents, music, video? Personally I have 500gb because I am a musician with lots of audio files.

That would make sense.
Well, I ordered the USB drive I need (currently I only have 4 GB, which is way to small), so hopefully I'll be able to post the results of this experiment soon!

---

### Post by 1clue on 2012-06-09
It's amazing what you get with 5G.

On the other hand, all the crap you store in your home folder can take up several times that.

Personally I'm not sure I'd want a serious distro on a USB stick.  I understand your scenario, but not whether you intend to use this heavily or not.

For one thing, USB tends to be pretty slow unless you have some pretty spiffy hardware.  For another, the possibility that you start a long file operation, go for coffee and then somebody (maybe a 5-year-old) yanks your stick out makes me shudder.

---

### Post by Ubun2to on 2012-06-10
> **1clue said:**
> It's amazing what you get with 5G.

On the other hand, all the crap you store in your home folder can take up several times that.

Personally I'm not sure I'd want a serious distro on a USB stick.  I understand your scenario, but not whether you intend to use this heavily or not.

For one thing, USB tends to be pretty slow unless you have some pretty spiffy hardware.  For another, the possibility that you start a long file operation, go for coffee and then somebody (maybe a 5-year-old) yanks your stick out makes me shudder.

I am glad for Ubuntu One-it really made me aware of the amount of stuff I can download (only 5 GB and I don't have the steady money flow required to pay for more space).
I really just want to try this for testing purposes. When USB 3.0 becomes mainstream and prices drop, I will take full advantage of it. I won't use this for graphic and resource intensive applications-I do the heavy stuff on my desktop (which I hope to upgrade to 16 GB of RAM soon, as I just got a new video card for it).
I personally think leaving a computer alone for a long period of testing is preposterous. I always backup my stuff, so I don't really worry about someone yanking the USB drive out.

---

### Post by Paqman on 2012-06-10
> **Ubun2to said:**
> I always backup my stuff

Good idea. USB sticks use flash memory, and that has a finite number of writes per sector (around 10,000). That's not a problem if you're just using them for storage (very occasional writes) but it is a problem running software. An OS will be doing a lot of writes to certain files. This means you're likely to start wearing out the stick quite quickly. Anecdotally people on here have said that they've been able to use USB sticks continuously for several months without any trouble, but it is something to be aware of.

---

