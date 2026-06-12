---
title: "Install tar.bz2"
date: 2011-12-31
forum: General Help
---

### Post by shadowfax1 on 2011-12-31
Ran into this recursive error
Foomatic library directory '/usr/share/foomatic/db' is not writable!
make[4]: *** [install-kit] Error 2
make[4]: Leaving directory `/home/marco/gutenprint-5.2.7/src/foomatic'
make[3]: *** [install-data-local] Error 2
make[3]: Leaving directory `/home/marco/gutenprint-5.2.7/src/foomatic'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/marco/gutenprint-5.2.7/src/foomatic'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/marco/gutenprint-5.2.7/src'
make: *** [install-recursive] Error 1

Tried installing a different package....same thing?

---

### Post by Lars Noodén on 2011-12-31
In the tarball there was a file named README or INSTALL.  What did it have to say about the steps needed for installation?

---

### Post by shadowfax1 on 2011-12-31
The general procedure to build Gutenprint is as follows:

    ./configure [options]
    make
    make install

Did this but still got the recursive error..

---

### Post by crazy bird on 2011-12-31
Is the Gutenprint package not standard available in synaptic??

---

### Post by shadowfax1 on 2011-12-31
Yeah....found it in the repos and it gave me the option
in gimp.   Probably not the latest version but its way
better than the standard linux print interface..

Thankyou....both.
Happy New Year

---

### Post by crazy bird on 2011-12-31
Can you mark this thread as solved? Thanks!

---

### Post by MoreOrLess on 2011-12-31
> Foomatic library directory '/usr/share/foomatic/db' is not writable!
..sounds like a permissions error (i.e. you needed to use sudo).

---

