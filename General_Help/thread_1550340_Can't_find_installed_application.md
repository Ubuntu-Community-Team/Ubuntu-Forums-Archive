---
title: "Can't find installed application"
date: 2010-08-10
forum: General Help
---

### Post by freshtoast on 2010-08-10
I converted an .rpm to .deb with alien, then installed it. The software (serna) shows up as installed in Software Centre but I cannot find out *where* it is installed so that I can run it!

It doesn't show up in Applications, or /usr/bin, and I can't invoke it from Alt-F2.

Any help appreciated!

---

### Post by Vaphell on 2010-08-10
sudo updatedb && locate serna

---

### Post by Rubi1200 on 2010-08-10
Have you tried running it from the terminal?

Applications > Accessories > Terminal

then try serna or whereis serna might also help.

---

### Post by The Cog on 2010-08-11
If you can find the package in Synaptic Package Manager, right-click and choose Properties, you should be able to see a list of installed files. Look for something in /usr/bin, maybe /usr/local/bin - that would be the launcher executable that you run from the command line or from the manu editor.

---

### Post by t0p on 2010-08-11
Another suggestion: open terminal and type in

```

which sema

```

And another: type

```
man sema

```

to see if there's some other command required to run sema.

---

### Post by freshtoast on 2010-08-11
Thank you very much for the replies - it installed itself into a directory in /opt/!

:D

---

