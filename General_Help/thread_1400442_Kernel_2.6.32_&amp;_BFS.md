---
title: "Kernel 2.6.32 &amp; BFS"
date: 2010-02-06
forum: General Help
---

### Post by Shibblet on 2010-02-06
Is there a DEB of the 2.6.32 Kernel with the BFS Scheduler built in?  I'd like to give it a run, but I'm not so sure about compiling it on my own.

---

### Post by Shibblet on 2010-02-09
Nobody?  Bump.

---

### Post by NightwishFan on 2010-03-28
For Lucid use this PPA:
[https://launchpad.net/~chogydan/+archive/ppa](https://launchpad.net/~chogydan/+archive/ppa)

For Karmic use:
[https://launchpad.net/~darxus/+archive/bfsbfq](https://launchpad.net/~darxus/+archive/bfsbfq)

To add a PPA run:
```
sudo add-apt-repository **boldtextabovepackagelist**
```

Example:
```
sudo add-apt-repository ppa:darxus/bfsbfq
```

Make sure you reload the packages after you add a PPA. Use:
```
sudo aptitude update
```

Hold in shift before GRUB loads to choose which kernel to boot. You can use this reference to set a specific kernel as default:
[https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29](https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29)

Just edit the /etc/default/grub file and change the GRUB_DEFAULT="0" line to the line of the kernel you want subtracted by one. (It starts at 0)

Example:
ubuntu-generic
ubuntu-generic-recovery
ubuntu-ck

ubuntu-ck would be "2"

Finally run this command to update grub.
```
sudo update-grub
```

My tutorial writing it TERRIBLE so please ask any questions before you attempt what you might not get. If you get all of it, and didnt beforehand you are a smarter person than I am.

---

### Post by Shibblet on 2010-03-28
> **NightwishFan said:**
> For Karmic use:
[https://launchpad.net/~darxus/+archive/bfsbfq](https://launchpad.net/~darxus/+archive/bfsbfq)


I am running the 2.6.32.9 Mainline kernel right now, and I can see a 50-60% performance increase from the 2.6.31-20 Kernel.  This is with encoding on Handbrake.

So I checked out the link above, and it's the 2.6.31-14(BFS) kernel, and it is making a similar performance increase, just a tiny bit faster, so around 55-65% instead.

I notice these performance increases by comparing the average frames per second on the encode.  And I am "approximating" the increase.  But with the standard 31-20 kernel, my FPS is 25-30, with 32.9 kernel it's 40-45, with 31-14(BFS) its 45-50.

So, what I would really like to get is a 2.6.32 kernel with BFS.

---

### Post by NightwishFan on 2010-03-28
If you are into that sort of thing you can compile one yourself for Karmic.

My Lucid kernel running is:
```
Linux coffee-desktop 2.6.32-16ck-generic #26~ppa1-Ubuntu SMP Thu Mar 18 19:59:58 UTC 2010 x86_64 GNU/Linux
```

It is from a PPA for Ubuntu 10.04 Lucid here:
[https://launchpad.net/~chogydan/+archive/ppa](https://launchpad.net/~chogydan/+archive/ppa)

---

### Post by Shibblet on 2010-03-28
> **NightwishFan said:**
> If you are into that sort of thing you can compile one yourself for Karmic.

Yeah... the last time I tried to compile my own kernel, there was a crash factor.  I would imagine that someone would have done this already for Ubuntu.

> **NightwishFan said:**
> It is from a PPA for Ubuntu 10.04 Lucid here:
[https://launchpad.net/~chogydan/+archive/ppa](https://launchpad.net/~chogydan/+archive/ppa)

Unfortunately this PPA doesn't work in Karmic.

---

### Post by danbh on 2010-04-18
hey there, I've been using that ppa a bit on karmic.  I used up through 32-16 on karmic.  Later version required a package that was in lucid only, but the latest will now install on karmic.  Unfortunately, it is incompatible with the karmic nvidia drivers I am using, so I'm still stuck on the regular kernel.  For your purposes, it looks like you should be ok.

---

### Post by NightwishFan on 2010-04-18
This PPA is for Karmic.
[https://launchpad.net/~darxus/+archive/bfsbfq](https://launchpad.net/~darxus/+archive/bfsbfq)

DKMS should install Nvidia drivers as long as you have the kernel headers installed.

---

### Post by Milos_SD on 2010-04-18
Is there BFS patch for 2.6.34-rc4 kernel?

---

### Post by EddieRingle on 2010-05-18
> **Milos_SD said:**
> Is there BFS patch for 2.6.34-rc4 kernel?

Just in case you didn't find it, the patches are released here:
[http://ck.kolivas.org/patches/bfs/]("http://ck.kolivas.org/patches/bfs/")

---

