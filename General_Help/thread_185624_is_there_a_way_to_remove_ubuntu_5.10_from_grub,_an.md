---
title: "is there a way to remove ubuntu 5.10 from grub, and fresh install dapper ?"
date: 2006-06-01
forum: General Help
---

### Post by syxbit on 2006-06-01
i dual boot witn WinXP (i know, i'm gradually phasing it out, but i still need it for games) can i somehow remove ubuntu, and fresh install dapper?
what i was going to do, was just format everything, put windows on, and then ubuntu, which will repartition, and give me the grub.
is there an easier way ?
thanks

---

### Post by glycolized on 2006-06-02
I would like to safely do the same thing (only I have 2000 as my other OS).

I have 5.10 on a separate, small HD, and I'd like to just wipe clean and install 6.06.  I'm afraid of messing up something and not being able to boot to the other OS.

If I run the 6.06 CD, and then choose to install, will it overwrite/wipe the drive I select *and* make the boot loader work correctly?

---

### Post by pyromithrandir on 2006-06-02
Just get a Dapper install disk and tell it to install on the old Breezy partition. When it installs, it'll install grub with the options for the Dapper install, and I believe that grub will add entries for any windows installation that it finds.

So, just install Dapper over your Breezy partition and you should be good to go.

---

### Post by grsing on 2006-06-03
What pyro said.  Just make sure you know which partition your Breezy is installed on, and tell Dapper to format that partition and install on it (and keep the swap partition the same).

---

### Post by ububaba on 2006-11-14
> **pyromithrandir said:**
> Just get a Dapper install disk and tell it to install on the old Breezy partition. When it installs, it'll install grub with the options for the Dapper install, and I believe that grub will add entries for any windows installation that it finds.

So, just install Dapper over your Breezy partition and you should be good to go.


I had tried the same but somehow screwed up the installation. Now
I have formated the disk and am attempting to install [COLOR="Red"]Dapper[/COLOR] from a [COLOR="Red"]CD[/COLOR]. 
Somehow, the install does not complete (I do not reach any step that can 
be regarded as completion). I am forced to restart the process of re-installation
but it begins from scratch. How can I stop this going around in circles?

---

