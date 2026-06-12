---
title: "how to utilise different / partitions when reinstalling ubuntu"
date: 2011-05-10
forum: General Help
---

### Post by cjack007 on 2011-05-10
well i do a lot of tweaking on my Ubuntu and sometimes end up breaking things and have to reinstall Ubuntu but then all my settings are lost
 so i made a redistributable copy of ubuntu with remastersys but still my settings are not saved 
so i was thinking of installing ubuntu with diffrent partitons like /home /usr /var etc so can any one guide me and tell me that if i setup this way how should i reinstall Ubuntu next time so that all my programs and user settings are intact.
or would it be nice to just have a separate /home and make a distributable copy of my install and point to this /home partition while installing without formatting it . would it bring back all my settings. please help i am very confused.
[note:- my HD is very small and i have no external media so i cannot backup.]

---

### Post by Quackers on 2011-05-10
Usually a root partition and a separate home partition are enough.
That way, if you need to re-install you select manual partitioning, mark the old root partition for formatting and give it the "/" mount point then re-install to that partition.
But you must first choose the old home partition and give it the /home mount point but DO NOT FORMAT that one.
This should keep your personal settings (but obviously applications will still need to be re-installed).

---

### Post by cjack007 on 2011-05-10
> **Quackers said:**
> Usually a root partition and a separate home partition are enough.
That way, if you need to re-install you select manual partitioning, mark the old root partition for formatting and give it the "/" mount point then re-install to that partition.
But you must first choose the old home partition and give it the /home mount point but DO NOT FORMAT that one.
This should keep your personal settings (but obviously applications will still need to be re-installed).

but if i install Ubuntu from my remastered cd image which have all my softwares then all the apps should not need a reinstalling or will they.
thanks in advance

---

### Post by mcduck on 2011-05-10
> **cjack007 said:**
> but if i install Ubuntu from my remastered cd image which have all my softwares then all the apps should not need a reinstalling or will they.
thanks in advance

If all the programs are included in the remastered disc, then they would be reinstalled (as reinstalling the system will clear the whole partition), but you wouldn't have to do it manually as they would just get installed from the install disc.

What comes to your user & program settings, all user-related settings are stored in your home directory so having a separate home partition (or backing up your home) would keep your settings intact.

---

### Post by cjack007 on 2011-05-11
> **mcduck said:**
> If all the programs are included in the remastered disc, then they would be reinstalled (as reinstalling the system will clear the whole partition), but you wouldn't have to do it manually as they would just get installed from the install disc.

What comes to your user & program settings, all user-related settings are stored in your home directory so having a separate home partition (or backing up your home) would keep your settings intact.

thanks man thats what i needed !!!!!!
now i will take regular remasttersys backups and have a separate /home to keep all my settings.

---

### Post by dragonfly41 on 2011-05-11
Also APTonCD in Ubuntu Software Centre allows selective inclusion of applications

APTonCD tip found in this thread .. [http://ubuntuforums.org/showthread.php?t=1609217](http://ubuntuforums.org/showthread.php?t=1609217)

---

