---
title: "Lightweight distro with WUbI"
date: 2011-07-25
forum: General Help
---

### Post by pourjour on 2011-07-25
salut tous les membre j'ai un souci longtemps avec mon ancien ordinateur (Stupid Pc) qui 192 mo pour la RAM et 120 Gb pour le HDD et pour le processeur 600 mhz, et une carte graphique ATI 8mo.le probleme c'est que je cherche une distribution léger pour cette ordinateur qui s'applique à ces recommandation et grand probleme :( c'est que la distribution doit être équiper du (Wubi).SVP aidez moi à trouver une.Merçi par avance.:)
----------------------------------------------------------------------------------------------------
hi members i have a problem with my old pc (stupid pc) the hardware :
RAM: 192 mo .
HDD: 120 GB (no probelem here).
CPU: 600 mhz.
Card graphic: 8 mo.
the probleme that i need a dstro can run using these requirement but distro must be provided by the (wubi)
Please i need your help to bring this computer to life;).thnaks

---

### Post by mike555 on 2011-07-25
Xubuntu

---

### Post by pourjour on 2011-07-25
> **mike555 said:**
> Xubuntu
 i tried.
but i can't work with them because xubuntu is too heavy they need 256 mo of ram as minimum and xfce is also heavy.:(thanks anyway

---

### Post by Nytram on 2011-07-25
Then I think you're out of luck because the lightest version of Ubuntu is Lubuntu, but I don't believe it will install with Wubi.

Any reason in particular you need to use Wubi instead of a Live disk?

---

### Post by pourjour on 2011-07-25
i found a beautiful and a lightweight distro called CrunchBung and one called MadBox the both good but i need to installed using wubi

---

### Post by mastablasta on 2011-07-25
> **pourjour said:**
> but i need to installed using wubi
 
why?
 
you are attemptint to use virtualisation on low ram system and low processor power system. you would be better off to split the disk, create a linux partition and install it there (side by side dual boot)

---

### Post by pourjour on 2011-07-25
i forgot to tell you that i have a problem in my pc when i create a partition and installing a system beside the xp the boot loading freeze and i can't select anyone of my system of exploitation nor linux nor xp.
and it doesn't work until a delete linux partition.
that why. thanks for your interesting .

---

### Post by bcbc on 2011-07-25
Wubi uses the Ubiquity installer (standard ubuntu installer). This in itself requires 256MB ram.

---

### Post by pourjour on 2011-07-26
so hwta i can do to solve my problem the boot freeze, anytime when i want to install an ubuntu distro beside xp or alone the grub froze.

---

### Post by Mark Phelps on 2011-07-26
You were told the installer needs 256MB of memory -- you don't have enough.

The only thing you can do is upgrade your memory to at last 256MB.  You can't force the installer to run in less memory.

---

### Post by bcbc on 2011-07-26
Yeah the alternate installer requires less RAM but it won't work with Wubi so you have to partition - and you said you wanted to avoid that. 

See [http://www.xubuntu.org/get](http://www.xubuntu.org/get)
> Minimum system requirements
You need 256 MB RAM to run the Live CD or 256 MB RAM to install. The Alternate Install CD only requires you to have 64 MB RAM at install time.

To install Xubuntu with the standard installer (Ubiquity), you need 4.4 GB of free space on your hard disk. The Alternate Install CD only requires you to have 2 GB of free space on your hard disk.

Once installed, Xubuntu can run with starting from 256 (or even just 192) MB RAM, but it is strongly recommended to have at least 512 MB RAM.

---

