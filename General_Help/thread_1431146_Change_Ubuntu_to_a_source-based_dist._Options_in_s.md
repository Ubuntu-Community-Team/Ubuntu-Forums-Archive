---
title: "Change Ubuntu to a source-based dist. Options in synaptic??"
date: 2010-03-16
forum: General Help
---

### Post by Darvenkry on 2010-03-16
Just wondering if there is a way to change synaptic to download the source files instead of the binaries and have them compiled on my computer. I'm thinking that this would create faster applications since they are compiled specifically for my computer. Would also like to know if there is a way to add CFlags and Optimizations somewhere in Ubuntu. I did it in Gentoo since it is source dist by adding things like -O3 --msse3 --fastMaths etc. Any ideas?

---

### Post by tommcd on 2010-03-16
I don't think this is possible. Anything installed via synaptic, apt-get, or the software center will be binary packages from the Ubuntu repos. These packages (as you probably know) are compiled according the wishes of the Ubuntu developers. There is no option that I know of for setting the kind of optimizations you are looking for with standard Ubuntu packages. The only option for this would be to install packages from source.
If you wish to compile packags from source in Ubuntu, first install the **build-essential** package from the Ubuntu repos.

Just out of curiosity, if you were using Gentoo and doing this kind of stuff, why did you switch to Ubuntu, which is a binary packaged distro?

---

### Post by Darvenkry on 2010-03-16
Well Gentoo was alot of hassle, and i think the development seemed to have died off aswell. Sure it was fun optimizing it for weeks and weeks to get some perfect build with kernel hacking etc. But Ubuntu is fast enough, and all the devices work straight out of the box. Just wanted that one feature which was the package manager for gentoo would compile everything from source instead of getting binaries so everything was optimized on the computer.

---

### Post by leorolla on 2010-03-16
[http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html)

Good luck.

---

### Post by slakkie on 2010-03-16
It is possible, but good luck in maintaining it.

---

### Post by skymera on 2010-03-16
Check out apt-build

It downloads the source and compiles it. Not as good as Gentoos, but i think it's worth a look at.

---

### Post by Darvenkry on 2010-03-16
Thx skymera, that is exactly what i was looking for. Any other similar applications like apt-build? One with a GUI maybe. Also how up to date is apt-build compared with the normal synaptic repos.

---

### Post by tommcd on 2010-03-17
> **Darvenkry said:**
> Well Gentoo was alot of hassle, and i think the development seemed to have died off aswell. Sure it was fun optimizing it for weeks and weeks to get some perfect build with kernel hacking etc.
Have you used Slackware at all? You can do stuff like this in Slackware without having to worry about dependency conflicts that you can run into with APT. Also, Slackware uses plain vanilla kernel and packages, so compiling a kernel is fairly easy in Slackware.

---

### Post by skymera on 2010-03-17
> **Darvenkry said:**
> Thx skymera, that is exactly what i was looking for. Any other similar applications like apt-build? One with a GUI maybe. Also how up to date is apt-build compared with the normal synaptic repos.

As far as i know it's the same as the repos.

After all, it pulls the source directly from the same repos.

Go to System > Administration > Software Sources

Make sure "Source Code" is ticked and anything else you would like.

I'm not sure if anything else exists like this.

---

### Post by j7%&lt;RmUg on 2010-03-17
Why not just do apt-get source on an app in the repos to get the source files and then just compile by hand? that is what you want to do right?

example:

apt-get source "app name here"

just chuck that in a terminal without the double quotes and off it goes.

---

