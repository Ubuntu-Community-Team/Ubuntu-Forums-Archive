---
title: "somehow ended up with LTS"
date: 2010-06-13
forum: General Help
---

### Post by Bucky24 on 2010-06-13
Hi all,

Up until a month or so ago I had a copy of Ubuntu 9.10 installed on my desktop. This was the standard desktop version that I have had for two years and have been upgrading every time a new release came out. I upgraded to 10.4 a few weeks after it was released, but only today do I realize that somehow I managed to upgrade to 10.4 *LTS*. I did NOT want LTS.

How could this have happened, and is there any way I can revert back to normal 10.4 without having to reinstall?

-Bucky24

---

### Post by clhsharky on 2010-06-13
Bucky24

Ubuntu 10.04 and 10.04LTS release is one in the same.

Sharky

---

### Post by WorMzy on 2010-06-13
LTS stands for Long Term Support. I'm not sure why you think this is bad, or is something you don't want, but it shouldn't affect your experience.

---

### Post by MCVenom on 2010-06-13
Umm....
[IMG]http://img404.imageshack.us/img404/7227/lolwhuttranslated384267dn3.jpg[/IMG]

:P

---

### Post by tom.swartz07 on 2010-06-13
> **BlackOtaku said:**
> Umm....
[IMG]http://img404.imageshack.us/img404/7227/lolwhuttranslated384267dn3.jpg[/IMG]

:P

HAHAHAHAHAHHA! I love this.

to the OP: LTS is the standard release. All that it means is that Ubuntu 10.04 will be supported for much longer than a standard release.

---

### Post by Bucky24 on 2010-06-13
> **clhsharky said:**
> Bucky24

Ubuntu 10.04 and 10.04LTS release is one in the same.

Sharky

Does that mean when 10.10 comes out I will be able to upgrade without problems?

[QUOTE=WorMzy]
LTS stands for Long Term Support. I'm not sure why you think this is bad, or is something you don't want, but it shouldn't affect your experience.
[/QUOTE]

Because usually LTS versions are released only every 2 years. I prefer to update my machine more often than this.

-Bucky24

---

### Post by steve161 on 2010-06-13
system-administration-software soures-updates-release upgrade.  Change from "long term support releases only" to "normal releases"

---

### Post by Iowan on 2010-06-13
> **Bucky24 said:**
> Does that mean when 10.10 comes out I will be able to upgrade without problems?
...
Because usually LTS versions are released only every 2 years. I prefer to update my machine more often than this.

-Bucky24You should be able to upgrade to 10.10. Without problems?

---

### Post by Bucky24 on 2010-06-13
> **steve161 said:**
> system-administration-software soures-updates-release upgrade.  Change from "long term support releases only" to "normal releases"

Awesome, thanks.

-Bucky24

---

### Post by garvinrick4 on 2010-06-13
> **Bucky24 said:**
> Does that mean when 10.10 comes out I will be able to upgrade without problems?



Because usually LTS versions are released only every 2 years. I prefer to update my machine more often than this.


-Bucky24
                           ```
sudo sed -i 's/lucid/maverick/g' [/etc/apt/sources.list]("file:///media/etc/apt/sources.list") && sudo aptitude update && sudo aptitude dist-upgrade
 
```

Here she is Bucky24 use at your in your own time.

---

