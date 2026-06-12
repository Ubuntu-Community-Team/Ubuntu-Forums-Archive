---
title: "Updating latex packages"
date: 2011-07-05
forum: General Help
---

### Post by oldmankit on 2011-07-05
Hello,

I got some advice from the tex stack exchange, regarding hyper links, which turned out not to work.  I checked the version of the latex packager hyperref that I was using, and was shocked to see that it was a 2009 build.  The people who were advising me suggested I update.

I would like to update this package.  I've had a look at the options.  In the end the easiest was to download the package directly from CTAN, unpack it, run latex hyperref.ins, and then copy the files over and do sudo texhash.

So far so good.

But now when I try to use latex I get a new error:
```
LaTeX Warning: You have requested, on input line 102, version
               `2010/04/26' of package ltxcmds,
               but only version
               `2009/08/05 v1.0 Some LaTeX kernel commands for general use (HO)
'
               is available.
```

I can see myself updating that and then finding more and more packages that need updating.

I tried installing miktex-tools but got nowhere.  And then I read someone's advice that it's silly to use a windows port in linux.

My question: what should I do?  I need a more up-to-date version of hyperref, and I need latex to work, that's all.

---

### Post by oldmankit on 2011-07-11
My question rephrased:  How do I update latex packages properly?  Do I need some software like kyle?

The ones that have been installed by default by lyx are too out-of-date.

---

