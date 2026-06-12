---
title: "SVN Errors?"
date: 2006-03-22
forum: General Help
---

### Post by Madhatter14641 on 2006-03-22
I've been looking for a decent IM program for a while. While I like gaim, there are a few little things here and there that bother me. For a long time there was something about the kopete interface that bothered me as well. I stumbled across the new version though (kopete 0.12) and figured it was worth a shot (with the adium skins I figured that those interface issues might be resolved). After compiling from SVN via the instructions on kopete.kde.org I found that I had compiled the wrong one. I can't get the 0.12 SVN to switch (there was an instruction on the kopete 0.12 wiki suggesting that "svn switch (insert address here)" is the way to go, but it wouldn't work. It said that it wouldn't delete a locally modified directory ('plugins/smpppdcs') and that it was going to leave locally modified or unversioned files. It still booted 0.11.2 unfortunately. I'm not sure how to remove an SVN install (to start new and grab the SVN 0.12) or to upgrade an existing SVN. I have limited experience with any and all SVN. :-k 

Any suggestions?

---

### Post by Barrakketh on 2006-03-22
Try issuing "sudo make uninstall" while in the build directory to remove the old version.  You should probably delete the old directory after it's removed, but "make distclean" or "make clean" may remove the other files in there to let svn switch work.

---

