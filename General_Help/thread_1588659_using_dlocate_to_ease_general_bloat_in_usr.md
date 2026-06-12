---
title: "using dlocate to ease general bloat in /usr"
date: 2010-10-05
forum: General Help
---

### Post by Zenmij on 2010-10-05
Running Disk Analyzer recently, I noticed /usr had swelled to about 4.2gb (usr/lib coming in at 2.0Gb and /usr/share at 1.8)

Now after running dlocate, I am left with a long list of packages such as: libatspi (14 lines), libgail (6 lines), gstreamer0.10-plugins-ugly-dbg (20 lines), anjuta (45 lines) and so on ... 

Is there an easy way to find out if the packages are redundant from an old kernel or not so they can be removed? 


Many Thanks.

---

### Post by lloyd_b on 2010-10-05
> **Zenmij said:**
> Running Disk Analyzer recently, I noticed /usr had swelled to about 4.2gb (usr/lib coming in at 2.0Gb and /usr/share at 1.8)

Now after running dlocate, I am left with a long list of packages such as: libatspi (14 lines), libgail (6 lines), gstreamer0.10-plugins-ugly-dbg (20 lines), anjuta (45 lines) and so on ... 

Is there an easy way to find out if the packages are redundant from an old kernel or not so they can be removed? 


Many Thanks.

Install the package 'deborphan', and then run 'deborphan' at the command line.  This will give you a list of all packages you have installed that nothing else in the system depends on.

This will give you a list of candidate packages to remove.  Look through it, and make sure there's nothing in there that you know you use, then "sudo apt-get remove ..." those packages.

Then repeat the process - there may be other packages that depend on *those* packages.  Repeat the process until 'deborphan' lists no orphaned packages, or only packages you want to keep.

Lloyd B.

---

