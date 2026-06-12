---
title: "new kernel - very slow!"
date: 2006-03-20
forum: General Help
---

### Post by leche on 2006-03-20
Hi guys,

after having had a "pure" debian for a while, for the ease of installation etc I have now moved to Ubuntu on my laptop, a HP NX6125. Installation went well (although lilo and grub would both exit with an error code on installation if in expert mode but I managed manually) and I am very happy with the system so far.

However after having compiled a new kernel, everything changed.

With any kernel compiled on my system later than 2.6.12 the system is _extremely_ slow almost to the point of being unusable. In X opening the system resource overview takes two minutes and the overview - when finally opened - uses 60% of the cpu!
After a few unsuccessful tries I loaded the config from /boot and tried to compile with this - same problem!
Is it just the kernel that is so slow or is there an option that I should have disabled with the new kernel.
Any help would be much appreciated since it's driving me crazy. 

Cheers
Che


System:
AMD Turion 64
512 MB RAM
80 GB IDE HDD

Using Ubuntu 5.10 with kernel 2.6.14-9-amd64-generic.

---

### Post by dermotti on 2006-03-20
Why dont you just use one of the Ubuntu kernels instead of compiling your own?

If you must compile your own, i used this guide and it worked out very well.


[http://www.ubuntuforums.org/showthread.php?t=84174&highlight=kernel](http://www.ubuntuforums.org/showthread.php?t=84174&highlight=kernel)

---

### Post by leche on 2006-03-20
Hi, 
thanks for the quick reply.

I need some functions that are new since the .14 release of the 2.6 kernel. 

Anyway, I just found out that it apparently applies to ANY kernel I compile on my machine - even if I take the 2.6.12.6 sources and compile them on my laptop it is ridiculously slow!

Any ideas? :)
I am lost... *scratching head*

Thanks
Che

---

### Post by dermotti on 2006-03-20
You could get it from the dapper repositories....but you may have some issues with udev...

---

### Post by leche on 2006-03-21
Hey dermotti,

wow, that was brief! ;)
I get it you mean that udev is causing the slowdown? That is dynamic /dev, right?
Hmm, I'll compile without and see what happens. Probably I just uncheck CONFIG_HOTPLUG or something, right? I'll see.
Anyhow, des Ubuntu generic kernel not use udev? Cause with their standard kernel everything runs smoothly.

Cheers
Che

P.S.: Just to see what happens I also followed the man you linked. Kernel is slow. :(

---

### Post by leche on 2006-03-21
Hey dermotti,

thanks alot for the help - I figured it out!
It is what I thought but could not find confirmation for anywhere on the web: something was wrong with the system clock. Apparently ACPI messes around with the hardware. 
Anyway, by giving two kernel args (noapictimer and noirq for apic) the system runs smoothly now. *happy*

Thanks again
Che

---

