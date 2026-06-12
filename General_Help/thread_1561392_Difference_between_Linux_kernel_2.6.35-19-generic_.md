---
title: "Difference between Linux kernel 2.6.35-19-generic and 2.6.35.3"
date: 2010-08-26
forum: General Help
---

### Post by inameiname on 2010-08-26
What is the difference between those kernels that you can install from this PPA:

[https://launchpad.net/~kernel-ppa/+archive/ppa]("https://launchpad.net/%7Ekernel-ppa/+archive/ppa")

ppa:kernel-ppa/ppa

...which currently has 2.6.35-19.25-generic

AND

[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

...which currently has 2.6.35.3-maverick (even has later version 2.6.36-rc2-maverick)

AND

[http://www.kernel.org/](http://www.kernel.org/)

...which currently has 2.6.35.3 (even has later versions 2.6.36-rc2 and 2.6.36-rc2-git4)

???

Are they the same? Which is newer? Is 2.6.35-19-generic = 2.6.35.3?

Thanks in advance.

---

### Post by inameiname on 2010-08-26
No responses. Doh! Figured this would be an easy answer thing from somebody who knows.

---

### Post by grandtoubab on 2010-08-26
> **inameiname said:**
> What is the difference between those kernels that you can install from this PPA:

[https://launchpad.net/~kernel-ppa/+archive/ppa]("https://launchpad.net/%7Ekernel-ppa/+archive/ppa")

ppa:kernel-ppa/ppa

...which currently has 2.6.35-19.25-generic

AND

[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

...which currently has 2.6.35.3-maverick (even has later version 2.6.36-rc2-maverick)

AND

[http://www.kernel.org/](http://www.kernel.org/)

...which currently has 2.6.35.3 (even has later versions 2.6.36-rc2 and 2.6.36-rc2-git4)

???

Are they the same? Which is newer? Is 2.6.35-19-generic = 2.6.35.3?

Thanks in advance.
I use
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
This one are builded by Ubuntu team
but I select the kernel matching with the distribution I use. Do not mix Lucid kernel and Maverick kernel for example.
RC are "release candidat" meaning they are not fullly tested, so do not use them unless you know what you are doing :D

---

### Post by AlphaLexman on 2010-08-26
Well I am not a kernel expert, but this is what I understand...

The different kernels you mention are NOT the same, although MOST people / users could not tell the difference. 

The PPA kernel is a user's personal modification of the open-source kernel.
The Ubuntu kernel is Canonical's corporate modification of the open-source kernel.
The Kernel.org version is most likely closest to Linus Torvalds release kernel.

Which one is newest? It's hard to say! It is possible a PPA or Canonical could release a modified version of the older kernel after a newer one has been added.

I do understand that dots (.) preceed dashes (-) in naming conventions. Therefore "2.6.35-9999" is less than "2.6.36-0" and there are no leading zeros either, so "2.6.35-3" is less than "2.6.35-19"

---

### Post by inameiname on 2010-08-27
I see. Thanks for your clarification. 

I knew they weren't really the same, but were compiled and made forms from the tar file from kernel.org, I was just unsure of which might be best to install. 

So you are saying the PPA kernel isn't from the kernel people? I thought it was just the PPA that is used by those that make the thing. My bad.

And you are saying that the Canonical's the best to easily install for Ubuntu, even moreso than the PPA, ehy? But only the ones that say Lucid on them, not Maverick. Why is that exactly, especially as there isn't any newer or non-RC that are the latest kernel and stable? Just curious. 

Anyway, thanks for the info. Guess I sort of have it understood now. Sort of. :P

---

### Post by inameiname on 2010-08-29
I found a link between the official one in the Ubuntu repos and the kernel-ppa that I'm using, which was previously thought of as a user modification of the kernel.

[http://www.ubuntuupdates.org/packages/show/248451](http://www.ubuntuupdates.org/packages/show/248451)

[http://www.ubuntuupdates.org/pm/linux-image-2.6.35-19-generic](http://www.ubuntuupdates.org/pm/linux-image-2.6.35-19-generic)

So if I'm not mistaken, it sounds as though it's literally the Ubuntu kernel's PPA, backported to use on Lucid. At least, that's my theory. I mean, why would they mention how to find the kernel through it if it isn't sponsored by it?

Thus, this also makes me wonder that if the PPA is indeed part of Ubuntu's release of their official modification of the kernel, how does that actually differ from the [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")'s mainline kernel? Both are official releases? IDK...

---

### Post by inameiname on 2010-08-29
I found this article that explains what the mainline kernel in [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) is:

[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)

So let me break it down how I think it is then.

You have the original kernel, not customized at all, and is the truest version you can get, from:

[http://www.kernel.org/](http://www.kernel.org/)

There, you can compile it as it is, or customize it for your particular pleasures, or your specific Linux distro. These have the names like this: 2.6.35.3

Reading the new article I found, it seems that the official Ubuntu kernels are stock kernels that have been modified from the original one ([http://www.kernel.org/](http://www.kernel.org/)), to best work with Ubuntu. They include Ubuntu patches and whatnot. These have the names like this: 2.6.35-19-generic. And for Maverick's Alpha 3, this can been seen by looking inside their repositories and looking at what version of the kernel it is running.

Also from the article, the mainline kernels, available as deb files in [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) are unmodified kernels, without any Ubuntu kernel patches (other than using Ubuntu kernel configuration files). Basically, compiled from [http://www.kernel.org/](http://www.kernel.org/) and made into these mainline kernel deb files for easy installation.

Finally, the PPA, [https://launchpad.net/~kernel-ppa/+archive/ppa]("https://launchpad.net/%7Ekernel-ppa/+archive/ppa") (or ppa:kernel-ppa/ppa), seems to be those very Maverick Alpha 3 Ubuntu customized/patched kernels backported to Lucid.

So essentially, all three mentioned in my thread can be considered 'official'.

Hopefully this sounds correct. ;)

Oh, and here is an explanation on version numbers:

> 
The kernel package version is of the following form 2.6.35-6.9.  The numbers before the -  represent the base upstream version from which this kernel was forked, the first number following the -  represents the ABI number, the final number is an upload number.   Taking the package version first remove the upload number, then round  the ABI number down to the nearest hundred (which can include 0), for  example: 
2.6.35-6.9 => 2.6.35-6 => 2.6.35-0 


---

