---
title: "Blank screen after fresh install"
date: 2011-01-09
forum: General Help
---

### Post by Smipims on 2011-01-09
Background: I installed ubuntu inside windows 7.  Everything worked well except the wireless drivers were giving me a problem so I decided to give ubuntu its own partition.  Uninstalled ubuntu and did the cd-less install.

Now: I choose ubuntu on bootup.  It says "Completeing the Ubuntu installation..." etc.  Counter goes to 0.  Screen turns black and nothing happens.  I've let it sit for 15+ minutes multiple times and nothing's come up.  What's the deal?  Why did it work before?  How do I fix it?

Computer: hp tm2-2150us notebook.  Windows works fine.

---

### Post by Smipims on 2011-01-09
Anyone have any ideas?

---

### Post by ZebaSz on 2011-01-09
You mean an "Ubuntu" entry in the MBR? That's most likely an error from Wubi, the entry was not deleted on uninstall.
However, I'm surprised that GRUB didn't appear. There should be no "Completeing the Ubuntu installation..." message. Are you sure you installed Ubuntu properly, and didn't cancel it half-way through the installation?

---

### Post by Smipims on 2011-01-09
> **ZebaSz said:**
> You mean an "Ubuntu" entry in the MBR? That's most likely an error from Wubi, the entry was not deleted on uninstall.
However, I'm surprised that GRUB didn't appear. There should be no "Completeing the Ubuntu installation..." message. Are you sure you installed Ubuntu properly, and didn't cancel it half-way through the installation?

I'll go back into windows to double check the uninstall.  And I'm fairly sure it installed properly.  I'm still a newbie, so any tips on fixing it?

---

### Post by ZebaSz on 2011-01-09
What I meant is, Wubi did uninstall, but it didn't delete the MBR entry, which is a commonly seen bug.
I think what you might need is to boot from the Live CD and restore GRUB. I'm not that much of an expert, though, so I'm not sure how to do it. Maybe you can google that, or someone else here can give you a hand.

---

