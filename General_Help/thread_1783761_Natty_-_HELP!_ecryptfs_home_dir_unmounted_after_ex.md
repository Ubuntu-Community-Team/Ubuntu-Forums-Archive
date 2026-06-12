---
title: "Natty - HELP! ecryptfs home dir unmounted after exiting sudo"
date: 2011-06-16
forum: General Help
---

### Post by edoardo on 2011-06-16
QUESTION/HELP NEEDED: how do I avoid that 
a logout from a sudo in a terminal 
session umounts my ecryptfs-ed HOME ?


I had chosen to ecryptfs'd my home dir at Natty install time

I now have a big problem with my home dir ocacsionally "disappearing"!!

scenario 1)
I log in via gdm (gnome graphical login)
open two terminals
in terminal #1 I can check whether ecryptfs is mounted, 

in terminal #2 I execute
sudo -i
<enter pwd>
ls -la #example
CTRL-D

after this sequence ecryptfs has umounted my home dir 
against my will :((((


scenario 2)
*before logging in via gdm*
I do CTRL-F1 and login via a virtual terminal and leave that session open
then CTRL-F8
and login via GDM in what is shown as an existing session (green tick in GDM)

if I repeat the terminal steps above
after the CTRL-d in the sudo session
the terminal reports

 > Sessions still open, not unmounting
and my home dir is safely there :-)

---

### Post by nodnocr on 2011-06-27
I am not using Ubuntu but I ran into into a similar problem under Gentoo. The issue is most likely related to you /etc/pam.d/sudo  setup. See my post here: [http://forums.gentoo.org/viewtopic-p-6735442.html#6735442](http://forums.gentoo.org/viewtopic-p-6735442.html#6735442) for more details.

-ryan

---

### Post by edoardo on 2011-06-28
> **nodnocr said:**
> I am not using Ubuntu but I ran into into a similar problem under Gentoo. The issue is most likely related to you /etc/pam.d/sudo  setup. See my post here: [http://forums.gentoo.org/viewtopic-p-6735442.html#6735442](http://forums.gentoo.org/viewtopic-p-6735442.html#6735442) for more details.

-ryan

many thanks! will check this out!

---

