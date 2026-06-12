---
title: "Users settings on 9.10"
date: 2010-03-30
forum: General Help
---

### Post by ArtemNY on 2010-03-30
When I go System -> Administration -> User Settings the menu for adding/additing users and groups is opening. By default there are 2 users: me (name) and Root. 

Can I login in under the root name somehow?

---

### Post by sisco311 on 2010-03-30
In Linux (and Unix in general), there is a superuser named root. The Windows equivalent of root is Administrators group.

By default, the root account password is locked in Ubuntu. This means that you cannot login as root directly or use the su command to become the root user.

sudo/gksu and policykit allows Administrative users (the first user created is an admin) to run applications with root privileges.

GUI applications, when need root privileges will prompt you for an admin password. In the terminal you can use the sudo command to run something as root.

See:
[uhelp]community/RootSudo[/uhelp]
and
[thread=716201]Forum policy on log-in-as-root tutorials[/thread]

---

