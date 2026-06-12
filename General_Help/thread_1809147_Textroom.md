---
title: "Textroom"
date: 2011-07-21
forum: General Help
---

### Post by danceswithcats on 2011-07-21
Hi,

Sorry if I'm posting in the wrong place.

I've installed the excellent textroom on a laptop running Lubuntu and want to install it on my desktop, which runs Ubuntu 10:04.  When I downloaded and ran the deb installer package I got an error: [I]Error: Dependency is not satisfiable: libglibmm-2.4-1c2a (>= 2.25.5)
[/I]
I've reinstalled libglibmm through synaptic and that hasn't solved it.  I wonder whether anyone would know how I can satisfy my computer's dependency, as, apart from the annoyance of not having that software on my computer, the error message makes me feel very inadequate.:(

Kind regards,

Pete

---

### Post by sectshun8 on 2011-07-21
I'm having the same issue with conkyemail and its dependency conkykeyring.  Even with keyring installed I'm always told its not satisfied when I try to do email.

Wish I could help on the "why" it's happening and offer a solution... but just know you're not the only one :)

---

### Post by CatKiller on 2011-07-21
> **danceswithcats said:**
> When I downloaded and ran the deb installer package I got an error: *Error: Dependency is not satisfiable: libglibmm-2.4-1c2a (>= 2.25.5)*

Check the version number. The version with Hardy is 2.16.0 and the .deb file you're installing says that it needs at least 2.25.5 (the Maverick version).

You can either find another source for the program you want to install (either a .deb that can use an earlier version of that library or a repository that can satisfy all the dependencies) or you can install a later version of that library from packages.ubuntu.com along with any dependencies that the library needs. Or you could upgrade Ubuntu.

---

### Post by danceswithcats on 2011-07-21
Thank you.  I'll work through your suggestions.  Much appreciated.

---

