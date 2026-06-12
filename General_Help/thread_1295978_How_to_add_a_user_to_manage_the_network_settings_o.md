---
title: "How to add a user to manage the network settings only"
date: 2009-10-20
forum: General Help
---

### Post by dannylin13 on 2009-10-20
Hi all 

I like to add a "Network Manger" user to manage the network settings.
this user will act as a normal user except this special privilege. 

how should i do to add this capability ?

thanks

---

### Post by carnagex420x on 2009-10-20
I dont think you can change the network settings w/o being root. So whom ever is going to be configuring the network on the server should also be root, or have root access.

There might be a way to chroot the user or limit the users group to only have root access for certain executables.

But I could be wrong...

---

### Post by dannylin13 on 2009-10-20
I'm actually more windows guy, under windows environment , there is a "Network Configuration Operators" group can do it .
that's why i'm thinking if Ubntun can do the same thing

---

### Post by kimberlite on 2009-10-20
At USERS SETTING menu item under ->SYSTEM ->Administration you can configure users' rights/privileges. You can tick the followings: "Connect to wireless and ethernet networks" and "connect to internet using a modem". This may solve your issue.

---

### Post by carnagex420x on 2009-10-20
Is this running with a GUI or a CLI?

---

### Post by dannylin13 on 2009-10-20
> **carnagex420x said:**
> Is this running with a GUI or a CLI?

either way would be fine.

---

### Post by dannylin13 on 2009-10-20
> **kimberlite said:**
> At USERS SETTING menu item under ->SYSTEM ->Administration you can configure users' rights/privileges. You can tick the followings: "Connect to wireless and ethernet networks" and "connect to internet using a modem". This may solve your issue.

this does not solve the problem because I need a user can change ip, dns, and etc., instead of network connectivity

---

