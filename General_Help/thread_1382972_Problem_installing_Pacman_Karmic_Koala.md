---
title: "Problem installing Pacman Karmic Koala"
date: 2010-01-16
forum: General Help
---

### Post by OldGoat58 on 2010-01-16
While trying to install Pacman from the Ubuntu Software Center the following error occurred.  Any help will be greatly appreciated.

Thanks!
Mike

Unpacking pacman (from .../pacman_10-17ubuntu1_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/pacman_10-17ubuntu1_i386.deb (--unpack): 
 trying to overwrite '/usr/share/man/man6/pacman.6.gz', which is also in package xscreensaver-data-extra 0:5.08-0ubuntu5 
Processing triggers for desktop-file-utils ... 
Processing triggers for man-db ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/pacman_10-17ubuntu1_i386.deb

---

### Post by rCXer on 2010-01-16
Do you have xscreensaver?  xscreensaver has a "Pacman" screen saver and its names might be conflicting with the game.  This is probably a bug.  I have no idea how to fix this though...

---

### Post by llamabr on 2010-01-16
what exactly did you type to get this error?

It's not a bug.  I suspect it's the way you called the command.

---

### Post by OldGoat58 on 2010-01-17
> **llamabr said:**
> what exactly did you type to get this error?

It's not a bug.  I suspect it's the way you called the command.

I didn't type anything.  I do have, and use, a Pacman screensaver that is part of an xscreensaver package I installed.  The reason I say I didn't type anything is that I navigated to Applications/Ubuntu Software Center/Games/Pacman and installed from there.

---

### Post by rCXer on 2010-01-17
After a bit of research I've found [this related bug report](https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/306740). The developers are working on fixing this. I posted a link to this thread.

---

### Post by OldGoat58 on 2010-01-18
> **rCXer said:**
> After a bit of research I've found [this related bug report]("https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/306740"). The developers are working on fixing this. I posted a link to this thread.


Thank you rCXer!  I forget to check Launchpad to see if what I experience is just me screwing things up like the other person suggested, or is in fact a legitimate problem.  This is why I love Ubuntu Linux, it's people helping people.

This brings up the question, do I mark the thread solved since the bug has been reported or leave it open??

Thanks!
Mike

---

### Post by rCXer on 2010-01-18
Not Yet.  Someone else on the forum might show up with a solution.

---

### Post by rifter on 2010-09-22
Unfortunately, even though there has been a fix for ages available (originally upstream from debian) and it is a very simple bug in the naming of one file in the xscreensaver package, for some reason the developers in their infinite wisdom never included this in any official karmic packages, and have marked [color=blue]_[the bug](https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/466701)_[/color] as fixed, supposedly in lucid.
It's severely stupid IMHO not to include a fix since all it takes is adding ONE CHARACTER to the package file.

---

