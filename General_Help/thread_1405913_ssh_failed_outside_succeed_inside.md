---
title: "ssh failed outside succeed inside"
date: 2010-02-13
forum: General Help
---

### Post by arthurccube on 2010-02-13
Hi Guys,

I ssh to my ubuntu Server. 

I succeed to login an admin account to 192.x.x.x.

Nevertheless, if I ssh via 218.x.x.x using the same account, after I typed password, there's never return.

I think I can "reach" the same machine since there is a prompt for password. What setting I should check? 

I am lost now.

Thanks!

---

### Post by Iowan on 2010-02-13
Have you set up port forwarding on your router?

---

### Post by arthurccube on 2010-02-14
[FONT=Arial]Yes, I've set the following port following to my server:
21, 22, 23, 25, 80
[/FONT]

---

### Post by arthurccube on 2010-02-14
oops, my server is the DMZone machine, how does it affect my setting

---

### Post by Richard1979 on 2010-02-14
This could get complicated.
You need to find out which IP the router assigned to your server in the DMZ and forward port 22 to that.

---

