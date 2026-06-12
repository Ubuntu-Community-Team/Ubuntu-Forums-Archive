---
title: "Kernel won't work"
date: 2012-04-19
forum: General Help
---

### Post by Hungry Man on 2012-04-19
So I've compiled the basic 3.2.2 linux kernel from kernel.org but Ubuntu just has a purple screen on boot. I didn't patch it with anything, just the plain thing.

Is there something I need to do to get it working with Ubuntu?

---

### Post by Doug S on 2012-04-19
You should be able to get the mainline 3.2.2 kernel, already compiled from here:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.2-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2.2-precise/) 
 
It is not clear to me why you would want that version instead of a more current one.
see also: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
and: [http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html](http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html) 
 
Sometimes other work is required to make a mainline kernel work. For example see recent postings on [this thread]("http://kernel.ubuntu.com/~kernel-ppa/info/kernel-version-map.html")
 
For me, my local console never works with the mainline kernels. I can only SSH in to use the computer, which is good enough for my testing.

---

### Post by Hungry Man on 2012-04-19
Awesome. Thank you.

So I have the 3.3 kernel source code (current stable from kernel.org) would I just patch it with:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3-precise/)
> 
	0001-base-packaging.patch	19-Mar-2012 01:35	7.5M	 
	0002-debian-changelog.patch	19-Mar-2012 01:35	252K	 
	0003-default-configs.patch	19-Mar-2012 01:35	 45K	 

?

edit: To clear it up, I'm not interested in a precompiled kernel. I want to compile it myself with specific grsecurity patches.

---

### Post by Hungry Man on 2012-04-20
That didn't work. Same issue - purple screen on boot. I'll try the pre-packed .deb but that's not really what I want.

---

### Post by Doug S on 2012-04-20
Normally, I don't compile the mainline versions, so am not much help there.
I think trying the already done .deb files will, at least, provide a useful data point if it works or not.
For what it's worth: When I am trying to implement patches and such, I'll back port them into the appropriate kernel for my system and test/try them that way. I tend to get less dependency issues and such using that approach. I don't know if this approach is possible for your case.
Example of what I do: First, make sure I am all up to date with "apt-get update" "apt-get-upgrade" "apt-get dist-upgrade"; Second, get and compile the source code for whatever kernel I am running; Make sure everything is fine with my kernel, with no changes; Now I have a test environment from which to make and test changes.

---

### Post by Hungry Man on 2012-04-20
The .deb 3.3 did work. It's just when I compile my own. Even when I compile without grsecurity it's broken.

---

