---
title: "Wanna reinstall"
date: 2006-04-03
forum: General Help
---

### Post by Duo Maxwell on 2006-04-03
Ok, I've messed up a few thing and figured I'm best off starting off with a fresh install of the OS again. 1.) can I reinstall ubuntu without reformatting 2.) how long till the next version is out? 3.) is there  a benefit to installing the 686 and whatnot versions of the stuff as well as replacing the 386 ones installed by the ubuntu installer? I had heard that the 686 versions would be faster on my machine.

---

### Post by taurus on 2006-04-03
1.  Yes, BUT why would you want to do that!  Since you've messed it up, format it so you would have a clean system!!!

2.  June 1st.

3.  Not much faster between kernel i386 & i686...

---

### Post by Darkriser on 2006-04-03
1) you'll probably loose data on your / partition
2) june 2006 - check "Dapper release" for more info
3) it may be little faster, so go for it ;)

---

### Post by az on 2006-04-03
[QUOTE=Duo Maxwell]Ok, I've messed up a few thing and figured I'm best off starting off with a fresh install of the OS again. .[/QUOTE]
You would be surprised to know how easy it is to fix most broken things in ubuntu.

[QUOTE=Duo Maxwell]
1.) can I reinstall ubuntu without reformatting .[/QUOTE]

No.  Well, yes, but no.  You want to keep your home files?  Just back them up.  It is far easier to do that than to create a seperate home partition.

You could delete everything in your / directory except your home directory (using a live cd) and then install, use manual partitioning and install onto an "unclean' target, but I have not done this.

[QUOTE=Duo Maxwell]
2.) how long till the next version is out? .[/QUOTE]

8 weeks.  You can always install now and dist-upgrade without losing any data.

[QUOTE=Duo Maxwell]
3.) is there  a benefit to installing the 686 and whatnot versions of the stuff as well as replacing the 386 ones installed by the ubuntu installer? I had heard that the 686 versions would be faster on my machine.[/QUOTE]

If you are running a pentium or celeron processor, use the 686 kernel.  If you are running an AMD processor, use the k7 kernel.  That's it.  There are no other packages to change.

So, once installed, install the linux-686 package and remove the linux-386 package.  The next time you boot, you will be using the 686 kernel.  It's more efficient and you really notice the difference on lower-powered hardware (like less than one GHz)

---

### Post by Duo Maxwell on 2006-04-03
Why I wanna do it? I still don't know what all I'm doing in linux, I installed some stuff, toyed with some settings and now things like nautilus don't work right anymore. The stuff I did tho I suspect is stuff that your average newbie would ever try, I gotta try breaking out of the windows or OS X way more...

---

### Post by az on 2006-04-03
[QUOTE=Duo Maxwell]Why I wanna do it? I still don't know what all I'm doing in linux, I installed some stuff, toyed with some settings and now things like nautilus don't work right anymore. The stuff I did tho I suspect is stuff that your average newbie would ever try, I gotta try breaking out of the windows or OS X way more...[/QUOTE]

So you want to wipe it clean and reinstall, then.  You can reformat your linux parition without borking the rest of the disk, of course.

---

### Post by superchar42 on 2006-04-03
The way I started learning was screw up, reinstall. When you're first learning, make sure everything important is kept on some sort of external source, whether you burn it to CD or keep it on a thumb drive. 
Make note of what you did when you screwed it up though, because though it was stated that most things are fixable, when you're still a newbie (like me!) then it's a lot easier to just try again. But don't do that mistake again. :D

---

