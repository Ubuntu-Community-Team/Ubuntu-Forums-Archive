---
title: "rc.local, autorun graphics application at startup"
date: 2011-02-08
forum: General Help
---

### Post by sunruh on 2011-02-08
I have an embedded PC104 application where I am trying to get my program to start automatically at power up. The program contains a graphical user interface, using an old SVGALIB (no longer supported). It works fine if I start it after log in.
 
But when I put the path in rc.local, it will only run if I disable all the graphical stuff. The program bunts if it looks ahead and sees the call to vga_setmode(), where I set it for 480 x 640 resolution.
 
If anyone has any ideas, I would really love it! I'm getting nowhere with this!

---

### Post by dcstar on 2011-02-08
> **sunruh said:**
> I have an embedded PC104 application where I am trying to get my program to start automatically at power up. The program contains a graphical user interface, using an old SVGALIB (no longer supported). It works fine if I start it after log in.
 
But when I put the path in rc.local, it will only run if I disable all the graphical stuff. The program bunts if it looks ahead and sees the call to vga_setmode(), where I set it for 480 x 640 resolution.
 
If anyone has any ideas, I would really love it! I'm getting nowhere with this!

Anything run at the base system level (cron, rc.local) that uses the X system must have a "DISPLAY=" variable set to specify that actual output device. You can search out examples in crontab entries on the net.

When you later run things in a graphical login shell it already has that information.

---

### Post by sunruh on 2011-02-10
[FONT=Times New Roman][SIZE=5]Thanks, David.  I will search for examples.  I am not using the X system for my graphics.  I am using an older library called SVGALIB, which displays a 640 x 480 x 256 color format.  Unfortunately, it is no longer supported, but was integrated into my software from 10 years ago.  Does that change anything?[/SIZE][/FONT]

---

### Post by sunruh on 2011-03-15
David, I looked up the crontab examples, and that file is used to run tasks periodically in the background.  This seems to be different that what I am trying to accomplish.  Can you expound a little more?

---

