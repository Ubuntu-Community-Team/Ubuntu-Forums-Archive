---
title: "Aur for ubuntu"
date: 2011-03-28
forum: General Help
---

### Post by Ockonal on 2011-03-28
Hello, I'm Arch Linux user. I like it only for it's AUR repository. To tell the truth I don't like Ubuntu's PPA repositories. I like when everything is gathered in one place.

So, is it possible to use PKGBUILD from AUR in ubuntu? Maybe it's possible to build **yaourt** (package manager for aur) in ubuntu?

If not, maybe, I'll write some own script which will parse PKBUILDS and run them.

---

### Post by sisco311 on 2011-03-29
> **Ockonal said:**
> Hello, I'm Arch Linux user. I like it only for it's AUR repository. To tell the truth I don't like Ubuntu's PPA repositories. I like when everything is gathered in one place.

So, is it possible to use PKGBUILD from AUR in ubuntu? Maybe it's possible to build **yaourt** (package manager for aur) in ubuntu?


Hi,

I doubt, but I'm not 100% sure...
 
> **Ockonal said:**
> 
If not, maybe, I'll write some own script which will parse PKBUILDS and run them.

Sounds interesting... Maybe a wrapper around checkinstall & auto-apt???

Anyway, if you are going to write it in bash, count me in. :)

---

### Post by 3Miro on 2011-03-29
Hi Ockonal: the AUR repos contain basically scripts that would download, compile and install software. This is done to accommodate software that could not be included in the regular Arch repository. Ubuntu has much bigger resources and keeps a much larger repository providing pre-compiled packages. I doubt there is something in AUR that is not in either the official Ubuntu repo or some unofficial one (the unofficial ones mostly cover "cutting edge" software).

Having used Arch as my main distribution on my desktop for several moths and currently using Arch on my laptop, I don't see an advantage of AUR over ppa (other than wanting to compile your own software, I do currently use Gentoo as my main distro).

---

### Post by wojox on 2011-03-29
yaourt? Packer is way better. :P

sisco's wrapper idea would be cool. It could definetly be a fun side project. If people on Ubuntu have to open the terminal for anything they start freaking out.

---

### Post by novikov on 2012-12-08
One advantage of aur scripts over PPA is that scripts are... Readable. 
You can look at what you install, check that links point to official servers etc. It's also easy to modify a script.
But if you have a ppa repository, you should blindly trust it, and you can't modify it yourself.

---

