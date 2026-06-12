---
title: "i868 processor - Ubuntu Version"
date: 2011-02-02
forum: General Help
---

### Post by phosphide on 2011-02-02
Hi All,
I am looking to install xubuntu on a very old desktop of mine with a i686 processor. However, the recent versions only work for x86 processors. How can I get earlier versions of linux that will run? Or is it even possible? Anything would be appreciated. I would like to run xubuntu but any version is fine honestly.

Edit: Reporting new problem. See 4 posts down.

---

### Post by Sazhen86 on 2011-02-02
I am going to assume that you meant to type i686 rather than i868 as that isn't a CPU model.  You should be able to get a version of Xubuntu to work on that, but be sure that you download the 32 bit version.  How much memory do you have?  Xubuntu requires 192MB but prefers 256MB or more.

---

### Post by phosphide on 2011-02-02
> **Sazhen86 said:**
> I am going to assume that you meant to type i686 rather than i868 as that isn't a CPU model.  You should be able to get a version of Xubuntu to work on that, but be sure that you download the 32 bit version.  How much memory do you have?  Xubuntu requires 192MB but prefers 256MB or more.
Yes, that was a typo I meant the i686. To be honest, I don't know how much memory this PC has because I haven't checked yet. It has been a while but I'm positive it has at least 256mb or more.
Let me try out the 32 bit download. I will post back with results.

---

### Post by 1clue on 2011-02-02
Never heard of that processor, but on the off chance you didn't make a typographical error then most Linux distributions support all or most architectures that the kernel works on.  Check out [http://www.kernel.org/doc/#Hardware](http://www.kernel.org/doc/#Hardware) to see what's there to see if it matches what you have.

Debian is the closest relative to Ubuntu.  It supports all or most architectures that Linux does.

---

### Post by phosphide on 2011-02-03
Well shoot. I got past that problem but now I am running into another one.

I get this error when I try to install.

```
Kernel Panic - Out of Memory and No Killable Processes
```

Should I do a memtest to figure out the problem?

---

### Post by Sazhen86 on 2011-02-03
Hi

You could try memtest, but I suspect it's due to there not being enough RAM.  Does the BIOS or the memory check during the POST tell you how much it has?

Cheers

---

### Post by matt_symes on 2011-02-03
Hi

Try something smaller like DSL or slax. You don't have enough memory to run all the required processes for xububtu.

[http://www.slax.org/](http://www.slax.org/)
[http://www.damnsmalllinux.org/download.html](http://www.damnsmalllinux.org/download.html)

Or you could try to find more memory.

There is also lubuntu if you want...

[http://lubuntu.net/](http://lubuntu.net/)

Kind regards

---

### Post by Primefalcon on 2011-02-03
if you cant run or have issues with xubuntu try lxde..... Get the alternate ubuntu disk (32bit) and ianstall the cli only version, after that ```
sudo apt-get install lubuntu-desktop
```

lxde which is lubuntu is a very very light desktop, even lighter than xfce (xubuntu)

---

