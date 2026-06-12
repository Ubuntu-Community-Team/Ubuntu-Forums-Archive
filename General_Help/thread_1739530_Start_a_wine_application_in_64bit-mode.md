---
title: "Start a wine application in 64bit-mode"
date: 2011-04-26
forum: General Help
---

### Post by b166er on 2011-04-26
Hi

I have small problem.

I want to install a 64bit-only application in my wine.
But every time i try to load the installer it says that it only works on a 64bit-system.

Iv'e tried the 32-version of the app and it works fine.
I heard that since version 1.2 wine is able to support 64bits.

But how do I force wine to load an app in 64bit-mode?

I'm guessing there is an option to the wine command or something. But what is it? can't find anything in the man-page. 
And a google on the subject only brings up old posts from people who are trying to install wine in 64bit-ubuntu...

---

### Post by Mark Phelps on 2011-04-26
Know of no way to force the installation of a 64-bit app on a 32-bit OS.

---

### Post by b166er on 2011-04-26
Ok, but that's not what I'm trying to do.

To install a 64bit app on a 32bit os wouldn't be possible or usable.


But I don't have a 32bit OS. I'm running ubuntu-amd-64 and nowadays wine can run 64bit apps.


But I think the installer-program is a 32bit program that probes the system and checks if it's running on 32bit or 64bits.

Wine is both, but it tells the 32bit-app that it is running on a 32bit system...

So I need a way of telling wine to act as if it is a regulair 64bit-windows.

---

