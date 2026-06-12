---
title: "Windows 7 RAM Problem"
date: 2009-12-22
forum: General Help
---

### Post by mojarlets on 2009-12-22
Hey, I'm running Windows 7 Professional 64-Bit and I have 6GB of Kingston HyperX RAM on my motherboard which is a ASUS P6T SE which can have 24GB of RAM, but Windows 7 is only saying there is 4GB of RAM, but when I run CPUZ is says I have 6GB. Anyone know what might be wrong?

---

### Post by AlexDBall on 2009-12-22
Well, i think this post should be more appropriate in a Windows forum. :)

Unless you install Ubuntu;)

---

### Post by StuartN on 2009-12-22
> **mojarlets said:**
> Hey, I'm running Windows 7 Professional 64-Bit and I have 6GB of Kingston HyperX RAM on my motherboard which is a ASUS P6T SE which can have 24GB of RAM, but Windows 7 is only saying there is 4GB of RAM, but when I run CPUZ is says I have 6GB. Anyone know what might be wrong?

If you either install the Server edition of Ubuntu, or install the server kernel to an existing Ubuntu system, then you will have full access to all of your memory.

I think that the 64-bit Desktop edition is also fully PAE aware and accesses all installed memory.

---

### Post by 3rdalbum on 2009-12-22
> **mojarlets said:**
> Hey, I'm running Windows 7 Professional 64-Bit and I have 6GB of Kingston HyperX RAM on my motherboard which is a ASUS P6T SE which can have 24GB of RAM, but Windows 7 is only saying there is 4GB of RAM, but when I run CPUZ is says I have 6GB. Anyone know what might be wrong?

Try running the 64-bit Ubuntu disc, and see how much memory is reported in the System Monitor program.

If it reports all 6 GiB or close to it, then you've got a Windows problem. If it reports 4 GiB, then try checking your BIOS for any settings related to address space, and try updating your BIOS.

---

### Post by 3rdalbum on 2009-12-22
> **StuartN said:**
> If you either install the Server edition of Ubuntu, or install the server kernel to an existing Ubuntu system, then you will have full access to all of your memory.

I think that the 64-bit Desktop edition is also fully PAE aware and accesses all installed memory.

Maybe I'm just being finiky with language, but 64-bit Ubuntu doesn't need PAE. The address space is already a couple of terrabytes, you don't need a "Physical Address Extension" on top of that!

In short, PAE allows a 32-bit processor and OS to access more RAM than its normal address space. 64-bit addressing already addresses more RAM than even PAE.

---

### Post by scouser73 on 2009-12-22
> **mojarlets said:**
> Hey, I'm running Windows 7 Professional 64-Bit and I have 6GB of Kingston HyperX RAM on my motherboard which is a ASUS P6T SE which can have 24GB of RAM, but Windows 7 is only saying there is 4GB of RAM, but when I run CPUZ is says I have 6GB. Anyone know what might be wrong?

Try the [[COLOR="Red"]**Windows 7 Forum**[/COLOR]]("http://www.sevenforums.com/")

---

