---
title: "-cp recursive but ignore some source"
date: 2010-07-04
forum: General Help
---

### Post by Gyrra on 2010-07-04
I'm still trying to learn, but seem to be hitting a few walls when it comes to man pages.
I don't know where else to look so I hope to get some help here - or at least another idea.

I'm trying to learn c++ as well as *nix terminal commands, and I like to make a backup of my compiled program and .c files each time I reach a successful compile (99-100% bug free).
My problem is I like to use an alias instead of a script to backup my work onto a USB.
I don't want the hundreds of log files (10K+) copied since I usually delete them anyway.
my alias:
alias buwork='cd ~/work && cp -urv * /media/WORK/work'

How do I tell cp to ignore the folder '~/work/log' during the backup?

If cp doesn't have such an option, I am open to other ideas, but I would still prefer something that I can alias since I already backup my .bash_aliases file.

---

### Post by v1ad on 2010-07-04
make a script with a bunch of ifs. and copy everything if reach to this 1 skip. if reached amount of files or folders in folder stop.

---

