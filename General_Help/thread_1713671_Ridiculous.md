---
title: "Ridiculous"
date: 2011-03-24
forum: General Help
---

### Post by nkae100 on 2011-03-24
So I goto compile a program... I use the ./configure command and eventualy come to a stop with the following error:

[QUOTE]configure: error: *** zlib.h missing - please install first or check config.log ***

... ok, so I view config.log and what do I get 4870 lines of code.

What exactly I am suppose to be looking for?

This is why Windows users cannot be bothered with Linux - 'assume user knows everything'.

---

### Post by nothingspecial on 2011-03-24
> **nkae100 said:**
> configure: error: *** zlib.h missing - please install first or check config.log ***

Have you installed the required zlib package?

Did you read the README

Have you installed all the dependencies?

We have package managers so you don't have to compile.

---

### Post by nkae100 on 2011-03-24
Then why did you say "we"?

No, I told me to read config.log, not README.

---

### Post by nothingspecial on 2011-03-24
Then read the README, what does it say?

They are not my packages, and they are rarely modified.

---

### Post by uRock on 2011-03-24
> **nkae100 said:**
> Your packages are usually modified versions of the software. I want the original.
Download and install zlib or install the version in the repo which has been modified to work with the system.

For better help, it would be good if you stated what exactly you are trying to install. A subject relevant title is helpful as well.

---

### Post by nkae100 on 2011-03-24
Sorry dude, I just wrote over my previous thread with an edit.

I've carked it I'm off to bed.

Mod please delete this post.

---

### Post by nothingspecial on 2011-03-24
> **nkae100 said:**
> Then why did you say "we"?

No, I told me to read config.log, not README.

I meant you and me and everybody who uses linux (with a package manager)

In the folder you extracted there should be a README file (sometimes INSTALL).

Read it.

---

### Post by SeijiSensei on 2011-03-24
> **nkae100 said:**
> This is why Windows users cannot be bothered with Linux - 'assume user knows everything'.

Just out of curiosity, when was the last time you compiled and installed a package from source in Windows?  In all the years I ran DOS and Windows I never compiled anything.  Hell, I don't even think there were compilers I could have installed for free in Windows like gcc.

To me, the chance to install programs freely from source was one of Linux's stellar features.  The need to do so is certainly less today than when I started using Linux fifteen years ago, but I still compile the occasional obscure item from time to time, or compile more recent versions of things like PostgreSQL than are available in the repositories.  98% of the time or more, I just find what I need in the repos.

To me, the criticism you're making here is, to coin a term, "ridiculous."

---

### Post by matt_symes on 2011-03-24
Hi

> **nkae100 said:**
> This is why Windows users cannot be bothered with Linux - 'assume user knows everything'.

You can also compile programs under window if you know how and the emphasis is *if you know how*. I don't believe you know how under windows.

If you don't know how to compile a program under Linux then you can't complain if that program doesn't compile.

People here have already instructed you in what to install to compile the program.

Next time take a depth breath and post a support question that is not quite so aggressive or condescending.

We are here to help if we can.

Kind regards

---

### Post by tgalati4 on 2011-03-24
You generally need to install the headers for each package that your program is dependent on.

For instance:

apt-cache search zlib

Shows:


zlib1g - compression library - runtime
zlib1g-dbg - compression library - development
zlib1g-dev - compression library - development

You would need the dbg version if you are compiling your program with the debugger installed.  You need the -dev for each package that your program calls or is dependent on.  Reading through those 4800 lines will reveal what is missing.

Compiling code in linux is actually pretty easy.

Setting up a proper build environment for your code takes some skillz.

Since you don't mention the package that you are trying to build, I can't make any further suggestions.

And with 30,000 packages already built for Ubuntu, chances are someone has already built it.

---

### Post by SeijiSensei on 2011-03-24
> **tgalati4 said:**
> Setting up a proper build environment for your code takes some skillz.

Even that's not very hard if you're compiling a different version of a program already in the repositories.  The only thing I routinely compile (like once every few months or so) is mplayer.  I thought it would be hard to track down all the source dependencies until I read a posting about how to use "apt-get build-dep mplayer".  As someone who came from rpm/yum, build-dep makes compilation incredibly easy.

(There may be a comparable solution for yum these days; I haven't had to use it other than to update existing systems for quite some time now.)

---

