---
title: "Problems installing Emacs 23.1"
date: 2010-02-06
forum: General Help
---

### Post by AmadeusOK on 2010-02-06
Hi all,

I've been trying to install the latest version of Emacs from source but I'm running into a trouble. The commands "./configure" and "make" work just fine. However, when I run "sudo checkinstall" I get a message saying that makeinfo is missing:

```

makeinfo is missing - cannot build manuals
make: *** [info] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

```

What is Error 1? Any ideas about what to do? Your help will be greatly appreciated.

---

### Post by coldfusion1313 on 2010-02-06
Just go into the package manger and install it from there.

---

### Post by gmargo on 2010-02-06
The program named "**makeinfo**" is not installed.  You can use _[http://packages.ubuntu.com](http://packages.ubuntu.com)_ to search for the program: 

_[http://packages.ubuntu.com/search?searchon=contents&keywords=makeinfo&mode=exactfilename&suite=karmic&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=makeinfo&mode=exactfilename&suite=karmic&arch=any)_ 

shows that "**makeinfo**" is in the "**texinfo**" package, so install that.

OTOH, coldfusion1313 does have an excellent point: emacs-23.1 is available directly from the repository: [http://packages.ubuntu.com/karmic/emacs23](http://packages.ubuntu.com/karmic/emacs23)

---

### Post by AmadeusOK on 2010-02-06
Now Emacs is running on my laptop. That was easy. Thank you guys.

---

### Post by coldfusion1313 on 2010-02-06
time for the easy button!!!

---

