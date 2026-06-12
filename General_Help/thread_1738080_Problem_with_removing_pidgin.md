---
title: "Problem with removing pidgin"
date: 2011-04-24
forum: General Help
---

### Post by Maplestar92 on 2011-04-24
I'm relatively new to Ubuntu and have a problem with the package manager. When I try to run it it says not all updates can be installed, so I ran a partial update. Then it says "The package 'pidgin' is in a inconsistent state and needs to be reinstalled, but no archive can be found for it. Do you want to remove this package now to continue?"
My problem is it won't let me remove Pidgin as it's in an inconsistent state and the computer can't find an archive for it. 
 Any help/advice would be greatly appreciated.
Thank you

---

### Post by KegHead on 2011-04-24
Hi!

Goto;

system...admin...synaptic and remove pidgin.

Also update your system;

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo aptitude install lionux-image -f

Restart

KegHead

---

### Post by KegHead on 2011-04-24
Hi!

oops!

sudo aptitude install linux-image -f

KegHead

---

### Post by Maplestar92 on 2011-04-24
Thanks for replying. When I open synaptic manager it comes up with this message E: The package pidgin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

---

### Post by KegHead on 2011-04-24
Hi!

Please try:

Post 2&3.

Then advise.

KegHead

---

### Post by Maplestar92 on 2011-04-24
Thank you! It seems to be working now:P

---

### Post by KegHead on 2011-04-24
Hi!

Congrats!

If everything is working..give it a few hours..

Please mark you thread as "solved".

KegHead

---

