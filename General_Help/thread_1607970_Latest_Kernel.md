---
title: "Latest Kernel?"
date: 2010-10-28
forum: General Help
---

### Post by mkris23 on 2010-10-28
Can someone tell me which is the latest stable kernel version available in the repositories?? Is it 2..6.35-22 ??? if so, when will 2.6.36 be available??

---

### Post by clhsharky on 2010-10-28
mkris23

Kernels are tied to releases, Ubuntu is not a rolling distro.
> Can someone tell me which is the latest stable kernel version available in the repositories??
Depended on the release your using.

What is the need for a fresher kernel?

Newer kernels can be installed, but not by normal updates and there are drivers issues sometimes.


Sharky

---

### Post by snowpine on 2010-10-28
You can always check at packages.ubuntu.com for example if you are using the current 10.10 Maverick release:

[http://packages.ubuntu.com/maverick/linux-generic](http://packages.ubuntu.com/maverick/linux-generic)

(The answer is, currently, 2.6.35.22.23, if you don't feel like clicking the link.)

Maverick will **never** give you kernel 2.6.36 through the official repositories, since Ubuntu is not a "rolling release" distro.

---

### Post by mkris23 on 2010-10-28
I'm running maverick. I've been having some problems with my CPU's hyperthreading which, according to the Linux Kernel Mailing Archives would be fixed in 2.6.36.

---

### Post by clhsharky on 2010-10-28
mkris23

Ubuntu patches there release kernels to fix issues.
Make sure you have the latest kernel from Ubuntu, if problem still exists please file bug report. Filing bug reports is important in the open source community, and they may give you a fix.

That said, can help you upgrade kernel if no resolution from launchpad.

Sharky

---

