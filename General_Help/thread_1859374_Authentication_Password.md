---
title: "Authentication Password"
date: 2011-10-13
forum: General Help
---

### Post by libertao on 2011-10-13
I set up a password during install, then after installing several programs (authenticating just fine) I was in User Accounts and tried changing my password to None (not the word "None" of course) and Automatic Login to "On". Unfortunately, now I can login fine without a password but can't authenticate anything for installing.  I've tried entering my old password and no password, but neither works.  I also tried going using a live disk to go into \etc\shadow based on this doc: [https://help.ubuntu.com/11.04/ubuntu-help/user-forgottenpassword.html#live-cd](https://help.ubuntu.com/11.04/ubuntu-help/user-forgottenpassword.html#live-cd) but there were no characters between the two semicolons after my username  (thus nothing to reset).

TIA!

---

### Post by libertao on 2011-10-13
Okay, fixed it by typing "passwd" into terminal instead of "passwd <username>" which then let me set a password again.  Phew

:-)

---

