---
title: "cannot use libpcap (broken?)"
date: 2010-10-30
forum: General Help
---

### Post by RainerZA on 2010-10-30
Hi I'm new to Linux.
I am trying to compile a piece of code but it keeps telling me when I type ./configure 

configure: WARNING: Compiling without libpcap support.
configure: error: Could not find working libpcap.

how can I fix it?
I tried installing other versions of libpcap from the .tar.gz files but when I try and compile that I get a boatload of errors in the grammar file.

help much appreciated!

---

### Post by P4man on 2010-10-30
To compile anything you need build-essential. If you havent already run:

```
sudo apt-get install build-essential
```

If that doesnt help, have a look in synaptic package manager, you probably need libpcap-dev. There might be other dependencies too. What are you trying to compile?

---

### Post by RainerZA on 2010-10-31
TY! getting libpcap-dev worked! didn't know I had to search with the -dev appendix when searching for lib files.
I was trying to compile and install kismet in order to track some information.

THANKS AGAIN!

---

### Post by P4man on 2010-10-31
you need the dev packages only if you are compiling stuff.

---

