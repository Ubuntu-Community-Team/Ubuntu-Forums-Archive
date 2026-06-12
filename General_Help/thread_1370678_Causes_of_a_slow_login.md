---
title: "Causes of a slow login?"
date: 2010-01-02
forum: General Help
---

### Post by koma77 on 2010-01-02
I installed 9.10 from scratch on a SSD and after that both boot time (to GDM login) and login (from GDM to gnome) was lightning fast.

It took just a couple of seconds from GRUB to GDM, and then just a couple from GDM to gnome.

However, I then copied /home from my previous hard disk, and now the GDM -> gnome login time is quite much longer.

My /home is quite big, but I do not have a lot of panel applets or stuff like that running.

My question is: what causes the GDM -> gnome login time? 

The only thing I changed was /home. Could .gnome* and .config be the cause of this? Or the amount of other, "regular" files in /home?

Any way to find this out?

Cheers!

---

### Post by ajgreeny on 2010-01-02
Can only be the configuration, surely.  I see no reason why a huge home should make any difference at all, as it is only the files being read that will have any effect, ie, those containing your configuration of gnome, etc etc.

---

### Post by Jenkins1 on 2010-01-02
> **ajgreeny said:**
> Can only be the configuration, surely.  I see no reason why a huge home should make any difference at all, as it is only the files being read that will have any effect, ie, those containing your configuration of gnome, etc etc.

I also have a similar problem. What config files need to be deleted and what settings will be lost?

---

### Post by koma77 on 2010-01-04
I'll try and move the .config to a directory on my SSD and then soft link it from my home dir and se if there is a significant speedup.

Besides .config, which config dirs/files are used during the startup of gnome?

---

### Post by ajgreeny on 2010-01-04
Several folders and files depending on your actual setup, and what you have running at start of session, ie in Startup Applications.

Certainly things in ~/.gconf, ~/.config, possibly also in ~/.gnome and ~/.gnome2, and there may also be some .xxxrc files that are needed, as well, but I still think that there must be some other problem, and depends on what you mean by "slow login".

If you can't have your desktop configured as you want it, it will be much less useful to you that just waiting a few seconds for config files to load.

---

