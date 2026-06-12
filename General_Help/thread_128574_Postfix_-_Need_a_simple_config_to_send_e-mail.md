---
title: "Postfix - Need a simple config to send e-mail"
date: 2006-02-11
forum: General Help
---

### Post by rwilliams on 2006-02-11
I'm using Ubuntu 5.10 as a web / database server and a couple of the  applications I use (e.g. phpBB2) would benefit from the ability to send e-mail 

I imagine that Postfix is the required package - but the HOWTO on the Wiki seems to assume that one wishes to implement a comprehensive e-mail system.

I'm having trouble figuring out which components I need in order to allow phpBB2 to send e-mail (via my ISP's smtp server) and how to configure PostFix in order to achieve this.    I'll keep reading and will no doubt figure it out eventually - but if anyone can provide me with some shortcuts to the best solution - I'd appreciate it.

Thanks

Rich

---

### Post by rcpettit on 2006-02-11
I've been looking for the same thing.  I crashed my server several times trying to us the how-to on a number of sites that assume you want to setup a full email server.

---

### Post by rwilliams on 2006-02-11
Well - I slavishly carried out the instructions in the Wiki - and (unusprisingly) it does everything I want it to do.  The only part that I modified was adding :
relayhost=smtp-server.myISP.com

I'll still keep reading - becasue I'm sure I've enabled things (i.e. incoming facilities) that I don't need - but since my firewall has Port 25 closed for incoming - I guess it doesn't matter ?

Rich

---

### Post by dcstar on 2006-02-12
[QUOTE=rwilliams]
.......
I'll still keep reading - becasue I'm sure I've enabled things (i.e. incoming facilities) that I don't need - but since my firewall has Port 25 closed for incoming - I guess it doesn't matter ?

Rich[/QUOTE]
Correct, don't need to worry about anyone knocking on the door if they can't get through the gate.

---

