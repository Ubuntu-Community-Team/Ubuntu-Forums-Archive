---
title: "I'm using 64-bit, but not getting 4GB"
date: 2010-04-29
forum: General Help
---

### Post by Finalfantasykid on 2010-04-29
I had been previously using 32 bit versions of Ubuntu, but now I did a clean install using the 64-bit OS.  But I don't seem to be getting the 4GB that my system has (XPS M1710).

[http://img98.imageshack.us/i/screenshotxj.png/](http://img98.imageshack.us/i/screenshotxj.png/)

As you can see I only have 3.2 GB of accessible memory, which is the exact same as what I used to get using 32-bit.  As far as I can tell from the uname -a output, I am infact using the 64-bit version, so what is up...?

---

### Post by kelvin spratt on 2010-04-29
I've got my full amount of ram with 64bt

---

### Post by arrrghhh on 2010-04-29
> **Finalfantasykid said:**
> I had been previously using 32 bit versions of Ubuntu, but now I did a clean install using the 64-bit OS.  But I don't seem to be getting the 4GB that my system has (XPS M1710).

[http://img98.imageshack.us/i/screenshotxj.png/](http://img98.imageshack.us/i/screenshotxj.png/)

As you can see I only have 3.2 GB of accessible memory, which is the exact same as what I used to get using 32-bit.  As far as I can tell from the uname -a output, I am infact using the 64-bit version, so what is up...?

Is your video card stealing some memory perhaps?  A lot of (cheaper) laptops don't have dedicated video memory.

Besides, 32-bit chops it off just past 3.5GB, so it makes no sense why 3.2 would be available.

---

### Post by Finalfantasykid on 2010-04-29
I have an Nvidia card with 256MB dedicated memory, so the main memory is not sharing any.

---

### Post by arrrghhh on 2010-04-29
> **Finalfantasykid said:**
> I have an Nvidia card with 256MB dedicated memory, so the main memory is not sharing any.

Hrm... Well I'm not sure then.  Have you confirmed your RAM in another OS, or why do you feel the system is robbing you of RAM?  :P

---

### Post by howefield on 2010-04-29
Perhaps your chipset doesn't support the full 4 gig.

---

### Post by Finalfantasykid on 2010-04-29
> **howefield said:**
> Perhaps your chipset doesn't support the full 4 gig.

I'm starting to think that, but when I go into the BIOS I'm pretty sure it says 4GB.  Even if it says that, would the OS still not have access to all that memory?

---

### Post by VinisLentoje on 2010-04-29
*please delete. thank You*

---

### Post by howefield on 2010-04-29
> **Finalfantasykid said:**
> but when I go into the BIOS I'm pretty sure it says 4GB.  Even if it says that, would the OS still not have access to all that memory?

Correct, it's entirely possible.

I've seen posts in the Dell forum about this model, but would research further before accepting it is the case,.

---

### Post by Finalfantasykid on 2010-04-29
I went to check my BIOS again, and you are correct.

It reported that I have 4GB installed, but due to a certain amount allocated for 'system resources' I can only access about 3.2 GB.  :(  What a shame...

---

