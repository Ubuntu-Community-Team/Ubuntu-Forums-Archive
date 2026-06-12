---
title: "Removing items in GRUB"
date: 2011-01-02
forum: General Help
---

### Post by Ron W on 2011-01-02
I keep updating Ubuntu and have a long list of upgrades in the GRUB menu that I would like to clear out.

The items go from 'Ubuntu, with Linux 2.6.32-21-generic' up to '...32-27...'. There is also a 'recovery mode' item as well with each of these items.

How can I remove these items from GRUB?

Are there other software items that I can remove from my HD to free up space? If so, where are they? I assume I use 'sudo' to remove these.

How many of the above should I remove?

Thanks

Ron

---

### Post by Elfy on 2011-01-02
Open synaptic - search for linux-image - mark the old kernels for complete removal - I would suggest that you keep current and previous.

That will also run update-grub so you'll have less in the menu.

You can run ```
sudo apt-get autoclean
``` to remove old packages from the apt cache. apt-get clean will remove all packages from the cache.

You could install and run bleachbit and see what you can clear - but be careful.

---

### Post by ttakun on 2011-01-02
Assuming that you have GRUB2 installed (if the command **grub-install -v** gives something greater than 0.97 it will be GRUB2) in your system ...
What I usually do is ...
Go to System - Administration - Synaptic Packet Manager and look for:

**linux-image** and **linux-headers**, and mark for uninstalling the version you want to get out from your GRUB menu. It'll automatically regenerate the GRUB menu as it executes update grub

You could also look for for the versions of the kernel you want to delete 2.6.XX-XX

---

### Post by sammiev on 2011-01-02
I found [Ubuntu Tweak]("http://ubuntu-tweak.com/") to be a great aid for stuff like this. GL :)

---

### Post by Elfy on 2011-01-02
> **sammiev said:**
> I found [Ubuntu Tweak]("http://ubuntu-tweak.com/") to be a great aid for stuff like this. GL :)

Yep - I tend to not use it though - I'd certainly not install something to just clean some space when there's ways to do so without :p

---

