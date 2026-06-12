---
title: "Installing packages from anothe PC? (instead of Via repos)"
date: 2010-02-04
forum: General Help
---

### Post by mahela007 on 2010-02-04
is it possible to install programs present on one computer on another computer by transferring package files? For example, let's say I've installed Thunderbird on one Ubuntu machine. Would I be able to install thunderbird on another computer by copying some files from the first computer?

---

### Post by oldfred on 2010-02-04
I would look at aptonCD:

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by gmargo on 2010-02-04
If you still have the _.deb_ file that your application was installed from, you could copy that file over and install it with **dpkg**.  The _.deb_ files are saved in **/var/cache/apt/archives** so you can check there, although they might have been purged after installation.

I would highly recommend installing **approx**, which is a caching proxy for Debian packages.  Install it on just one of your machines (if you have multiple), and then configure all machines to download packages through it.  Then when machine 2 requests something that machine 1 has already downloaded, it gets the cached copy and does not re-download from the net.

---

### Post by mahela007 on 2010-02-05
> **gmargo said:**
> If you still have the _.deb_ file that your application was installed from, you could copy that file over and install it with **dpkg**.  The _.deb_ files are saved in **/var/cache/apt/archives** so you can check there, although they might have been purged after installation.

I would highly recommend installing **approx**, which is a caching proxy for Debian packages.  Install it on just one of your machines (if you have multiple), and then configure all machines to download packages through it.  Then when machine 2 requests something that machine 1 has already downloaded, it gets the cached copy and does not re-download from the net.

Interesting... I'll try that and the option in the previous post as well.

---

