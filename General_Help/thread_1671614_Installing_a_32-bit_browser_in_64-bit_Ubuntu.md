---
title: "Installing a 32-bit browser in 64-bit Ubuntu"
date: 2011-01-20
forum: General Help
---

### Post by mbidewel on 2011-01-20
Is there a way to install a 32-bit browser in 64-bit ubuntu?  My work uses the Juniper SSL VPN which requires 32-bit.  Most of the discussions I have seen either imply a 32-bit distro or the use of scripts which don't work in my case since host checker requires the browser.  

In Fedora I work around this by installing the 32-bit google chrome package, is there a way to do this in Ubuntu?

Thanks

---

### Post by yetiman64 on 2011-01-20
In short:      yes.
In my view:  it's nasty and messy -hope someone can suggest a better option.

I hope there is a way to do the job with ia32libs, if not you'll soon get to knows the ins and outs and sheer terror of chroots and bind mounting :P.

If you have a look at the attachment, the top browser with Google showing is 32bit chrooted, the bottom browser with your thread title in on UF is the 64bit browser.

The "System Properties" filesystem entries on the right show the bind mounting (including /home and storage directories) for the 32 bit chroot. Yes all of them showing are for the chroot :).

To run two browsers, who both happen to share the same .mozilla folder due to a bind mounted home partition, you will need to create/use separate firefox profiles. Particularly if you run them both at once.

Although the command shows dchroot being called the setup required for lucid is actually schroot in the background. Also the "--no-remote -P "32bit_FF""  is what specifically opens the 32bit firefox profile 32bit_FF.

To look into creating firefox profiles check out (in terminal),
```
firefox --no-remote -P
```& check attachment #2

It has been an extremely long and dangerous road setting up this chroot. Nearly nuked my whole data collection over several partitions and drives when I "rm"ed the chroot while the bind mounting was still in place. Yes it was a stupid move but sheer terror found the CTRL + C keys to break the rm (yes it was the full nasty one) command in time. Only lost the contents of the bind mounted fonts folder, but this cost me a re-install, I still haven't learnt to read everything in rectangular boxes. 

RESEARCH chroots CAREFULLY, they can bite. :wink:

Edit: OR consider a 32 bit ubuntu install with firefox in Virtualbox. Much easier/safer. Should have thought of that earlier :-)

---

### Post by pqwoerituytrueiwoq on 2011-01-20
not sure if it will install but
32bit dev build google chrome:
[http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb](http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb)


i have run a 32bit ff that i extracted from the .tar.bz2 archive i got om mozilla's site but a crap load of plugins will not work cause the plugins are 64bit
you could use it for this


wonder is the nspluginwrapper will work on Juniper SSL VPN
you know the dirty trick we used on flash before there were 64bit dev builds

---

### Post by pqwoerituytrueiwoq on 2011-01-20
dam forums are f-ing with me (duplicate)

---

### Post by pqwoerituytrueiwoq on 2011-01-20
dam forums are f-ing with me (duplicate)

---

### Post by mbidewel on 2011-01-20
> **pqwoerituytrueiwoq said:**
> not sure if it will install but
32bit dev build google chrome:
[http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb](http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb)


i have run a 32bit ff that i extracted from the .tar.bz2 archive i got om mozilla's site but a crap load of plugins will not work cause the plugins are 64bit
you could use it for this


wonder is the nspluginwrapper will work on Juniper SSL VPN
you know the dirty trick we used on flash before there were 64bit dev builds
I tried installing the package with dpkg and got an error on the package arch.

---

### Post by oldos2er on 2011-01-20
Try **sudo dpkg -i --force-architecture foo.deb**

---

