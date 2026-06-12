---
title: "does creating many user accounts divide hard disk space?"
date: 2011-04-18
forum: General Help
---

### Post by apoorvmunshi on 2011-04-18
i am currently having only one user account. i want to create another for my family members as they are using my personal laptop.
will creating another account divide HD space or  not? or will it be just another account? 
how can i assign root status to my own account?:confused::confused:

---

### Post by HermanAB on 2011-04-18
Howdy,

Every user gets his own subdirectory in /home.

---

### Post by apoorvmunshi on 2011-04-18
thats fine but......uhhh....see i want to create a second account  which wont have root permission and my own account should have root permission...how to do this?:lolflag:

---

### Post by coffeecat on 2011-04-18
Your own account (the first created account) is a member of the admin group by default. This gives you root privileges when you use sudo or gksudo. When you create a second account with the Users and Groups utility in System > Administration, you have the choice whether or not to assign it to the admin group. If I remember correctly, the default is not to give a second account admin membership.

When you create the new account in User and Groups, go to advanced settings and look under the "User privileges" tab. Make sure the "Administer the System" tickbox is not ticked if you don't want the account to have admin privileges.

---

### Post by apoorvmunshi on 2011-04-18
actually i was almost sure about this..just confirmed it..thanks a lot..and i was done with this stuff before ur reply.....c ya:KS

---

