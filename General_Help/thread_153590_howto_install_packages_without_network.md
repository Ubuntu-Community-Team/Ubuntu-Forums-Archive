---
title: "howto install packages without network ?"
date: 2006-04-01
forum: General Help
---

### Post by Sod75 on 2006-04-01
Hi there, 

I've installed a pc with Kubuntu for someone that doesn't have an internet connection. So far so good. But how do I install something extra on that pc since I can't just use Adept or apt-get...

I have internet access myself (obviously) so am I right in assuming I could just do the following ?

eg to install frozen-bubble
-download frozen-bubble_1.0.0-6_i386.deb (via Adept, copy it from /var/cache/apt/archives)
-burn it on a cd ,insert the cd on the destination pc, mount it
-run dpkg -i frozen-bubble_1.0.0-6_i386.deb

but how do I know if it has dependencies on other packages not on that pc ?
Any way of listing all packages a package depends on ?
would it even work as I described ? Is there an even easier way ?
:-k

---

### Post by Rog131 on 2006-04-01
It is possible to download stuff from repositories and make local repository: [http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-dpkg-scanpackages)

[COLOR="Red"]BUT[/COLOR] dependencies are the problem.

Example:
apt-cache show kate - tells:

Depends: kdelibs4c2 (>= 4:3.5.2), libacl1 (>= 2.2.11-1), libart-2.0-2 (>= 2.3.16), libattr1 (>= 2.4.4-1), libaudio2, libc6 (>= 2.3.4-1), libfontconfig1 (>= 2.3.0), libfreetype6 (>= 2.1.5-1), libgamin0, libgcc1 (>= 1:4.0.1), libice6, libidn11 (>= 0.5.13), libjpeg62, libpng12-0 (>= 1.2.8rel), libqt3-mt (>= 3:3.3.4), libsm6, libstdc++6 (>= 4.0.1), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxft2 (>> 2.1.1), libxi6, libxinerama1, libxrandr2, libxrender1, libxt6, zlib1g (>= 1:1.2.1)
Recommends: kregexpeditor
Suggests: aspell | ispell | hspell, kate-plugins, khelpcenter, konq-speaker, konsole

More about installing without permanent internet connection:
Topic: possible without internet? 
[http://kubuntuforums.net/forums/index.php?topic=3798.msg14548#msg14548](http://kubuntuforums.net/forums/index.php?topic=3798.msg14548#msg14548)

---

### Post by christhemonkey on 2006-04-01
if you go to [packages.ubuntu.com]("packages.ubuntu.com") then you can search for what you like, and then see all the dependencies, and get all of them and their dependencies, and eventually will have everything needed!

---

