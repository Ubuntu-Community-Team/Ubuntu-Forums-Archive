---
title: "Suspend and Hibernate in 10.10"
date: 2011-02-14
forum: General Help
---

### Post by Miltnoid on 2011-02-14
Hey guys, relatively new Linux user on a laptop, and I'm loving it!

However, there does seem to be one problem I (and from Google searching, many others), keep running into.  I'm having issues with Suspend and Hibernate.

From my Google searches, I learned that what most people do is they download uswsusp, and utilize the s2disk and s2ram programs.

However, my s2disk and s2ram programs aren't working as intended.

When I sudo s2disk, my computer stalls for a second or so, and then finishes and starts a new command line.  At that point, my mouse is frozen until I click a button or key, at which point the computer behaves as usual.  My computer doesn't shut down.

When I sudo s2ram, I get the output:
"Machine is unknown.
This machine can be identified by:
    sys_vendor   = "LENOVO"
    sys_product  = "2768VEJ"
    sys_version  = "ThinkPad T400"
    bios_version = "7UET66WW (2.16 )"
See [http://suspend.sf.net/s2ram-support.html](http://suspend.sf.net/s2ram-support.html) for details.

If you report a problem, please include the complete output above."

When I sudo s2ram -f, I get the output:
"Switching from vt7 to vt1
fbcon fb0 state 1
fbcon fb1 state 1
s2ram_do: Input/output error
fbcon fb0 state 0
fbcon fb1 state 1
switching back to vt7"

I'm using Ubuntu 10.10 64 bit on a Lenovo T400 Laptop.  I don't really care about suspend as much as I do hibernate, but if you guys had ideas about either, that would be greatly appreciated!

-Miltnoid

---

