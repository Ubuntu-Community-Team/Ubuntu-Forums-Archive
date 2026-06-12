---
title: "Apt-build World"
date: 2011-11-09
forum: General Help
---

### Post by thunder9861 on 2011-11-09
Good day,

Recently, I have stumbled upon the possibility of recompiling the entire os using the "apt-build world" command, however I am having some difficulties getting it to work.

As a simple example, if I do (as root):
```
apt-build install leafpad
```I see the sources download and compile, however before the resulting package actually installs, I am left with this error:
```
E: The value 'apt-build' is invalid for APT::Default-Release as such a release is not available in the sources
```I am running a barebones install of Ubuntu Oneiric Server edition (freshly installed) on an Asus T91MT netbook. 

The reason I am experimenting with apt-build world is due to the significant speed increase I achieved after tweaking and recompiling the kernel for the Atom processor.
I want to optimize the entire OS in the same way. On top of this, I am interested in the learning experience, and would like to write a guide on how to accomplish this task once I get it working.

I am well aware that Ubuntu is not suited for building from source, and that Gentoo or LFS would be better choices, however I am quite a fan of Ubuntu and don't see any reason why it shouldn't be possible.

Thank you for any tips / help!

---

### Post by thunder9861 on 2011-11-09
Aha! I figured out the trick.
I need to issue the command like this:
```
apt-build -t oneiric install leafpad
```It appears that by doing this, I will not get a newer package that may be available in oneiric-updates or oneiric-security. I will be playing with apt-pinning to see if I can resolve this issue, but if anyone knows more on this topic, please do share.

Thanks

---

### Post by thunder9861 on 2011-11-10
Ive determined that apt-build is rather inconsistent and not too reliable for what I am trying to do.
For example, "apt-build install bsdutils" fails because it cannot find the source package. This is because the source package is actually "utils-linux". "apt-build install utils-linux" works just fine. On the other hand, "zlib1g" is provided by package "zlib", however "apt-build install zlib" fails because it cannot find the associated binary (Why should it care about the binary?). "apt-build install zlib1g" however works just fine.

Both of these cases appear to have no issues with the normal "apt-get source" command, therefore I am writing some scripts to produce the same behavior as "apt-build world" without actually using apt-build at all. My strategy is as follows:

The user defines a list of packages they want to install in a file
The script iterates through the file and determines the dependencies of each package using "apt-rdepends"
The script then determines the packages of each dependency using "apt-cache showsrc"
Finally, the resulting package list is fed into "apt-get build-deps" and "apt-get -b source"

I haven't tried it yet, but this should result in a folder full of .deb's, which can then just be installed using "dpkg -i *.deb".

I'll keep this post updated with my findings.

---

### Post by thunder9861 on 2011-11-11
Well, my script is running and the system is recompiling. I'm not sure  how long it will take, maybe a day or two, but hopefully it will be a  success!

I'm also working on a second script that can automatically download  updated packages and compile them from source, so I should be able to  have a fully updated Ubuntu system compiled specifically for my machine.

I'll wait until its complete before sharing the scripts, since I want to make sure they work first.

---

### Post by Aide9aic on 2012-04-21
Bumping an old but timely thread, for I just stumbled across **apt-build** and am considering it myself, mostly for the learning experience.

I'm wondering if you ever got those scripts in a form that you'd be willing to share?

---

