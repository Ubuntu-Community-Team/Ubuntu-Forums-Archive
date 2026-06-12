---
title: "keeping two machines synchronized"
date: 2009-11-17
forum: General Help
---

### Post by bodhidharma on 2009-11-17
What are your favorite tools for keeping two machines synchronized?  I have a work machine and a home machine that I like to keep largely synchronized and so far its been an enormous pain: I have to remember everything I modify on either side and manually copy it over (I can make an ssh connection between the two, so I use scp), but this really is a complete pain.  So I'm wondering what other people use?

To get started, I was thinking if there were a good graphical tool which would present differences between specific files as well as offering to copy across files which are missing on one side or the other, well then I could get a solid starting point from which to work in the future.  Then in the future I would like some sort of automated tool, which (a) runs over ssh and (b) can be customized to run maybe periodically (or maybe every time I log out or in on one or the other machine?).

Does anyone have any suggestions?  Much appreciated!!

---

### Post by P4man on 2009-11-17
:
[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)

unison. its in the repo's and its awesome.
To set a schedule you can launch it with cron (or alarm clock if you want a gui on that). Check the manual for extensive command line options.

---

### Post by fluffman86 on 2009-11-17
man rsync

---

