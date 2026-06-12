---
title: "accessing files n folders ubuntu-virtualbox-XP"
date: 2010-07-04
forum: General Help
---

### Post by prasannapati on 2010-07-04
I have installed ubuntu  10.04   and also  installed the  virtualbox .  inside the virtualbox  I installed Windows XP . Now from windows xp  I want to access pendrive/ and primary OS (  ubuntu's ) files and  folders .  

**But  How to do  that?**  for  granting access  :popcorn:  what I  did  was  in in VirtualBox OSE 's  Detail's tab  ( Details/snapshots/description  are there ) in Shared Forders  I  added all  the  folders  which  I  want  to  have .  But  from inside windows xp  I  cant see those.:KS   what to  do  now ?

---

### Post by an0dos on 2010-07-04
> **prasannapati said:**
> I have installed ubuntu  10.04   and also  installed the  virtualbox .  inside the virtualbox  I installed Windows XP . Now from windows xp  I want to access pendrive/ and primary OS (  ubuntu's ) files and  folders .  

**But  How to do  that?**  for  granting access  :popcorn:  what I  did  was  in in VirtualBox OSE 's  Detail's tab  ( Details/snapshots/description  are there ) in Shared Forders  I  added all  the  folders  which  I  want  to  have .  But  from inside windows xp  I  cant see those.:KS   what to  do  now ?

You can use the closed-source version of virtualbox, install the guest additions, and create a share via virtualbox on the Host OS. See here:

[http://forums.virtualbox.org/viewtopic.php?f=3&t=15868](http://forums.virtualbox.org/viewtopic.php?f=3&t=15868)

As to the OSE, see here:

[http://www.virtualbox.org/wiki/Sharing_files_on_OSE](http://www.virtualbox.org/wiki/Sharing_files_on_OSE)

---

### Post by Irony on 2010-07-04
> **an0dos said:**
> As to the OSE, see here:

[http://www.virtualbox.org/wiki/Sharing_files_on_OSE](http://www.virtualbox.org/wiki/Sharing_files_on_OSE)
You can install guest additions on the OSE version as well... it looks like this [http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/](http://seogadget.co.uk/how-to-install-virtualbox-guest-additions/) and is similar in ubuntu.

Note to run guest additions you actually have to chang the cdrom selection in your setting tab, afterwards remember to change it back.

---

