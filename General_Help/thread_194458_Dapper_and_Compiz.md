---
title: "Dapper and Compiz"
date: 2006-06-11
forum: General Help
---

### Post by veelivar on 2006-06-11
Hello All,

I hope this is not too stupid a question(s).

I've just noticed that Dapper has been released so I'm downloading the install cd to get it nice and fresh.  (my current install is pretty messed up so it's probably cleaner to start again)  so here are my questions.

Is compix and xgl part of Dapper? Or do I need to jum through all the hoopes to get in installed again?  If so what is currently the best guide to follow?

Also with the change in license is Sun's Java now part of the standard install? or if not  what is the best guide to fololw to install it? diito with Netbeans. 

Thanks in advance,
Dan.

---

### Post by Aurelias on 2006-06-11
> Is compix and xgl part of Dapper?
Nope, not really.  I'd recommend the [ubuntu wiki article]("https://wiki.ubuntu.com/XglHowto") on getting that to work.

> Also with the change in license is Sun's Java now part of the standard install? or if not what is the best guide to fololw to install it? diito with Netbeans.
I don't think they're included, although I haven't done a full reinstall yet.  I like to download the binaries straight from sun's website (java.sun.com) and unpack them inside /usr/local/, then make symlinks (ln -s /path/to/original/file linkname)in /usr/bin for java, jar, and whatever other binaries you'll need.  As for netbeans, I've never used it, but it could probably be installed the same way.

Hope some of that's useful,
Aurelias

---

### Post by psb6m on 2006-06-11
As to Sun Java, It is now (because of favorable licensing changes) in the Multiverse repository. Current version is 1.5.0. To my mind, there are many advantages to using the version in the repository.

---

### Post by yteh on 2006-06-11
For xgl/compiz, you can use the following link (it's also in the sticky for General Support): [http://www.ubuntuforums.org/showthread.php?t=148351](http://www.ubuntuforums.org/showthread.php?t=148351)

I've used the HowTo on both gnome and kde. Worked well for me.

---

