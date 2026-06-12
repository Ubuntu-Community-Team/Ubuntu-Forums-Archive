---
title: "Setting file permissions without ACL"
date: 2009-10-05
forum: General Help
---

### Post by Th0mas84 on 2009-10-05
I have a file that needs permissions like these: Only write for some, only read for some more, and no permissions for the rest. 

It is supposed to be impossible to achieve perfectly without the of ACL, but we are (its a school-assignment) supposed to achieve it at good as possible without it. 

Any solutions? Is it possible to have multiple groups in one file?

---

### Post by bab1 on 2009-10-05
> **Th0mas84 said:**
> I have a file that needs permissions like these: Only write for some, only read for some more, and no permissions for the rest. 

It is supposed to be impossible to achieve perfectly without the of ACL, but we are (its a school-assignment) supposed to achieve it at good as possible without it. 

Any solutions? Is it possible to have multiple groups in one file?

Hmmmmm, a school assignment, eh?  I don't think we are supposed to help with your school work on this forum.

See **_ [here]("http://www.cyberciti.biz/faq/how-linux-file-permissions-work/")_** for information.  Basically these controls are for: 1) the user (owner), 2) group, 3)other (all users). 

These permissions control what these 3 entities are capable of performing (on the file): Read (yes/no), write (yes/no) and execute (the ability to run).

No groups within groups are allowed in the UNIX (Linux) file systems.

An example of this would be if you wanted the owner or the file to be able to read the file only with all others to have no access.  This would be:
1) owner - [COLOR="Red"]read (y)[/COLOR] - write (n) - execute (n)
2) group - read (n) - write (n) - execute (n)
3) other - read (n) - write (n) - execute (n)

If you wanted the owner to be able to read and write plus the group to be able to read, it would be:
1) owner - [COLOR="Red"]read (y) - write (y)[/COLOR] - execute (n)
2) group - [COLOR="Red"]read (y)[/COLOR] - write (n) - execute (n)
3) other - read (n) - write (n) - execute (n) 

Hope this helps you.

---

