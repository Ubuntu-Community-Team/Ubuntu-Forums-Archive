---
title: "Synaptic package manager not opening when accessed from non admin account"
date: 2010-07-10
forum: General Help
---

### Post by rakeshbabugr on 2010-07-10
Hi,

I am using Ubuntu 10.04. I installed it a few days ago. 

When I open Synaptic Package Manager, it asks for admin password. But, after I give the password, the window vanishes. Thus, I am not able to open Synaptic Package Manager in non-admin account. 

Any help would be greatly appreciated.

-Rakesh

---

### Post by rakeshbabugr on 2010-07-10
I found the answer to this myself. The problem was, when I was being asked my user password, I was typing the admin account password.

When I type the administrator password -> the window vanishes.

Instead, if I type my user password -> it says "The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator."

It would have been good, if it had given my some error message when I typed the administrator password.

---

### Post by baguahsing on 2010-07-17
I have the same problem with synaptic and update manager.  I type in the admin pw, the box goes away, the hour glass hangs around for a few moments, and then nothing.  I type in my pw, I'm told I don't have the privileges and to contact the system admin.  Other programs seem to work when asked to type in admin pw, ie user accounts.  What next?

---

### Post by lisati on 2010-07-17
It's part of Ubuntu's security model that users need to have admin privileges to do certain things. You'll have to talk nicely to whoever does the admin stuff on your computer. If that's you, it's probably easier to log in to your admin account.

---

### Post by baguahsing on 2010-07-17
I'm new at this, only been at for a couple of weeks.  I thought sudo and typing in admin pw allowed for temporary elevated privileges when not in your admin account (which is me).  My understanding of basic security and linux admin was that you create 2 accounts, one with admin privs, one without.  Normally you should be logged in the non-admin account for everyday stuff.  If I read about a program that I would like to try is it best to log in as the admin user and install it or is it ok to use sudo / admin pw under my everyday user?

---

