---
title: "packages not found??"
date: 2010-10-15
forum: General Help
---

### Post by srslynrdy on 2010-10-15
Hello everybody. First post

I have ubuntu 10.04 installed and i have manually installed some packages that the software manager does not find.

after installing these packages i ran the command
"dpkg --list | grep tcl"

it returns
```

ii mysqltcl 3.05-3 Interface to the MySQL database for the Tcl language
ii tcl 8.4.16-2 The Tool Command Language (default version) - run-time files
ii tcl8.4 8.4.19-4 Tcl (the Tool Command Language) v8.4 - run-time files
ii tcllib 1.12-dfsg-2 the Standard Tcl Library
ii tclx8.4 8.4.0-3 Extended Tcl (TclX) - shared library

```

now when i do "tclsh" and execute "package require tcl" it sais "cannot find package tcl"... it does this for all the above packages except the "mysqltcl".

can somebody please help?

thanks

---

### Post by srslynrdy on 2010-10-18
please anybody have any ideas? am i just doing things wrong or what??

---

### Post by matsuzine on 2010-10-18
Okay, I'm no tcl expert but I wonder if what you need is the tclx8.4-dev package?

From the little bit of information I found, it looks like that might be what's missing.

---

### Post by srslynrdy on 2010-10-18
thank you for replying.
i did a apt-get install for the dev package but it still is not finding the packages when i do the require.

another thing i noticed is whenever i run "tclsh" and do a "info patchlevel" it returns 8.5.9

but when i do "tclsh-default" and do "info patchlevel" it returns "8.4.19"

hmm...

---

