---
title: "Firefox Problems..."
date: 2009-12-15
forum: General Help
---

### Post by N8JDR-HAM on 2009-12-15
Okay, I installed Ubuntu just recently (maybe a month ago) and it's been running very smoothly on my PC (got a virus in Windows, and didn't have the time or money to deal with it, so I installed Ubuntu, moved the un-corrupted files from the Windows partition, then deleted the windows partition (VISTA ... yuk) and am now running dual-boot Ubuntu 9.10/Windows 98). That was, until some upgrade or extention or something in Firefox went bad, and now am unable to fix it myself.

What I've tried (and what happened)
1) Uninstalling Firefox with Ubuntu Software Center - seemed to have deleted the files, - reinstalled, still non-functional.
2) Uninstalling using "sudo rm firefox" using Terminal - got the reply "no such file or directory 'firefox'".
3) Uninstalling using "sudo rmdir firefox" - still no such file or directory
4) Searched the computer for firefox (considering I have over 1TB of data, it took some time) and finally found it under usr-bin- and then used sudo rm and sudo rmdir, even -f, -i, -r, and just about everything else I could come up with. Empty handed.
5) Tried manually deleting (click on folder, click delete) and no permissions (I'm the administrator). Then I read that you can't delete the folder unless the files are already deleted, tried that, no avail.
6) Tried "sudo ps axjf | grep firefox" and got the following (I'll leave this for someone who knows what half of this means - still an old DOS Command Line user, but this is entirely different, so idk):
   4622  4716  4715  4622 pts/0     4715 S+    1000   0:00      \_ grep --color=auto
 to **[COLOR="Red"]firefox[/COLOR]**

Thanks all, I've exhausted everything I can think of on this. btw - the initial problem that led to all of this is when I click on the firefox icon, you get the "loading" mouse icon (circle thing moving around ... yeah, very technical I know) and then nothing happens.

 - N8JDR / Jake

---

### Post by spiderbatdad on 2009-12-15
System>>Administration>>Synaptic Package Manger
Use this utility for adding removing programs, in general. You normally wouldnt sudo rm individual system program files, but if you did, you would need a complet path sudo rm -f /usr/bin/firefox and so on.. But it looks like you might have other problems.
You can delete root owned files ( a great way to totally break your system) by launching the file browser as root...gksu nautilus

---

### Post by Dennis N on 2009-12-15
Find Firefox package in Synaptic Package Manager

Usually: System > Administration > Synaptic Package Manager

Right Click on Installed Firefox Package and select Mark for Complete Removal. Click on Apply, then again in the confirmation dialog.

That will remove all configuration files as well as the package.

Note: rm will not uninstall anything; it deletes a file or folder.

---

### Post by N8JDR-HAM on 2009-12-15
Well, tried running synaptic package manager, still no luck. Acts like it's going to run firefox (once again, loading thingy...) and then nothing. (Firefox 3.0 installed)

Thanks for the suggestions...

---

### Post by spiderbatdad on 2009-12-15
sorry to hear this. it sounds like something fundamentally wrong with the upgrade or whatever started these problems. It can be very difficult to diagnose...like a critical lib got deleted...who knows? As your installation is so new, perhaps it would be better to re-install...a dirty word around here sometimes. It could save hours of work, but you wouldnt learn nothin.

---

### Post by N8JDR-HAM on 2009-12-15
Yeah, my fear is the data. If I re-install ubuntu, how to save 1TB stored on the internal HD (I had it on an ext. I was using with my laptop, but the laptop died - 10 yrs old - and then two weeks after I got the desktop the HD went, and the last copy of files is on the comp.)

Does ubuntu save the data? Any ideas of what could've done this? How to avoid it?

---

### Post by spiderbatdad on 2009-12-15
I haven't seen this problem just spring up the way you described, unless the upgrade was interrupted. My thought was with all the sudo rm -abcdefg you broke something. :) How about burning a copy of gparted live and using it to prepare a partition for you to do a fresh installation. Access your data as a mount point?

---

### Post by N8JDR-HAM on 2009-12-15
possibly.

I imported Vista as a mount ...
Imported my first copy of Linux (8.06) as a mount ... (roommate corrupted some of the boot files while messing with it; last time I ever leave it logged in while I go get some water)
Now a third ... idk. But at the same time, it'll take one heckuva HD to copy all these files. Might just take this one to a comp programmer friend of mine, he still owes me a favor or a half-dozen for stuff I've done for him. Have him figure this mess out... lol.

---

### Post by hawthornso23 on 2009-12-15
> **N8JDR-HAM said:**
> Well, tried running synaptic package manager, still no luck. Acts like it's going to run firefox (once again, loading thingy...) and then nothing. (Firefox 3.0 installed)

Thanks for the suggestions...

Check you've got the right version of firefox in synaptic. The version installed with karmic is usually 3.5, but 3.0 is also available. You might be trying to fix the wrong version. In synaptic do a search for firefox.

---

### Post by N8JDR-HAM on 2009-12-15
It worked, wiped out all firefox references. I re-installed (only one version, no updates, no extensions, etc.) and it still doesn't work. Even tried running it in safe mode, same deal.

---

