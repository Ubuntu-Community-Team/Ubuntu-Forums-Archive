---
title: "updating perl to latest version"
date: 2011-04-13
forum: General Help
---

### Post by wily_one on 2011-04-13
Basic noob question: How do I use apt-get to upgrade an existing package to the latest version?  

Specifically, I have Perl v5.10.1 installed, and I see that v5.12.3 is  the latest.  I don't want to download source and compile, I want to be  lazy and just run something like apt-get.  Doable?  TIA.

---

### Post by lithopsian on 2011-04-13
> I see that v5.12.3 is  the latest
You see where?  On a website?  The latest version could be anything but you can only upgrade to what is in the Ubuntu repository.

If you want to get a little bit fancy you can add a repository that offers builds of a newer version.  Or download a deb file that someone has built for you.  Or you can download the source and build yourself any version you like, assuming that you have compatible headers that it needs.

Ubuntu only has up to 5.10.1 in the repositories.  I'm not aware of a PPA that offers newer versions of Perl so you would have to compile your own.

---

### Post by wily_one on 2011-04-13
Thanks - how do I see what versions are in the Ubuntu repository?  And yes I see the latest from the source: [www.perl.org](www.perl.org).

---

