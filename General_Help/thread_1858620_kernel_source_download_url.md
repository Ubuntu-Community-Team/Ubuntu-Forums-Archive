---
title: "kernel source download url"
date: 2011-10-12
forum: General Help
---

### Post by masuch on 2011-10-12
Hi,

Could please anybody tell some reliable (mirror) URL where I can download kernel source 3.0.6 except kernel.org or except using git ?

thanks,
m.

---

### Post by linuxman94 on 2011-10-12
Why don't you use kernel.org?  And the latest stable release is 3.0.4

---

### Post by masuch on 2011-10-12
that's not true.
The last stable kernel is 3.0.6,
which is not on kernel.org web page yet.

Actually it is on kernel.org , but on git:
[http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=summary](http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=summary)

---

### Post by WorMzy on 2011-10-12
[Linus' github]("https://github.com/torvalds/").

You don't have to use git; you can download the latest files as a [zipball]("https://github.com/torvalds/linux/zipball/master").


EDIT: Whoops, just realised you want stable. You used to be able to download that from git hub (as recently as last week), but for some reason you can't right now. Maybe Linus is about to move back to kernel.org.

---

### Post by masuch on 2011-10-13
> **WorMzy said:**
> [Linus' github]("https://github.com/torvalds/").

You don't have to use git; you can download the latest files as a [zipball]("https://github.com/torvalds/linux/zipball/master").


EDIT: Whoops, just realised you want stable. You used to be able to download that from git hub (as recently as last week), but for some reason you can't right now. Maybe Linus is about to move back to kernel.org.

It is pity that kernel source is not located in [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)... .

---

### Post by linuxman94 on 2011-10-13
Here's the git snapshot download of 3.0.6 stable:

[http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=snapshot;h=a004e0962a10dfa7fc83dfa4ed4109d1cf84124b;sf=tgz](http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=snapshot;h=a004e0962a10dfa7fc83dfa4ed4109d1cf84124b;sf=tgz)

---

### Post by masuch on 2011-10-14
> **linuxman94 said:**
> Here's the git snapshot download of 3.0.6 stable:

[http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=snapshot;h=a004e0962a10dfa7fc83dfa4ed4109d1cf84124b;sf=tgz](http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=snapshot;h=a004e0962a10dfa7fc83dfa4ed4109d1cf84124b;sf=tgz)

Thank you,
But, It is not answering my question. See #1.

---

### Post by masuch on 2011-10-19
to avoid download whole stable git:
git://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git linux-3.0.y

by going to:
[http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=summary](http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=summary)
Click on the "tree" link and then click on the "snapshot" link.
It will return a nice tar.gz snapshot of the tree, without the need to use git.

---

### Post by linuxman94 on 2011-10-19
> **masuch said:**
> to avoid download whole stable git:
git://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git linux-3.0.y

by going to:
[http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=summary](http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=summary)
Click on the "tree" link and then click on the "snapshot" link.
It will return a nice tar.gz snapshot of the tree, without the need to use git.

That's the exact same thing i linked, except i linked straight to the tar.gz snapshot file.

---

### Post by masuch on 2011-10-20
> **linuxman94 said:**
> That's the exact same thing i linked, except i linked straight to the tar.gz snapshot file.

Yes, I know. I just put it here because I found it on another forum ... how to get there by mouse clicking, no big deal :-)

(I am still interesting in another mirror for kernel source, if it exist ?-)

---

