---
title: "Recompile vs. Linux-Image Update"
date: 2006-05-31
forum: General Help
---

### Post by Fatjoint on 2006-05-31
I've read before, and have failed miserably when trying, that recompiling your kernel gets you the most performance out of your rig.  

Is recompiling any different than downloading from Synaptic Package Manager Linux-Image 2.6.12-10-686 and then rebooting?

If you were to try and recompile your kernel, what is the best way of doing it?  Should I be at bare-bones pre-update install?

I can follow instructions, but I don't understand why or how when following the HOW-TO that I get errors and fail.  What's worse, when you read these posts about your performance gains, you get this feeling there's this whole other world of CPU goodness that you're missing out on.

[edit] just wanted to say that last bit isn't a bitch or moan - I just need some help here...

---

### Post by gwpritch on 2006-05-31
Quite honestly I think some of the claims of huge performance increases with kernel recompiles are wildly exaggerated. 
I have compiled quite a few over the years and any gains have been modest.
Certainly tailoring a kernel (by compiling your own) to your own particular hardware configuration can significantly speed up the boot process. The kernel knows exactly what you have and isn't inefficiently searching. There is also disk space to be saved by not compiling and storing every module available.
Dispite some claims to the contrary I have never seen significant gains obtained by merely upgrading from a 386 to a 686 kernel (these pre compiled images must of necessity be tailored( or not) to a very wide range of possible hardware configurations). What it does do is give you access to features of the more modern processors that are not available in older ones. Again some modest gains in efficiency may be found.
As to errors you may be encountering, post them along with your hw configuration an someone may be able to help.

---

### Post by PriceChild on 2006-05-31
I've noticed a slight increase in performance... not really worth the effort though.

What annoyed me most though was despite importing the previous kernel's configuration, and only turning off certain parts to aid performance, various things such as cds and ipods not appearing on the desktop or even mounting resulted from using my own kernel. Very annoying, probably worth just sticking to the standard kernels :)

Pricey

---

### Post by az on 2006-05-31
[QUOTE=Fatjoint]I've read before, and have failed miserably when trying, that recompiling your kernel gets you the most performance out of your rig.  ...[/QUOTE]


Not really the case anymore, ever since hotplug(2002), udev(2004) and HAL which load modules you need, instead of a lot of kernel options running for no reason.


[QUOTE=Fatjoint]
Is recompiling any different than downloading from Synaptic Package Manager Linux-Image 2.6.12-10-686 and then rebooting?...[/QUOTE]
Recompiling per se is just compiling the code.  I guess you assume that you configured it to only compile the bits you need.  The stock linux-image you get from the archive is not configured the way you would do it yourself.



[QUOTE=Fatjoint]
If you were to try and recompile your kernel, what is the best way of doing it?  Should I be at bare-bones pre-update install?...[/QUOTE]

No.  Just install the source, copy the current kernel config and then modify it.  The recompile.  Use kernel-package which generates debs for your new kernel which can be installed and removed easily.
[QUOTE=Fatjoint]
I can follow instructions, but I don't understand why or how when following the HOW-TO that I get errors and fail.  What's worse, when you read these posts about your performance gains, you get this feeling there's this whole other world of CPU goodness that you're missing out on.
[/QUOTE]

With very very few exceptions, you are not missing out on much.  You can install a kernel more specific to your architecture (686, smp, k7, whatever...) but beyond that, don't worry.

---

### Post by gwpritch on 2006-05-31
When compiling your own you should really only reuse your previous configuration if upgrading from say 2.6.12 to 2.6.14.
If you compare the config menues from kernels any further apart you will begin to see many changes, additions and deletions which make your present .config file almost sure to crash and panic the final kernel.
It may seem a pain but if you really want to compile your own, go through the menu from beginning to end manually, selecting or deleting what you want. It is a real learning experience. There is help and advice available for most entries and defaults which are usually fairly safe. 
And keep in mind if your new kernel crahes and burns, you're old one is still there to fall back on. Then look at the logs, and go back into the new configuration and tweak some more.

---

### Post by Fatjoint on 2006-05-31
Thank you very much fellas, if I have this right -

downloading the preconfigured 686 kernel from the repo isn't much worse than compiling your own from scratch, it just has more features loaded and the difference between the two is almost negligible.  You might gain some speed from recompiling, but for the most part you will not.

Mostly compiling from souce is to choose portions of the OS that need or don't need. i.e. services for different hardware.

That correct or mostly?

---

### Post by gwpritch on 2006-05-31
If you're interested in learning about how linux works on a much more basic level I would encourage you to try compiling your own kernel but its not going to change your life and get you more girls.  :mrgreen:

---

