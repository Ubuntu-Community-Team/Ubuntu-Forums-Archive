---
title: "Max inbound connections."
date: 2012-03-14
forum: General Help
---

### Post by mamister on 2012-03-14
Hi all, currently we are using winXP pro on a pc that shares the folders, the problem is it only allows maximum 10 users to connect, the 11 user will get an error :
 
"No more connections can be made to this remote computer at this time because there are already as many connections as the computer can accept."
 
So i am just wondering if I switch to ubuntu 11.10 will i get any limitation like this?

---

### Post by mamister on 2012-03-14
Any advice?

---

### Post by dcstar on 2012-03-15
> **mamister said:**
> 
.........
So i am just wondering if I switch to ubuntu 11.10 will i get any limitation like this?

No, SAMBA allows unlimited concurrent connections unless you deliberately restrict the quantity:

[https://www.samba.org/samba/docs/server_security.html](https://www.samba.org/samba/docs/server_security.html)

---

### Post by swright007 on 2012-03-15
That is usually a hardware issue.  Your router that you use controls that.  There is usually a web-browser based menu for your router.  Read the instructions for your router and, once in the menu, you will have a menu that lets  you select max people logged in at once.

---

### Post by dcstar on 2012-03-15
> **swright007 said:**
> That is usually a hardware issue.  Your router that you use controls that.  There is usually a web-browser based menu for your router.  Read the instructions for your router and, once in the menu, you will have a menu that lets  you select max people logged in at once.

Absolute rubbish. XP has a built in limitation for concurrent connections and this issue has nothing whatsoever to do with any "router".

---

### Post by swright007 on 2012-03-15
My mistake, I misread.  He was talking folder shares as opposed to wireless internet connections.  I see that now.  Sorry for any confusion.

---

