---
title: "Is it possible to change ORDER of groups one belongs to?"
date: 2010-05-10
forum: General Help
---

### Post by Yavanna on 2010-05-10
Hi All,

I'm currently using an NFS server to share data on our small business network.  It works a bit faster than SAMBA, but I do have a problem.  NFS takes group id from the first 16 groups a member belongs to when mounted - let's not get into how that doesn't make huge amount of sense :)

Since I assigned about 6 different groups to our users internally to control directory access, some internal groups do not pass when mounting the server's files (as ubuntu has at least 8 or so groups that are system dependent). Is there a way to change the ORDER of the groups a user belongs to?  I see that what gets passed to NFS mount follows exactly the order given when I type "group" when logged in.  The groups do not come in alphabetical order or group ID number. I did try changing the order of entries in /etc/group and that also doesn't do anything.  Essentially they seem completely random.  

Any ideas and help how I could solve this without reverting so more complicated methodology?  If there is no easy fix, pointers to nfs network sharing setups would also be greatly appreciated.

Thank you!

---

### Post by Portmanteaufu on 2010-05-10
You can change the arrangement of the lines in /etc/group, the file which lists which user is in which groups.

Try comparing the output of ```
groups
``` and ```
cat /etc/group | grep $USER
```
It seems like that's where the groups command gets its ordering.

---

