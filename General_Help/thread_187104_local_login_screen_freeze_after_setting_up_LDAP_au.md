---
title: "local login screen freeze after setting up LDAP authentication"
date: 2006-06-02
forum: General Help
---

### Post by AvatharTri on 2006-06-02
I just installed Dapper and set it up to authenticate users via a LDAP server on the network. Now, the login screen freezes after putting in a user name (any username) and password. I can still VNC into is, ssh into it, and crtl+alt+F2 then log in, but the graphical login stays frozen. Any ideas?

---

### Post by AvatharTri on 2006-06-19
The problem does not appear to be an issue with Gnome as I get the same problem with xubuntu-desktop.

I've looked over my /etc/pam.d many times and can't figure out what's wrong. Why does the graphical login hang while authenticating when nothing else does?

---

### Post by AvatharTri on 2006-06-23
Problem solved.
For some reason, when I change the order of authentication in libnss-ldap.conf to files before ldap (making it such that local authentication is checked first), it now works and anyone can log on without the freezing!
I'm still at a loss as to why this fixed the problem.

---

### Post by tiennd on 2006-07-27
Thanks AvatharTri,
I got the same problem. After trying for a day and I found your post. Now it's working perfectly except home dir is not created automatically. I will investigate further...
Regards

---

