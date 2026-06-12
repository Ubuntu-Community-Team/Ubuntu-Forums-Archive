---
title: "Gestikk  on Ubuntu 9"
date: 2009-07-12
forum: General Help
---

### Post by jossaq on 2009-07-12
Hi there I'm trying to set up gestikk on my Ubuntu 9.

When I run it this error appears

Traceback (most recent call last):
  File "/usr/bin/gestikk", line 30, in <module>
    import gestikk.tools as gtools
ImportError: No module named gestikk.tools

Any help?

TKS
Jossaq

---

### Post by DizzyC on 2009-07-27
Same problem here :(

---

### Post by vruum on 2009-07-27
are you installing from the .deb package? if so it's using an old version of python, either get the tarball from the gestikk website (and read the README, it has instructions for installing) or edit the first line of /usr/bin/gestikk to say #!/usr/bin/python2.5 or copy the gestikk folder in /usr/lib/python2.5/site-packages to /usr/lib/python2.6/dist-packages/

---

### Post by hookdump on 2009-08-02
> edit the first line of **/usr/bin/gestikk** to say **#!/usr/bin/python2.5**

Thank you so much, that worked perfectly!

---

### Post by flakojaime on 2009-08-23
> **hookdump said:**
> Thank you so much, that worked perfectly!


me too

thanks!

---

