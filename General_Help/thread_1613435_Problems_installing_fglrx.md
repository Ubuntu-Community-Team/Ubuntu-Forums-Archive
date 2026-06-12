---
title: "Problems installing fglrx"
date: 2010-11-04
forum: General Help
---

### Post by thezood on 2010-11-04
Is anyone else having problems installing fglrx? It seems the DKMS module fails to install. When searching for this error message, it appears there was a similar issue with fglrx in august but it should be fixed now. Has it reappeared or is it something with my installation?

I get a similar error when i try installing the binary from the ATI website.

```

Building initial module for 2.6.35-22-generic

Error! Bad return status for module build on kernel: 2.6.35-22-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.780/build/ for more information.

```

---

### Post by dcstar on 2010-11-04
> **thezood said:**
> Is anyone else having problems installing fglrx? It seems the DKMS module fails to install. When searching for this error message, it appears there was a similar issue with fglrx in august but it should be fixed now. Has it reappeared or is it something with my installation?

I get a similar error when i try installing the binary from the ATI website.

```

Building initial module for 2.6.35-22-generic

Error! Bad return status for module build on kernel: 2.6.35-22-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.780/build/ for more information.

```

Are you installing official Ubuntu kernels or others?

---

### Post by thezood on 2010-11-05
> **dcstar said:**
> Are you installing official Ubuntu kernels or others?

Not sure what you're asking here. As you can see in my post, I'm using 2.6.35-22-generic which is default in Maverick.

---

### Post by thezood on 2010-11-07
Installation worked with kernel 2.6.36-rc8. However, it should work with 2.6.35 too. Is noone else having this problem?

---

### Post by Yellow Pasque on 2010-11-07
> Consult the make.log in the build directory
The build can fail for various reasons. If you don't post the file in question, all we have to work on is a vague error message, and chances are that your issue will go unsolved...

---

### Post by thezood on 2010-11-08
Yeah, should have thought of that. I didn't find this bug report before but it seem to be a known issue: [https://bugs.launchpad.net/ubuntu/+source/dkms/+bug/641830](https://bugs.launchpad.net/ubuntu/+source/dkms/+bug/641830)
Weird that nothing has happened for several months though...

```

DKMS make.log for fglrx-8.780 for kernel 2.6.35-22-generic (x86_64)
mån  8 nov 2010 18.19.19 CET
AMD kernel module generator version 2.1
Error:
kernel includes at /lib/modules/2.6.35-22-generic/build/include do not match current kernel.
they are versioned as "2.6.35.4"
instead of "2.6.35-22-generic".
you might need to adjust your symlinks:
- /usr/include
- /usr/src/linux

```

---

### Post by thezood on 2010-11-12
I wonder if this is being worked on. Is anyone else experiencing this problem?

---

### Post by Square87 on 2010-11-14
> **thezood said:**
> I wonder if this is being worked on. Is anyone else experiencing this problem?

I have this problem, too. Kubuntu 10.10 with linux-image-2.6.35-22-generic
My make.log is the same.

---

### Post by Yellow Pasque on 2010-11-14
Install another kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/)
You need the image, headers-all, and headers-$arch packages

---

### Post by thezood on 2010-11-15
> **Temüjin said:**
> Install another kernel: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/)
You need the image, headers-all, and headers-$arch packages

I've already tried that and I got the same error message. As I understand it, fglrx had this problem in september but it was fixed for kernels .35 and .36 so if there's been a regression, it probably affects them both. However, I still don't know if everyone is affected by this or if it's just me and a few more.

EDIT: Shame on me, I must be drinking again... It actually works with kernel 2.6.36.

---

### Post by Yellow Pasque on 2010-11-15
> Shame on me, I must be drinking again...
No shame in that :)

> It actually works with kernel 2.6.36.
Yeah, the problem is with Ubuntu's packaging of that kernel. Patches for using Catalyst with newer kernels have been out.

---

