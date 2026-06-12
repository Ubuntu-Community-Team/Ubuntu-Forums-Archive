---
title: "Installing program trouble"
date: 2012-01-26
forum: General Help
---

### Post by Keman on 2012-01-26
Hello, I'm relatively a linux novice.  I've worked on it before, and I can do the basics, but I'm far from experienced.  My issue is, I have a VPS server running with ubuntu-9.10-x86_64.  I do not have a GUI installed on it and manage it remotely.  Now, I need to install gcc to compile some programs, but I ran into a problem while trying to do so.  The RPM command does not work, like its not installed.  The only package with RPM I could find was a source file.   It requires gcc.  When I try to use yum, I get "ImportError: No module named rpm.  Not sure if that means it can't find the file, or RPM command isn't working.  I've tried apt-get update, apt-get upgrade, and many variations of apt-get install gcc with no success.
."  I'm lost >>;.

I do not have access to the linux disc, and I cannot find a precompiled RPM package, or a precompiled gcc package for my version of ubuntu....what are my options?

Thank you for your time.

---

### Post by Frogs Hair on 2012-01-26
Ubuntu uses Debian or .deb packages not RPM . I am not familiar server , so I don't where or if RPM packages are applicable . 

9.10 has reached end of life and its repositories are no longer available on line . If there are required dependencies for the program they would have to be installed manually .

---

### Post by Keman on 2012-01-26
....that would explain alot....thank you very much :).

---

