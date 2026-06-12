---
title: "Epson ink levels in 12.04 anyone?"
date: 2012-07-10
forum: General Help
---

### Post by nikkkko on 2012-07-10
Hi,

If anyone out there has sucessfully managed to read ink levels for an Epson Stylus, (mine's a Photo P50), please could you put me out of my misery and let me know how you did it?

Thanks in advance...

---

### Post by ajgreeny on 2012-07-10
The only way that I found to show ink levels in my old, now dead stylus photo 830U was with mtink, available in the repos.  It looks as if there is a problem with that now in ubuntu versions 11.04, 11.10 and 12.04, but have a look at [http://ubuntuforums.org/showthread.php?t=1871321](http://ubuntuforums.org/showthread.php?t=1871321) and you may be able to get it working

Install it and then make sure you, as user, are in the lp group.  The first time you start it you will probably be told you don't have permission to connect to the printer, but if you try again after following the info in that other post it may work OK.

Good luck!!

---

### Post by nikkkko on 2012-07-11
Thanks for the quick reply - I managed to get it working.

I tried mtink
[LIST]
[*]added myself to the lp group
[*]commented out the blacklisting of usblp
[*]modprobed usblp
[*]launched mtink
[/LIST]
mtink ran without complaining, but all I got back after a long pause was a dialogue box saying it couldn't reach the printer.

Launched mtink using sudo and it works. Finally!

---

