---
title: "How do I create my own meta-package?"
date: 2009-08-13
forum: General Help
---

### Post by sblunix on 2009-08-13
Hey guys, I've never compiled a .deb, and I have no knowledge on how .deb files work, but, I figure as a first .deb file, I don't actually want to include a program, I just want to list some programs from the repository I think people should install as dependencies, and when the installation happens, those programs run, so, how would I go about doing this?
I'm thinking I want it to work like [non-free-codecs]("apt:non-free-codecs") or [ubuntu-restricted-extras]("apt:ubuntu-restricted-extras"), there is no actual program, it's just a meta-package (as far as I know)...

---

### Post by sblunix on 2009-08-13
Sorry, shameless self-bump and whatnot... It's been an hour and after doing a bunch of reading, I'm still confused :(

---

### Post by maheshasolkar on 2009-08-13
I have not done this myself. But to point you in some direction - for lack of any other help :) - here's a couple of articles that may be helpful:

  [http://www.linux.com/archive/articles/60383](http://www.linux.com/archive/articles/60383)

  [http://www.debian.org/doc/debian-policy/ch-controlfields.html](http://www.debian.org/doc/debian-policy/ch-controlfields.html)

If you can put the packages you want installed as dependencies of your new meta-package, it should work. No guarantees!

---

