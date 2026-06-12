---
title: "Installing a program into a single folder"
date: 2012-09-05
forum: General Help
---

### Post by battles on 2012-09-05
I installed mixmaster on Ubuntu and it ended up spewing the mixmaster files all over the computer.  Is there some way to force an installation to put all files into a single folder?  I am new to linux.  Thanks.

---

### Post by TheFu on 2012-09-05
Find the cached DEB package under /var and manually install it with **dpkg --instdir** option. Be certain to de-install any prior installation from the system **before** you start.  **I have never used this, so I do not know whether it actually works or not.**

If that doesn't work, you can grab the source code and read the installation instructions. If it uses "./configure", then you can set the install-prefix.

---

### Post by battles on 2012-09-07
Well, I am fairly new to linux and didn't have any success with instdir.  It did seem to try to install mixmaster, but couldn't finish for a number of diagnostic messages that I really didn't understand.  I couldn't find the mix deb anywhere, so I downloaded mix.  That might have been the problem.  I decided to search out all the mixmaster files and copy them to another folder.  I have not tried to execute it yet because I need to redo some of the config files.  I think your idea might have worked if I could have found the mix deb on ubuntu.  Thanks.

---

### Post by TheFu on 2012-09-07
When you had any failure, it would have been helpful if you posted the exact messages here.  Often those messages are easy to understand for others, but hard for someone new to Linux/UNIX. It takes a little time to understand them. I've been there too.

In Ubuntu, you really, really, really don't want to find .DEB files just anywhere and install them.  Ubuntu and Linux with a package manager isn't like MS-Windows. You want to always install only packages from the approved package manager when you are new.  

The "mix*.deb" file should be under /var/cache/apt/archives, unless you did a "clean."

This is still the easiest answer for your issue.

---

