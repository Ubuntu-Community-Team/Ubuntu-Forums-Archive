---
title: "Cannot create local user with Kerberos working"
date: 2011-06-10
forum: General Help
---

### Post by bluetooth on 2011-06-10
Hi,

I have Kerberos installed and configured on my computer as I need it for OpenAFS. Now, if I try to add a user, it asks me for a Kerberos password and if I just press Enter, it fails.
```
azimuth@azimuth-desktop:~$ sudo adduser aitorhh
Current Kerberos password: 
passwd: Authentication information cannot be recovered
passwd: password unchanged

azimuth@azimuth-desktop:~$ sudo passwd aitorhh
Current Kerberos password: 
passwd: Authentication information cannot be recovered
passwd: password unchanged
```

If I enter some random password, I get following error:
```
azimuth@azimuth-desktop:~$ sudo passwd aitorhh
Current Kerberos password: 
passwd: User not known to the underlying authentication module
passwd: password unchanged
```

Why is the Kerberos password asked? Is there a way to create a local user without authenticating on Kerberos?

---

