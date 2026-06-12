---
title: "Error: Dependency is not satisfiable:libdvdread3"
date: 2009-10-13
forum: General Help
---

### Post by Seemples! on 2009-10-13
Eet ees new for me to come to using the Ubunu Linux v 9.04 after ears of meerkat magic using the horreeble Weendows!
 
But seriously, I have literally just installed Ubuntu 9.04 on a partitioned drive on a laptop to test out an application called TEOTUX which was written and tested on Ubuntu 7.04.
 
I have downloaded the deb package but when I try to install using the Synaptic package manager it it throws up the above error.
 
libdvdread3 is no longer available and I assume was replaced by libdvdread4 which is already installed.
 
Is there any way to get around this problem or is it something I need to take up with the people who wrote the source code?
 
As a new to Linux user any help would be much appreciated.
 
I only wish it was SEEMPLES![-o<

---

### Post by P4man on 2009-10-13
Did you try install libdvdread4  ? Might well work. just open a terminal and type

```
sudo apt-get install libdvdread4 
```

Then try the deb again.

---

### Post by Seemples! on 2009-10-13
Yup, hence this statement in my original post
 
**'libdvdread4 which is already installed.'**
 
Are these things normally backwardly compatible?

---

### Post by P4man on 2009-10-13
Sorry, I guess I didnt read carefully enough :blush:
You can force the install, and it may just work with libdvdread4, or not, but perhaps you don't even need to rip dvds ?

Anyway, try this. Download the .deb. Open a terminal, and cd to the download folder. Eg

```
cd Downloads
```

Then run this:

```
sudo dpkg --ignore-depends=libdvdread3 -i  teotux-media_2.20.7-1_all.deb 
```

(you can copy paste that to avoid typo's)

---

### Post by Seemples! on 2009-10-13
\\:D/Yeii Eet Vorked!!
 
A Gazillion Thanx my Friend, You are welcome at Meerkat Manor aneetime!
 
Cheers

---

### Post by P4man on 2009-10-13
> **Seemples! said:**
> \\:D/Yeii Eet Vorked!!
 
A Gazillion Thanx my Friend, You are welcome at Meerkat Manor aneetime!
 
Cheers

Dont be too happy yet, you'll have troubles doing upgrades I think (broken packages). But you can check it out at least, and perhaps someone will post a better solution.

---

### Post by Seemples! on 2009-10-13
I wonderd if it might be better to reinstall Ubuntu version 8.04 which uses libdvdread3, install Teotux and then upgrade to Ubuntu 9.04.
 
Would that be a better way to go and would it solve the problem if upgrading a previously instlled application?

---

