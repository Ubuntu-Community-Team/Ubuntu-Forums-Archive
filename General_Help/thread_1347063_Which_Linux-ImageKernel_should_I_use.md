---
title: "Which Linux-Image/Kernel should I use?"
date: 2009-12-05
forum: General Help
---

### Post by MechWarrior001 on 2009-12-05
I'm trying to help a friend setup Ubuntu on his laptop, and I was wondering which kernel/image I should use to take full advantage of his 64-bit AMD Duron CPU. I saw a couple images on the repository with a label similar to "...x86/x86-64" but I wasn't sure.

---

### Post by MartyBuntu on 2009-12-05
> **MechWarrior001 said:**
> ...his 64-bit AMD Duron CPU.

There's 64 bit Duron?

Hmmm...I'm not sure about that...

---

### Post by Leppie on 2009-12-05
On the [Ubuntu download page]("http://www.ubuntu.com/getubuntu/download"), the last part of section 1 (download ubuntu cd image) is "Alternative download options, including Ubuntu installer for Windows". If you click on the writing, new options appear. Choose the ones to your liking (like the 64 bit version), and click the big green download button.

Otherwise, there's different images available through releases.ubuntu.org. Depending on your needs, there's server versions, desktop versions, netbook versions, or specific other needs. I suppose the 64 bit desktop cd would be the best choice for your friend's laptop (if it is a x64 machine).

---

### Post by Leppie on 2009-12-05
Maybe it's a Turion?

---

### Post by MechWarrior001 on 2009-12-05
As of the moment, we don't have a means to download and burn a 64-bit installer CD, so which packages should we get from the repository to upgrade to 64-bit?

---

### Post by IllegalCharacter on 2009-12-05
There's nothing in your current repositories to upgrade to 64-bit versions, since the 64-bit Ubuntu uses a different repository than the 32-bit one.

It would be a huge pain to upgrade your packages to the 64-bit versions, it would probably be very time consuming as I doubt a lot of them will work very well together. The easiest option is to somehow get a copy of the 64-bit install CD and install that. If you don't have access to that, it would probably take less time to go to a nearby cyber cafe, download the 64-bit ISO, burn it there, and bring it back.

Finally, why do you want to go to 64-bit? There is not a huge speed boost, and a lot of the time there are compatibility issues with third-party software like Flash or Java plugins.

Anyway if you're still dead-set on grabbing the 64-bit version, just go here to download the 64-bit version of the kernel: [http://packages.ubuntu.com/karmic-updates/linux-image-2.6.31-15-generic](http://packages.ubuntu.com/karmic-updates/linux-image-2.6.31-15-generic). But don't say I didn't warn you!

---

### Post by MechWarrior001 on 2009-12-10
Alright, thanks. Also, we have a older laptop running a Intel Mobile Pentium 2. Which Kernel Should we use for that?

---

### Post by IllegalCharacter on 2009-12-10
The 32-bit one would be your best bet, since Pentium 2 is not a 64-bit processor ;)

I doubt Ubuntu would run very well on a Pentium 2 anyway, you should probably look into Xubuntu or even a different distro designed to work on older machines.

---

### Post by MechWarrior001 on 2009-12-10
I know, i just thought despite not being 64bit, why start a new thread about kernels if there already is one?

And we will probably end up loading Xfce onto the system; I was just wondering if there are specific kernels/images that run better on Pentium 2s than the generic default ones.

---

