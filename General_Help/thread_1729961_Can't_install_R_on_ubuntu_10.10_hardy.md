---
title: "Can't install R on ubuntu 10.10 hardy"
date: 2011-04-15
forum: General Help
---

### Post by nihilion on 2011-04-15
Hello,

I've having trouble installing R. I tried following instructions available online, but nothing seems to work properly. For example, here: [http://cran.r-project.org/bin/linux/ubuntu/README](http://cran.r-project.org/bin/linux/ubuntu/README)

I get the following error message:

The following packages have unmet dependencies:
 r-base : Depends: r-base-core (>= 2.13.0-1lucid0) but it is not going to be installed
          Depends: r-recommended (= 2.13.0-1lucid0) but it is not going to be installed
          Recommends: r-base-html but it is not going to be installed
E: Broken packages


So then I try to install r-base-core, and I get the following:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 r-base-core : Depends: liblzma1 (>= 4.999.9beta+20091116) but it is not installable
E: Broken packages


Installation via synaptic doesn't work either. I get the following similar error:

r-base:
 Depends: r-base-core but it is not going to be installed
 Depends: r-recommended but it is not going to be installed
 Recommends: r-base-html but it is not going to be installed


Thank you

---

### Post by nihilion on 2011-04-15
I found the problem. My addition to the source list had 'lucid' instead of 'hardy'. oops.

---

### Post by WorMzy on 2011-04-15
I'm a little confused by this.

10.10 is Maverick Meercat.

Hardy is 8.04.

Lucid is 10.04.

I think you need to decide which version you're using. :P

---

