---
title: "How best to solve a full hard drive?"
date: 2010-01-18
forum: General Help
---

### Post by caffienated on 2010-01-18
Hello!

Sorry for post that probably sounds ridiculous, obviously I need to delet some files!

Problem is that my HDD only has 96MB free before booting the installed OS (current up to date Xubuntu)

Clearly I should never have allowed it to get so full, but now it won't let me delete anythign even, claiming there is insufficient space.  I assume this means it wants to stick it in teh waste bin, and there isn't enough space.

Is it possible to (temporarily!) disable the wastebin from xfce command line?

Plan B:  Is it feasible to boot from live CD and then mount the HDD partition and some3how supply credentials for the user account with the problem?

All the bulk is in my Home folder (No!  Really?), and I do know my own login and pwd... 

I don't have a bootable Flash drive already made, and my poor old laptop's only got USB1 anyway, so it might actually be faster using CD!  ^_-

Hope there's a sensible workaround!  There's no irreplaceable data if I *do* need to just kill the partition and reinstall, but there are a few torrents that were a pain in the @ss to complete!

Cheese!

---

### Post by synapsys on 2010-01-18
Easiest thing to do would be to boot a live cd. Mount your home folder (from places) and delete files from there. The live cd runs in memory and from the cd, so it's not worried about your full hard drive.

---

### Post by michy99 on 2010-01-18
If you boot from a live cd, you can open a nautilus session as root.```
gksudo nautilus
```Then you can delete whatever you need to. Use Shift+Delete to bypass the trash and actually delete.

---

### Post by caffienated on 2010-01-18
Thks! I'll try the gksudo approach...

I actually made a new copy of the live cd specially for the purpose a few days ago but while HDD mounted ok, couldn't see 'my' files ... presumeably cos I wasn't logged on as me.

I presume what you're describing temporarily make me super-user, and hence able to delete anything no matter where it is.

Might see about shift-deleting from regular boot though... live cd is S-L-O-W on that lappy (p3 1200, 256mb... ;))

One day I'll stop being uber tight and ebay some cheapo SODIMMS for it!

Thanks!

---

