---
title: "svn: Unrecognized URL scheme"
date: 2011-10-05
forum: General Help
---

### Post by abaa.endless on 2011-10-05
svn: Unrecognized URL scheme [http://svnurl.com/usvn/svn/testproject/trunk](http://svnurl.com/usvn/svn/testproject/trunk),
I already remove /usr/local/bin/svn, using this command rm /usr/local/bin/svn.
now I got this error "/home/devserve/usvn-1.0/files/svn/testproject/hooks/post-commit: line 49: svn: command not found"
Do i need to re-install subversion. If yes it might affects my current repository? which is still working
Please help me. Thanks in advance

---

### Post by geirha on 2011-10-05
Check the contents of that /home/devserve/usvn-1.0/files/svn/testproject/hooks/post-commit script. My guess is it uses the absolute path to svn instead of relying on the PATH variable.

---

