---
title: "Compiling Source Code?"
date: 2011-06-05
forum: General Help
---

### Post by JoeAdamsIV on 2011-06-05
Hey everyone, long time Windows user here. Just switched over to Ubuntu 11.04 32bit. I have spent the day configuring it to my likings, and am content with Ubuntu. I have zero experience with coding, and bare minimum knowledge. Anyways, I have gotten some tar.gz files, that I have extracted them into folders, and then in terminal I run ./configure, and then I get the error "You need intltool 0.40.0 or later". What can I do to fix this? Thanks

---

### Post by raja.genupula on 2011-06-05
man this can help you
read this 
[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete)

---

### Post by Topsiho on 2011-06-05
You can install intltool from Synaptic. Same for most missing utilities.
But for compiling you can best install everything necessary in one move: install build-essential.

When installing a tar.gz file you can best first unpack it, and find a READ.me file or something like that, to see whether there are instructions for how to install.

Last: when it's possible, you better install from the repositories, it is much safer, unless you read all the source code (and understand it, which I doubt :) ). Otherwise you might wind up having malware on your computer, just as in Windows when you install programs that you shouldn't have trusted (such as most Windows users do :) ).
However, in the repositories you'll not always find the newest version of an application, and if you really need that, you'll be forced to install from such as a tar.gz file.

You'll have to find information about:

How to unpack a tarball (tar.gz file)
How to install from a tarball (use google)

And if you succeed that's a little triumph!

Topsiho

---

