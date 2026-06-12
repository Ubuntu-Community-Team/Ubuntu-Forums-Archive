---
title: "Airsnort"
date: 2006-02-16
forum: General Help
---

### Post by screener on 2006-02-16
How can I install airsnort on my ubuntu laptop?

Thanx

Screener

---

### Post by christhemonkey on 2006-02-16
Its in the repositories, in universe. (version 0.2.6-1)
Has quite alot of dependencies if your not installing through synaptic or apt.
(like if your not on the tintenet on the laptop.)

---

### Post by mjsoccer1 on 2006-03-06
[I]Package airsnort is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package airsnort has no installation candidate
[/I]


I tried downloading the source, and compiling the source with
[I]./configure
make
make install[/I]

and I get this:
[I]configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
[/I]

Anyone have any solutions? Thanks

---

### Post by Ramses de Norre on 2006-03-06
Do you have universe enabled? Looks like you haven't.

---

### Post by mjsoccer1 on 2006-03-06
I have all of my repositories enabled, and all Universe repositories are set as multiverse.

---

### Post by mjsoccer1 on 2006-03-06
I set the community repositories back to Universe and I am able to download and install airsnort... I thought that by making them multiverse, that included all Universe packages as well... apparently not?????  Thanks for the suggestion... What is the difference between multiverse and universe?

---

### Post by Ramses de Norre on 2006-03-06
Universe is community maintained and multiverse are packages that are illegal in a lot of countries. When you don't mind about that you should enable them both.

---

