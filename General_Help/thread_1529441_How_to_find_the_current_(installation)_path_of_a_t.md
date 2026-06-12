---
title: "How to find the current (installation) path of a tool?"
date: 2010-07-12
forum: General Help
---

### Post by pstein on 2010-07-12
Assume I call a certain tool in terminal like
 
foobar -myoption
 
But
a) there exists more than one installation of "foobar" on the system
or
b) I don't know where "foobar" is installed.
 
How can I find out WHICH foobar resp. WHICH path belongs to the currently active foobar tool?
 
I prefer a cmdline command with option similar to:
 
findactivepath -tool=foobar
....
Output: Used location=/usr/bin/foobar
 
I don't want to dig around with PATH investigations by searching every PATH component. 
Furthermore I don't want to get recommendations and expectations like "normally tools are installed in...". Think of unusual installed software.
 
Is there a more convenient way to get the info?
 
Peter

---

### Post by wojox on 2010-07-12
Have you tried 

which foobar

or 

whereis foobar

Why would you need two separate instances of foobar installed?

---

