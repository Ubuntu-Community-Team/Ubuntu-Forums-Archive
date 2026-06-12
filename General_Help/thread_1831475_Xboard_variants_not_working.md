---
title: "Xboard variants not working"
date: 2011-08-23
forum: General Help
---

### Post by Khelben Arunsun on 2011-08-23
I know xboard supports variants, so how do I get the variants to work?

I've gone to file > New Variant and no matter what I select, I always seem to get:

Variant (NAME) is not supported by Fairy-Max 4.8.0

I remember installing xboard, not Fairy-Max? What's going on here?!

Any Help would be much appreciated.

---

### Post by gmargo on 2011-08-24
**xboard(1)** is the display program; it doesn't play chess itself, but instead starts a "chess engine" in the background to do all the real thinking.  The default chess engine is **fairymax(6)**.

I took a look at the fairymax source and found the problem to be an uninitialized variable that just happened to contain the one value that breaks the code.

Ubuntu releases 10.04 Lucid, 11.10 Maverick, and 11.04 Natty all use the same version of fairymax (4.8o) with this bug, while 11.10 Oneiric's version (4.8q) is updated and does not have the bug.

You could download the Oneiric version and compile for your particular Ubuntu version.

Or if you want to patch the distributed fairymax code, here is a one-line change that fixes the problem.  This is against the 4.8o-1 version on Lucid/Maverick/Natty:
```

--- fairymax.c.00       2010-01-22 08:50:50.000000000 -0800
+++ fairymax.c  2011-08-23 16:07:26.086949202 -0700
@@ -388,7 +388,7 @@
                                          
 void PrintVariants()
 {
-        int i, j, count=0; char c, buf[80];
+        int i, j, count=0; char c=0, buf[80];
         FILE *f;
 
         f = fopen(INI_FILE, "r");

```

---

### Post by Khelben Arunsun on 2011-08-25
Nice! Thanks for the reply. I'll alien the 4.8q version.

---

### Post by rulet on 2011-10-21
Xboard doesn't start with installed crafty engine. Any ideas how to fix it?
Ubuntu 11.10

 ... I've deleted crafty package and installed it again. Xboard now starts, but I don't see crafty engine in the list of xboard menu.
How to add crafty engine to xboard?
And by the way glchess crashes after of some time running(both in in 2D and 3D modes). i just whant to add glchess pictures to xboard :)

---

