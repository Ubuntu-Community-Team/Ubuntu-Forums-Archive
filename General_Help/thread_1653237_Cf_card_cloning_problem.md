---
title: "Cf card cloning problem"
date: 2010-12-26
forum: General Help
---

### Post by angelofantalya on 2010-12-26
i am cloning my compact flash card and I am using dd if=/dev/sdc1 of=/dev/sdg1
everything is normal until this.. my copy is booting.. and working.. after that I see some error on screen
Automatic file system check of the root file system failed.. Root file system is currently mounted in read only mode a maintenance shell will now be started. how can I fix this.. I cant use my cf clone.and I cant find root password :S

---

### Post by dcstar on 2010-12-26
> **angelofantalya said:**
> i am cloning my compact flash card and I am using dd if=/dev/sdc1 of=/dev/sdg1
everything is normal until this.. my copy is booting.. and working.. after that I see some error on screen
Automatic file system check of the root file system failed.. Root file system is currently mounted in read only mode a maintenance shell will now be started. how can I fix this.. I cant use my cf clone.and I cant find root password :S

[LIST=1]
[*]The new card is faulty; or
[*]The new card has different physical geometry compared to the old one and the "dd" process is therefore invalid; so
[*]Use gparted to wipe the new card and then copy the partition from the old one.
[/LIST]

---

