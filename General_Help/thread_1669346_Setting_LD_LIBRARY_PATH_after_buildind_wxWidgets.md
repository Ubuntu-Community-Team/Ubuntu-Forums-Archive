---
title: "Setting LD_LIBRARY_PATH after buildind wxWidgets"
date: 2011-01-17
forum: General Help
---

### Post by bruno9779 on 2011-01-17
Hi, I have been trying to compile Rigs of Rods.

There is a true dependency hell, many libraries need to be compiled by hand. I am almost at the end of it and I got stuck.

After compiling wxWidgets 2.9.1 I am asked to set the LD_LIBRARY_PATH to find the newly compiled libraries:

```
The installation of wxWidgets is finished.  On certain
 platforms (e.g. Linux) you'll now have to run ldconfig
 if you installed a shared library and also modify the
 LD_LIBRARY_PATH (or equivalent) environment variable.
 
 wxWidgets comes with no guarantees and doesn't claim
 to be suitable for any purpose.
 

```

Since [this bug ]("https://edge.launchpad.net/ubuntu/+bug/366728") is still active, all the documentation I can find isn't pertinent and I don't seem to understand the steps taken in the workarounds proposed

Thanks

---

### Post by sohail_linux on 2011-01-17
jsut run , ldconfig as root . You may not need to modify LD_LIBRARY_PATH is libraries are installed on default path.

---

### Post by bruno9779 on 2011-01-19
It worked, thanks.
I wasn't running it as root.

---

