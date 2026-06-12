---
title: "Forced install of package with unmet dependency, now apt inconsolable"
date: 2011-10-01
forum: General Help
---

### Post by gumpish on 2011-10-01
Greetings.

I just forced the install of the Natty package for python-beautifulsoup (there's a big difference between soup 3.2 and soup 3.1). The Natty version is set to depend on a higher minor version of Python, which is actually completely immaterial to Beautiful Soup (and indeed, it runs perfectly fine!).

So I forced the install and everything is going fine except that now all of the package management interfaces howl and whine that they can't do ANYTHING at all (such as install updates) while there is a "broken" package on the system.

How can I get the package managers to ignore the fact that I have a package installed which has an unmet dependency?

Thanks!

---

### Post by gumpish on 2011-10-03
To answer my own question, my solution was to modify the dependencies of the natty version of the package so that my version of Python was now acceptable.

I used the script found here to do it:

[http://ubuntuforums.org/showthread.php?t=636724]("http://ubuntuforums.org/showthread.php?t=636724")

Have a nice day.

---

