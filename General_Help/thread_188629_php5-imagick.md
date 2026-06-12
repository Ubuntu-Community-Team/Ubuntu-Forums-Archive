---
title: "php5-imagick"
date: 2006-06-04
forum: General Help
---

### Post by n00b2ubuntu on 2006-06-04
Anyone know any repositories I can get php5-imagick?

On upgrading from Breezy to Dapper it upgraded me to php5 but I can only find php4-imagick :( 

Thanks!

---

### Post by n00b2ubuntu on 2006-06-04
Right, well I got the source from debian unstable in the end and compiled it. Seems to work fine! :mrgreen:

---

### Post by Littleweseth on 2006-09-16
If someone could post instructions on how to replicate this, that would be very cool indeed. (I'm writing a mathematical thingy in PHP and need something to convert TeX source to .png's.) For reference, I've never compiled from source in my life :D Guess now's the time to start?

EDIT :

I just stumbled across general instructions ([http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)) on how to install packages from source. I guess the only thing I need help with now is 'how do I get the source from the Debian unstable repo?'. Should I just directly download the file, or add [http://mirroraddress/debian/debian](http://mirroraddress/debian/debian) unstable main non-free restricted to my sources.list and do something with that?

Cheers;
-lws

[Apologies for thread resurrection.]

---

### Post by Littleweseth on 2006-09-16
I seem to be about halfway to solving my own problem. However, I'm running into a bit of ugliness.

Here's what I've done;

```
apt-get install build-essential
added the following to /etc/apt/sources.list
deb-src ftp://mirror.pacific.net.au/debian unstable main contrib non-free
apt-get update
```

Give the source files somewhere to live;
```
cd ~
mkdir ./php5-imagick
cd ./php5-imagick
apt-get source php5-imagick
```

Change into the directory containing the untarred and patched files;
```
cd ./php-imagick_0.9.11+1
sudo dpkg-buildpackage -b
dpkg-buildpackage: source package is php-imagick
dpkg-buildpackage: source version is 0.9.11+1-4
dpkg-buildpackage: source changed by Jose Carlos Medeiros <debian@psabs.com.br>
dpkg-buildpackage: host architecture i386
dpkg-checkbuilddeps: Unmet build dependencies: debhelper (>= 5) dpatch bison flex php4-dev (>= 4:4.4.0-1) php5-dev (>= 5.0.4-3) libmagick9-dev | libmagick-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
```

The problem i'm having involves resolving the dependencies. I'm trying to install them using aptitude, but it appears one of debhelper, dpatch or bison depends on a package called old-flex, which of course doesn't like plain flex.

Any hints on where to go from here?

---

### Post by rossio on 2006-10-01
If I could *bump* this thread again, I'd also love to hear some thoughts on how to get php5-imagick working. I followed the same steps as in the above post, right up to using dpkg-buildpackage, and encountered the same dependencies. This makes me think there must have been a misstep somewhere along the way, because even if the other dependencies (bison, debhelper, etc.) are all met, why would I want to install php4-dev when I already have php5/php5-dev installed?

All in all, I hope someone with more knowledge could shed light on this issue. I really want to get php5-imagick installed and working!

---

### Post by PriceChild on 2006-10-01
DON'T add a debian repo to your sources.list... it could have nasty side effects and dependency troubles.

If i were you i would just download the pagckage and install with dpkg manually.

---

### Post by rossio on 2006-10-01
I think the idea with adding the Debian repository was to then immediately remove it after the php5-imagick source had been been downladed. At least, that's what I did.

> **PriceChild said:**
> If i were you i would just download the pagckage and install with dpkg manually.

But download which package? I might just be overlooking the obvious, but this is exactly what I'm lacking.

On a whim, I also just tried adding Edgy's universe repositories to my sources.list (to be removed immediately thereafter), since this package [does seem to be available for Edgy]("http://packages.ubuntulinux.org/edgy/web/php5-imagick"). But then in trying to install php5-imagick, apt-get simply told me that my libc6 package needed to be >=2.4, whereas Dapper has 2.3.something, so no luck there either.

[Edit:]

In the interests of complete and precise disclosure, this is what I get after adding the Edgy repo:

```
$ sudo apt-get install php5-imagick
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed. The following information may help to resolve the situation:

The following packages have unmet dependencies:
  php5-imagick: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20 is to be installed
E: Broken packages
```

---

