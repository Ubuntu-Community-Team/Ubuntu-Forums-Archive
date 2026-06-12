---
title: "How do i run 64bit ubuntu?  I have a core2quad q8200"
date: 2010-02-20
forum: General Help
---

### Post by Waveridr85 on 2010-02-20
uname -m shows i686

From what I understand this means I am running in 32 bit.  Is there a simple way to switch my machine to run 64 bit?  Are there any disadvantages or advantages?

---

### Post by howefield on 2010-02-20
Depends on your definition of simple :)

Only way is a clean install with a 64 bit cd.

As to benefit, depends on what you are doing with your computer.

Intensive tasks like video encoding are likely to perform much better.

If you are planning to move to the next release, might be worth trying it then.

Lucid Lynx is released 29th April.

---

### Post by Waveridr85 on 2010-02-20
> **howefield said:**
> Depends on your definition of simple :)

Only way is a clean install with a 64 bit cd.

As to benefit, depends on what you are doing with your computer.

Intensive tasks like video encoding are likely to perform much better.

If you are planning to move to the next release, might be worth trying it then.

Lucid Lynx is released 29th April.

I think that may be a good idea.  It is just a few months away.  I am very new to ubuntu and linux.   When i install the new release.  Do all the settings , files and such stay in place?

---

### Post by howefield on 2010-02-20
> **Waveridr85 said:**
> I think that may be a good idea.  It is just a few months away.  I am very new to ubuntu and linux.   When i install the new release.  Do all the settings , files and such stay in place?

All your settings will be found in /home.

Should you wish to keep them, you can back them up and copy them over.

If you are doing a clean install with 64 bit, might also be worth looking at creating a separate partition for your /home as this will make future upgrades / installs a bit easier.

---

### Post by mk1w86 on 2010-02-20
> Are there any disadvantages or advantages?

One of the main reasons to use 64BIT is if you have 4GB or more of RAM. ;)

---

### Post by GSF1200S on 2010-02-20
There used to be quite a few disadvantages, specifically java and flash plugins. Occasionally, you'll find a package that isnt ported to 64bit yet, but this is increasingly rare. 

Now, the flash released by Adobe for linux 64 bit is still an alpha, but it is FANTASTIC. I cannot think of a single flash crash Ive had with this plugin.Ive had no issues with Java lately either.

For me, its nice to be able to use my 6GB of RAM ;). Admittedly, there is supposedly a way to use more than 3.6 GB of RAM with 32bit, but its more involved and not as fast as just using 64bit. 64bit Ubuntu is just as easy as 32bit nowadays..

---

### Post by Muscovy on 2010-02-20
64 bit will give some (I don't know how much) boosts in speed. The only downside is it uses more RAM. Just idling with nothing notable open increased RAM usage from ~300 to ~500 MB, but pretty much any computer with a 64bit capable processor has plenty of RAM.

---

### Post by mk1w86 on 2010-02-20
> Admittedly, there is supposedly a way to use more than 3.6 GB of RAM with 32bit, but its more involved and not as fast as just using 64bit. 64bit Ubuntu is just as easy as 32bit nowadays..

Yes, using PAE, but as you say you are better off running 64BIT because PAE can have an impact on system performance.

---

### Post by Waveridr85 on 2010-02-21
Yes,  I defiantly think I will go to 64bit since I do have 4gb of ram.  I had no idea it would only register 3.6.  Thanks again for the info.

---

