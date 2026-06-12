---
title: "Is there any difference between compiling and pre-compiled programs?"
date: 2012-07-11
forum: General Help
---

### Post by Wiking on 2012-07-11
Is one better than the other? Differences in performance?

---

### Post by CLCressman on 2012-07-11
My experience is that it is a hassle chasing down all the *[FONT=Courier New]-dev[/FONT]* versions of the libraries that you need for compiling. The advantage of compiling is that you can sometimes get a later version or a program not in any repository. The disadvantage of compiling is that you have to download and recompile any updates manually. You can sometimes find a ppa that has just what you want, without the hassle of compiling from source. Just my $.02

---

### Post by SeijiSensei on 2012-07-11
The typical reasons for rolling your own is if the released binary wasn't compiled with some option that you need, or you need a feature that was added to a more recent version of the program than the one in the repositories.

The drawback, and it's a big one, is that anything you compile from source will not be automatically updated in the event there are security patches or new features.

The overall answer to your question is to stick with the binary releases in the repositories unless you have a specific need to compile your own version.

> **CLCressman said:**
> My experience is that it is a hassle chasing down all the *[FONT=Courier New]-dev[/FONT]* versions of the libraries that you need for compiling.

Apt will do this for you in many cases.  Use the command

```
sudo apt-get build-dep packagename
```

and it will determine the -dev dependencies and install them for you.  It makes compiling something like mplayer with perhaps two dozen dependencies a whole lot easier.

---

