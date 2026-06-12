---
title: "Kernel Package Name Too Long"
date: 2010-01-21
forum: General Help
---

### Post by carlexpc on 2010-01-21
I've been compiling customized kernel packages for ubuntu and I've noticed that the final debian package output from running the command:

*# fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers *


returns a couple of packages with a very long package name which looks similar to this:

[I]linux-headers-2.6.32.1-custom_2.6.32.1-custom-10.00.Custom_i386.deb
linux-image-2.6.32.1-custom_2.6.32.1-custom-10.00.Custom_i386.deb[/I]


Is there a way or a workaround to reduce the filename length to a shorter format? Any help is greatly appreciated.

---

### Post by jamesisin on 2010-01-21
I guess you could use bash scripting to parse those file names into variables (presumably shortly names variables) and then use those variables instead.  Is that the sort of thing you were thinking of?

---

### Post by carlexpc on 2010-01-21
> **jamesisin said:**
> I guess you could use bash scripting to parse those file names into variables (presumably shortly names variables) and then use those variables instead.  Is that the sort of thing you were thinking of?

What I would like to achieve is a debian package with a shorter name like
***linux-headers-2.6.32.1-custom_i386.deb***

I haven't tried renaming the package to the format I want because I am afraid that I could experience problem installing/uninstalling the package from my system.

---

### Post by jamesisin on 2010-01-21
This is how I understand it.  The package itself (the .deb) will not refer to itself (as xxxxxxx.deb) during the installation process.  This part seems obvious enough.  Once it is installed any other package that might be looking for your new package will NOT be looking for xxxxxxx.deb but will be seeking whatever it was that this installer actually installed.

In short, my take would be that you can name your file a.deb and not encounter problems.

(Unless you are using something which specifically calls the xxxxxxx.deb package installer.  But in that case I would think that would be a script you yourself wrote and could thus change.)

---

