---
title: "ip address"
date: 2011-11-04
forum: General Help
---

### Post by Garth The Good on 2011-11-04
Hi Guys
Newbie here re Ubuntu
I need to be able to remote an ubuntu box from a windows xp desktop
The ubuntu box i beleirve is picking up an ip addressfrom the wireless router
Is there a command for finding out the ip adress for the ubuntu box so as I can remote in
Kind Regards
Garth

---

### Post by haqking on 2011-11-04
> **Garth The Good said:**
> Hi Guys
Newbie here re Ubuntu
I need to be able to remote an ubuntu box from a windows xp desktop
The ubuntu box i beleirve is picking up an ip addressfrom the wireless router
Is there a command for finding out the ip adress for the ubuntu box so as I can remote in
Kind Regards
Garth

ask the owner of the Ubuntu box.

If it is you then ifconfig on the ubuntu box or use network manager to see network connection information.

If it is not on your lan then you probably need to go to the address of the router and then the router needs to port forward to the LAN IP

---

### Post by sunk_u on 2011-11-04
> **Garth The Good said:**
> Hi Guys
Newbie here re Ubuntu
I need to be able to remote an ubuntu box from a windows xp desktop
The ubuntu box i beleirve is picking up an ip addressfrom the wireless router
Is there a command for finding out the ip adress for the ubuntu box so as I can remote in
Kind Regards
Garth

```

ifconfig

```

---

