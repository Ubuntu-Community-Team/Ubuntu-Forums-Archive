---
title: "Deleted files on NTFS using file browser"
date: 2009-10-08
forum: General Help
---

### Post by vik.casar on 2009-10-08
Hello.

This is my problem: My old hard disc (C: using win XP) went beyond repair (OS, not hard drive physically) - so i was using other disc with Jaunty (Z: ) and XP (E: ) installed to recover the files. Now, using Jauntys file  browser, i accidentally deleted some files id still like to recover. I cannot log into C: because win is damaged and im afraid that reinstall might overwrite something. I could log in from E:, however parent directory containing deleted folder in C: shows "Acces denied" - maybe because of this, "NTFS undelete" utility didnt find any files in the folder where the files used to be, and another utility "Restoration" crashed during the scan of C:. These i ran ofcourse from E:. Jaunty has no problem accesing the directory (no "acces denied), however, i lack utilities (and skill) on Ubuntu for this.

So the question is, did those utulities fail because files are beyond recovery because they were located on NTFS and were deleted by Ubuntu using ext3? Or should i rather use those programs on Ubuntu using WINE. Or maybe some ext3 recovery? Are there any Ubuntu native utilities that can scan NTFS? Im linux noob btw.

Any help and ideas? Thanks.

---

### Post by sedawk on 2009-10-08
i)
There is a linux tool called ntfsundelete.
You might give this a try. 

ii) If I remember right the reason you do not have enough
  access rights is that your XP installations use different
  (randomly created) user IDs for the XP admin account.
  To edit permissions and ownerships for NTFS drives that have
  been created with another XP instance you have to do some
  trick with XP (home edition). I think you have to boot
  in recovery mode and there might be additional steps necessary
  to get the button/tab/dialog to change these settings - they
  are not visible by default!

iii) You might be able to do ii) with a recovery/repair CD
  Check out BartPE stuff to create on.

---

### Post by vik.casar on 2009-10-08
Thank you,

I was able to gain permission in XP as you pointed out in #2. That didnt work out, unfortunately. Im afraid recovery CD will do as much good.

Now, as for undelete, during scan, i get "Segmentation fault". The listed -t filtered items so far show 0% chance of recovery. So what about the Segmentation fault? That may be the reason why one of those XP utilities crashed - fault and crash occured after one file. Does Segmentation fault mean that the files went fubar or is there a possible remedy still? Would reformat of C: leave the deleted files intact, or would they be messed up? And could it remove segmentation fault?

thanks

---

