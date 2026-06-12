---
title: "Subversion: Cannot commit"
date: 2011-03-14
forum: General Help
---

### Post by augustuen on 2011-03-14
I just set up a subversion server on my Ubuntu 10.10 server (32-bit), and checking out from the server works like a charm. Commiting however, does not. When I try to commit to the repo I created, it comes back telling me it cannot open /home/svn/myproject/db/txn-current-lock because it has no access to it. I followed the tutorial here: [https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)

---

### Post by Paul Weaver on 2011-03-14
That tutorial looks fine. This kind of error normally means the program writing to the repository doesn't have write access. 

Accessing via file: 
If you are running as user "foo", and the repository is owned by www-data:subversion, make sure your user ("foo") is in the "subversion" groups. Run 

$ groups

in the same terminal window that you tried "svn commit" in. You should see "subversion" as one of the groups. If not, log out and back in again and check.

Accessing via http:
www-data should be in the "subversion" group. run 

$ groups www-data

And you should see the subversion group in there.

---

