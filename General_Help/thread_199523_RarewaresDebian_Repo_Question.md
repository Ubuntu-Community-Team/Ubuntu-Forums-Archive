---
title: "Rarewares/Debian Repo Question"
date: 2006-06-18
forum: General Help
---

### Post by Cable on 2006-06-18
I've successfully added the following repo to Synaptic
```

deb [http://www.rarewares.org/debian/packages/unstable/]("http://www.rarewares.org/debian/packages/unstable/") ./

``` 
But when I go to install anything there that has certain dependencies, it says it can't install it because it doesn't have a high enough version.  I read on [this page]("http://www.rarewares.org/debian-info-apt.html") on Rarewares that I should add another repo to take care of the dependencies.
```

deb [COLOR=Black][ftp://ftp.nerim.net/debian-marillat/]("ftp://ftp.nerim.net/debian-marillat/")[/COLOR] sid main

``` However, when I try to add this to my repos in Synaptic, then go to reload, it pops up saying it couldn't load that one because no public GPG key is available.  What should I do to solve this problem?  I'd like to use the Rarewares stuff.  :(  Help is greatly appreciated!  Thanks!

---

### Post by RAOF on 2006-06-18
I'll just put my hand up and say "It is in general a **really** bad plan to add Debian repositories to Dapper".  It is possible (but unlikely) to get your install into a state where **nothing** works, not even apt/dpkg, and the only solution is to reinstall.  The marillat repository should be pretty safe, but I don't think there's anything in there which isn't in some Ubuntu repository.

What particular dependencies is it complaining about?

---

### Post by Cable on 2006-06-18
Example:  When I go to install ***oggenc-aotuv*** it says
```

oggenc-aotuv:
  Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20 is to be installed

```

---

### Post by RAOF on 2006-06-18
Ok.  libc6 is one of the foundation packages of your system, it is a **seriously** bad idea to replace it.

Does the rarewares reposistory have source packages?  You won't have all those crazy dependencies if you take the source package and build it yourself.
```
apt-get source -b oggenc-aotuv
```
should build that package from sources, if there are any available.

Alternatively, you could manually download the packages you want, extract them with dpkg, edit the dependency information to match the Ubuntu package, and repack the package with dpkg, then install it.  But building-from-source is much easier.

---

### Post by Cable on 2006-06-18
Well, I found the source for the aotuv ogg vorbis on [this]("http://www.geocities.jp/aoyoume/aotuv/") page.  So I now have the source.  However, it's an entire directory of stuff, so I'm not sure what to do with it.  How do I build it?  The link to download it (in case you want to take a look) is [here]("http://www.geocities.jp/aoyoume/aotuv/libvorbis-aotuv_b4.51.tar.gz.tgz").

---

### Post by RAOF on 2006-06-19
That's not quite what I meant.  The deb-src is what they use to build the packages, and it's easy to build packages from (see my above post).

Since they don't provide that, it's much more difficult.  It might be easier to download the package manually (using firefox or whatever), and then messing with the dependency information.  To do that, you'd want to run (from a terminal):
```
dpkg -x *the_downloaded_package.deb* temp
dpkg --control *the_downloaded_package.deb* temp/DEBIAN
gedit temp/DEBIAN/control

```
Find the bit which says "libc6 (>=2.3.6-6)" and replace it with "libc6 (>=2.3.6-0ubuntu20)".  Then
```

dpkg -b temp *the_downloaded_package_fixed.deb*
sudo dpkg --install *the_downloaded_package_fixed.deb*

```

This will **probably** work.  If it doesn't, it's time for the messiest of the options - building from that zipped source you've got.

---

