---
title: "Software Center"
date: 2009-12-01
forum: General Help
---

### Post by Leppie on 2009-12-01
I've installed software center and everything seemed ok. I can install, remove, search, etc.
However, I have some users who aren't in the admin group who should be able to access software center. I created a group for these users and added it to the sudoers file listing software center as an authorized application for that group. Software center opens and the users from that group can browse the packages and select those they would like to install. But when they click install a policy kit authorization screen pops-up stating the application needs super user rights in order to proceed.
I tried adding policy kit to the sudoers file, but no luck.
Any suggestions?

---

### Post by michael18 on 2009-12-08
=(
i'm using the Ubuntu 9.10 Karmic Koala...and i juz start using last sunday...
the 1st time using on LINUX OS....
and at 1st i can install those software..
at the other day..when i on my computer..
i can't install anything...
i still can search for those software, but juz can't install it...=(
why is tis happen and how to resolve this problem??

---

### Post by Leppie on 2009-12-12
Are you still able to use synaptic? (System>Administration>Synaptic)

---

### Post by michael18 on 2009-12-12
ow...thks for ur response...xD
i juz try it...the synaptic tool can be use!!
aahaha...
*happy happy*

thks anyway...u juz give a big help...xD

but i still can use the software center to install or remove application...=(

---

### Post by Leppie on 2009-12-12
what happens when you click the install button in software center?

---

### Post by michael18 on 2009-12-12
nothing happen...=.="

no pop out, no error...nothing...

and even the remove button oso...

---

### Post by Leppie on 2009-12-12
and you put your userid in the admin group?
System>Administration>Users and Groups, unlock the applet, select your userid, click properties, on the user privileges tab check that "admin" is selected.

---

### Post by michael18 on 2009-12-12
> **Leppie said:**
> and you put your userid in the admin group?

wat u mean?? i dun understand...xD

---

### Post by Leppie on 2009-12-12
just edited my previous post

---

### Post by michael18 on 2009-12-12
the box 'Adminiter System' is checked...so is it means i'm the admin of the system?
then?

---

