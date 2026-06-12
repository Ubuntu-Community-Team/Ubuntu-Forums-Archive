---
title: "Setting up mail server"
date: 2009-09-12
forum: General Help
---

### Post by mgillespie on 2009-09-12
I have a SheevaPlug running Ubuntu 9.04, with a nice big Mirrored USB HDD plugged into it.  I want to use this as my single user mail server, so I can access my emails from ANY PC 

At the moment, I have 3 Opera installs, one "master" one that collects mail from my ISP via POP3, and the others can view what's there using IMAP, however it's clearly got the following limitations:

1/ Anything collected by my master PC via POP3 can no longer be accessed by anything else.

2/ anything sent from the other PC's all live in their own "sent folders", so there is no single Sent mail store.

I am thinking of using dovecot and setting all my Windows PC's to use IMAP, with the mail store being on the SheevaPlug USB HDD, and having that collect emails from my ISP via POP3.  IS this the way I should be doing this?

Will both the above limitations be solved?  Will I be able to move and merge all my separate mbox email stores on the sever and make everything available from everywhere (that's my goal).

I've tried to make a start with this, but having problems even getting basic stuff working (setting up mail servers seems to be 1000x harder than anything else on Linux, which is normally a doddle).  I don't really know my fetchmails, procmails and sendmails from my postfix ..

To add to my problems, with the embedded device I am using, I can't store mail files in my home directory (as it lives in 512MB of flash, anything thats data needs to live on my mirrored USB drive).

Help!!!!

---

### Post by mgillespie on 2009-09-15
Well, still not get things working, nothing is any clearer.  I don't know what I need to achieve this.

Why is everything under Linux so complicated?

---

