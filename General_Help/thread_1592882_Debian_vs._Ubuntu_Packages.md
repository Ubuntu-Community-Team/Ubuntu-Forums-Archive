---
title: "Debian vs. Ubuntu Packages"
date: 2010-10-11
forum: General Help
---

### Post by Zanthir on 2010-10-11
I am trying to figure out which package I should install for Wordpress because I want a multi-user site and this is no longer supported under Wordpress-Mu, but is now supported under Wordpress version 3 ([reference]("http://mu.wordpress.org/"))

Wordpress-Mu is an Ubuntu package available via apt-get through the universe repository ([Wordpress-Mu 2.9]("http://packages.ubuntu.com/lucid/wordpress-mu"))[]("http://packages.ubuntu.com/lucid/wordpress-mu"). I found an unstable Debian package for Wordpress 3.0 that supports multi-user sites (and will continued to be supported) here ([http://packages.debian.org/unstable/web/wordpress](http://packages.debian.org/unstable/web/wordpress)).

So I'm wondering a few things. First, are Debian packages completely compatible with Ubuntu, or are there differences that may complicate things? I know Ubuntu packages *are* Debian packages (I think), but I think this is a valid question. (Maybe move to absolute beginners?) Second, besides downloading Wordpress 3.0 from the site above, is there a repository I can get it from, maybe an Ubuntu repository? I'm thinking if there are some small differences to improve performance on Ubuntu vs. some other Debian install, this would be the preferred way to go.

Thank you for all your help in advance.

---

### Post by mc4man on 2010-10-11
> are Debian packages completely compatible with Ubuntu, or are there differences that may complicate things?
There are certainly differences that will complicate things or worse, though there are some packages that can be installed without issue.
(you'd need to follow the dependency trail - in this case I wouldn't even bother.

Maverick has the 3.0 version, that's an option to consider 

This ppa has wordpress 3.0 for lucid
[https://launchpad.net/~lucid-bleed/+archive/ppa](https://launchpad.net/~lucid-bleed/+archive/ppa)

I would be very careful with this ppa - it also contains other backported maverick packages, including ffmpeg and libs.

If you use, I wouldn't leave the ppa enabled after installing whatever you want and then blindly using the update manager.

---

### Post by Zanthir on 2010-10-11
Oh, thanks. This is a fresh install of Ubuntu Server (as of yesterday), so I'll probably just go with Ubuntu 10.10 (as it seems to have been [released yesterday]("https://lists.ubuntu.com/archives/ubuntu-announce/2010-October/000139.html")).
 
I'm relieved to hear it supports Wordpress 3. Hopefully that will make my life easier.

---

