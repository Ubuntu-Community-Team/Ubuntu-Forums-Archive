---
title: "Updating gawk"
date: 2011-12-29
forum: General Help
---

### Post by l07 on 2011-12-29
I'd like to update gawk to 4.0 and would like to know how best to do so, and how to avoid any problems that may arise.

---

### Post by Lars Noodén on 2011-12-29
The freshest one in the repository for upcoming 12.04 is still only gawk 3.1.8, so you'll have to roll your own package.  

It's easy once you've done it the first time.  But you'll have to look around for documentation.  Here's one to get started with:

[http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/](http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/)

---

### Post by l07 on 2011-12-30
I was thinking simply aliasing gawk to a locally compiled version in .bashrc would allow me to use the new version interactively, but then if I want to use it in scripts, aliases would have to remain effective there. Then I was thinking, if nothing depends on gawk, so I can just replace the binary. Is that so?

---

### Post by Lars Noodén on 2011-12-30
The only package that seems to depend on gawk is the package "base-files"  If you overwrite the binary and it turns out there is a conflict then I guess you could always re-install the old package.

---

