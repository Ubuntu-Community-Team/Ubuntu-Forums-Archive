---
title: "Determine when package was installed"
date: 2010-06-21
forum: General Help
---

### Post by Exp HP on 2010-06-21
**tl;dr version: **How can I determine when a package from the repository was installed?

** long version:**
I foolishly decided to use Ubuntu Software Center to install an application.  I thought it would be nice to actually have a screenshot for once; you never get to see those in aptitude.  But right about now I'm kicking myself for having used it, because I really need to know what other packages it installed for dependencies.

I'm uninstalling the program right now because it has some flaws that I know how to fix in the source; the program was written in Tk, which, lo and behold, is something I've been teaching myself the last week!
So I was *very* surprised to see **Tcl** and **Tk** listed under "Packages being removed because they are no longer used".  I find it hard to believe I did not already have these packages before getting this program... but I'm not sure.  The version of Tk in the repository is outdated, so I had to build many things from source.  Perhaps I never got these packages?

If they were installed to satisfy a dependency for this program, I must remove them, because they could conflict with the Tk setup I worked so hard to achieve.
If they were already installed, I must keep them, because they might be *integral* to that setup I worked so hard to achieve.

Can you see my dilemma? How can I tell when they were installed?

---

### Post by philinux on 2010-06-21
Open synaptic.

File>History.

sudo cat /var/log/apt/term.log

---

### Post by Exp HP on 2010-06-21
Thank you.  The history in Synaptic was incomplete, not including the current month.  The log file, on the other hand, contained everything, and it confirmed that the Tcl and Tk packages were indeed installed to satisfy dependencies for this program.  With that, I'm definitely going to uninstall them.

---

