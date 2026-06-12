---
title: "Installing Software Packages"
date: 2006-01-30
forum: General Help
---

### Post by Wouterrrr on 2006-01-30
Hey all,

I'm having kind of difficulties with installing software packages through the synaptic package manager in unbuntu.

For example when I click on mysql-server-4.1 I get some dependency errors :confused: 
> mysql-server-4.1:
 Depends: mysql-common-4.1 (>=4.1.12-1ubuntu3) but it is not installable
 Depends: mysql-client-4.1 but it is not going to be installed
 Depends: libdbi-perl  but it is not installable

Also other package's like eclipse (dependencies) and subversion (isn't in the list) and a lot of others complain when I try to install them. I don't get this, why do they complain, and why are they in the list then? :-| 

Does this mean I have to install them or their unresolveable dependencies by hand? I tried to install pkgsrc ([http://www.netbsd.org/Documentation/software/packages.html)](http://www.netbsd.org/Documentation/software/packages.html)), but this package complains also:
> configure: error: no relevant library found containing tgetent
And I cant seem to find a solution for this.

Am I too much a beginner, should I read the LDP articles or howto's or what? :confused: 

Thnx in advance,

Wouter

---

### Post by GeneralZod on 2006-01-30
Sounds like you need to enable some more repositories; check out aysiu's guide here:

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by Wouterrrr on 2006-01-30
That just wat it needed, the package manager is working perfect now!,

The linux world has opened before my eyes today!

Thnx mate!

Wouter

---

