---
title: "[getdeb] Searching specific repositories and using specific versions of programs"
date: 2009-07-31
forum: General Help
---

### Post by altonbr on 2009-07-31
Is there a way with apt/apt-get/aptitude, synaptic, add/remove, etc. to search specific repositories?

I want to look through getdeb's testing repository.

I found a list on a mirror ([http://mirrors.dotsrc.org/getdeb/ubuntu/dists/jaunty-getdeb-testing/games/binary-i386/Packages](http://mirrors.dotsrc.org/getdeb/ubuntu/dists/jaunty-getdeb-testing/games/binary-i386/Packages)), but I wanted it to be through a package installer instead.

Is it possible?

The repository is:
```
deb http://archive.getdeb.net/ubuntu jaunty-getdeb-testing games
```

---

### Post by dcstar on 2009-07-31
> **altonbr said:**
> Is there a way with apt/apt-get/aptitude, synaptic, add/remove, etc. to search specific repositories?

I want to look through getdeb's testing repository.

I found a list on a mirror ([http://mirrors.dotsrc.org/getdeb/ubuntu/dists/jaunty-getdeb-testing/games/binary-i386/Packages](http://mirrors.dotsrc.org/getdeb/ubuntu/dists/jaunty-getdeb-testing/games/binary-i386/Packages)), but I wanted it to be through a package installer instead.

Is it possible?

The repository is:
```
deb http://archive.getdeb.net/ubuntu jaunty-getdeb-testing games
```

Synaptic will offer you all versions of a package available in all of your repositories, you can install whatever version you see on the list.

---

### Post by altonbr on 2009-07-31
> **dcstar said:**
> Synaptic will offer you all versions of a package available in all of your repositories, you can install whatever version you see on the list.

Ya I know, but is there any way to JUST search the repository? I want to know what software is in there as you can't traverse [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu)

It's a silly request, I know, because I already found a mirror with the Releases file, I just want to be able to search with synaptic or something.

This would be very useful for other repositories.

---

### Post by luigi_mb on 2009-07-31
> **altonbr said:**
> Is there a way with apt/apt-get/aptitude, synaptic, add/remove, etc. to search specific repositories?



Get the whohas package from the repositories.

/luigi

---

### Post by altonbr on 2009-07-31
> **luigi_mb said:**
> Get the whohas package from the repositories.

/luigi

That looks like a very useful program, thank you.

---

