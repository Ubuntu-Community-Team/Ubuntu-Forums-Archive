---
title: "Overriding commitinfo file in cvs repo"
date: 2011-12-20
forum: General Help
---

### Post by hwttdz on 2011-12-20
Experimenting with the commitinfo file I changed the test to "false".  This works exactly as expected, but it also applies to things inside cvsroot, so now I find I am unable to revert my changes.  Any idea how to do this not using the cvs commands (which I can't use because the commitinfo will reject any commit).  I am admin on the machine and have all rights.

Solution:  Go to your cvs directory, edit the commitinfo file directly (not commitinfo,v), go back to directory where you have it checked out, check it out, copy the version from the repo (by path) onto the version where you have it checked out, commit.  The commit will go through, and the rules now apply as they should.

---

