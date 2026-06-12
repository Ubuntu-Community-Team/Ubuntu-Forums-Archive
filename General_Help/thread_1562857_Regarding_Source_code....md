---
title: "Regarding Source code..."
date: 2010-08-28
forum: General Help
---

### Post by limestone on 2010-08-28
Hi, anyone know how to get dep for source code (not in Ubuntu)?
Do I have to look up and download all the deps manually on the internet?

---

### Post by GregBrannon on 2010-08-28
Can you be more specific or give an example?  What source code?

I doubt that there's one answer that'll cover all of the possibilities included in your question.  Then again, maybe I just don't understand the question.

---

### Post by limestone on 2010-08-28
> **GregBrannon said:**
> Can you be more specific or give an example?  What source code?

I doubt that there's one answer that'll cover all of the possibilities included in your question.  Then again, maybe I just don't understand the question.

When downloading source-tar-ball that need dependencies, where can I get it?
Do I have to search the web for each package?

---

### Post by jocko on 2010-08-28
> **pont.andersson said:**
> When downloading source-tar-ball that need dependencies, where can I get it?
Do I have to search the web for each package?
No. If you use ubuntu, you can get most things from the repos, including development headers for every library available in the repos.
For programs that are already in the repos, you can get the build-dependencies (= the development headers for the libraries the program depends on) by:
```
sudo apt-get build-dep *packagename*
```
For programs that are not in the repos, you can still get the build-dependencies from the repos. The development headers for a package is usually just the name of the normal package followed by the suffix "-dev", so if the program you need to build is dependent on libx11, just search for "libx11" in synaptics. You'll find a few packages, the one you would need in this example is named "libx11-dev".

---

### Post by amauk on 2010-08-28
This is what package managers were designed for

If you're getting source packages via a package manager, it can grab the dependencies for you as well

If you're not using a package manager, then you have to get the dependencies manually

---

### Post by jocko on 2010-08-28
> **amauk said:**
> If you're not using a package manager, then you have to get the dependencies manually
You can still get the dependencies from the package manager.

---

### Post by amauk on 2010-08-28
> **jocko said:**
> You can still get the dependencies from the package manager.but not automatically

To install all build dependencies for package foo, you can do```
sudo apt-get build-dep foo
```

but if you're not using the package manager then any dependencies will have to be installed manually

./configure
oops, missing dep1
sudo apt-get install dep1-dev

./configure
oops, missing dep2
sudo apt-get install dep2-dev

./configure
Yay

---

### Post by limestone on 2010-08-28
> **amauk said:**
> 

If you're not using a package manager, then you have to get the dependencies manually

That's what I'm after... Where can I get the dependencies if I'm NOT using a package-manager???

---

### Post by jocko on 2010-08-28
> **pont.andersson said:**
> That's what I'm after... Where can I get the dependencies if I'm NOT using a package-manager???
As I and others have already said: Even if you want to build something from source code that you have downloaded yourself, without the help of a package manager, you can usually still get all of the dependencies using the package manager. It just that the package manager can not get all dependencies automatically with *one* simple command.

I repeat what have already been said in slightly different words:
[COLOR=Blue]**A. **[/COLOR]If the source of the program you want to build is in the repos, you get ALL dependencies with ONE command (command 1):
```
sudo apt-get build-dep *packagename*
```[COLOR=Blue]**B. **[/COLOR]If the source of the program you want to build is NOT in the repos, **you still get the dependencies from the package manager**, you'll just have to tell it *exactly which* packages to install with a command like (command 2):```
sudo apt-get install *example1-dev example2-dev example3-dev* ....
```Or search for the packages in synaptic and install them from there.

[COLOR=Blue]**C. **[/COLOR]If the source of the program IS in the repos, but you download a newer version from the developer's web page, you can still get at least most of the dependencies with the one simple command (command 1), but there may of course have been some changes in what libraries are needed, so you may need to install one or a few more packages manually (command 2).

It sometimes happens that some things require some libraries that are newer than what is available in the repos, and it may even be possible (but highly unlikely) that you may stumble over a library which is not available from the repos at all in any form. In those very RARE cases you'll have to find the source code of that library yourself. Where to get it? From the developer of that specific library. Use google to find the specific project's webpage...

---

