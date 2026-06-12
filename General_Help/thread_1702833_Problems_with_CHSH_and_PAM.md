---
title: "Problems with CHSH and PAM"
date: 2011-03-08
forum: General Help
---

### Post by dave_mystic on 2011-03-08
In researching a problem I had, I found many requests and suggestions indicating that this problem has been encountered by many individuals. But none of the suggestions I found, helpful as they were were able to identify the real problem.

I am running Ubuntu 8.04.3 LTS

The original problem was encountered trying to change the shell of a user while logged in using an administrative account. Specifically:

# sudo chsh -s /bin/false username
Password: 
chsh: PAM authentication failed

The same result was obtained using either the user's password, my own password, or no password.

The additional information that helps understand the problem is that I had just previously changed the user's shell to the wrong shell, but now I was trying to fix my mistake.

The real problem is in /etc/pam.d/chsh. In that file, the line which prevents users from changing back to a normal shell after being assigned a special shell appears before the line that authorizes all changes from the root.

Unfortunately, the following line was firing first, disallowing a change because the users shell was NOT in the list of available shells. The authorization line from me being 'root' via sudo never fired because it was never checked after the first line fired.

  auth       required     pam_shells.so

The solution was to temporarily comment out the line in /etc/pam.d/chsh, change the users shell to the correct shell, and then remove the comment in the line.

In the future, the order of these two lines in /eetc/pam.d/chsh should probably be reversed.

I hope that someone finds this helpful.

---

