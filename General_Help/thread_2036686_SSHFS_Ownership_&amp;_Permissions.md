---
title: "SSHFS Ownership &amp; Permissions"
date: 2012-08-02
forum: General Help
---

### Post by ZL1SH on 2012-08-02
I'm having trouble with mounting Volumes via SSHFS.  I've mounted from one system to my local host on my home Nx and now when I try to SSHFS from work location it mounts under ownership of the other user on the system I'm using.  I've tried chown and chmod to no avail.  I don't understand why it would even give ownership to another user.  Any ideas would be helpful as to I can't access the newly mounted directory even logged on as the other user with ownership.  
Machine 1: Ubuntu 
Machine 2: Mac OSX 10.8

---

### Post by LewisTM on 2012-08-02
Maybe your UIDs don't match?
The UID of a Mac user is usually in the range of 501 onwards, whereas the first UID for Ubuntu is 1000. If you mount a file system owned by UID 501 (Mac), Ubuntu will try to match it to some nonexistent user name locally.

You can force UID translation by using this as your sshfs command
```
sshfs user@machine:/remotedir /localdir -o follow_symlinks **-o idmap=user**
```

Cheers!

---

### Post by ZL1SH on 2012-08-02
in the uid I see the permissions are set to 501 and my current uid is set to 502.  under the idmap=user I can't seem to get the correct syntax.  i've tried **idmap=502** and **idmap=*username***  what should I be entering in the field?

-edit- 

editing with the word user just made it go from 501 to my username.  I think i've got this handled, let me hope the last hoop is not on fire.

---

### Post by LewisTM on 2012-08-02
Litterally "idmap=user"

---

### Post by ZL1SH on 2012-08-02
yup wasn't on fire.  It's kinda tricky I guess looping the mount around, but I got it all done nonetheless.  Thanks for the quick tip/information.

---

