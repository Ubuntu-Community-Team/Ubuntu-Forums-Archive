---
title: "Permissions error / cannot boot"
date: 2011-08-05
forum: General Help
---

### Post by substanceneil on 2011-08-05
Recently, I installed 11.04 64-bit in an sda7 partition alongside my existing 11.04 32-bit system on sda5.  Both installations were working quite well.  (I was trying to assess which is better for my Thinkpad X220 i5-sandy bridge).

Using the 64-bit sda7 boot partition, I found that I could mount sda5 (to access my home folder, etc) but only read only.  After doing some research, I ran the following command from the 64-bit (sda7) boot:

sudo chown -R dngr:dngr /media/sda5

Note that in both systems, my username is dngr.  after remounting, I did have read/write access to sda5.

Now I cannot boot up in the 32-bit sda5 any longer.  Looks like the permissions change is causing a hold host of errors as ubuntu loads.

1) How do I undo the ownership change?  Who owned the sda5 partition before I assigned it to dngr?

2) How do I accomplish my goal of allowing read/write access to my home files on sda5?  In retrospect, I think I might have been better off trying

sudo chown -R dngr:dngr /media/sda5/home/dngr

Would that have been better?  Is there a way for both systems to share the same home folder, or would that screw with my program settings?

Thanks.

My fstab setings are pasted below:
--------/etc/fstab----------
# / was on /dev/sda7 during installation
UUID=afe1b267-c179-4fce-aae3-ddca725d31f1 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda6 during installation
UUID=74af83a5-8c02-469c-bc4f-ace4a0a8ba1a none            swap    sw              0       0
# /dev/sda5 is the root partition for x86 32bit installation
/dev/sda5 /media/sda5     ext4    defaults,user        0       2

---

### Post by syntr on 2011-08-05
Ouch, yeah, by default most of the files outside of /home are owned by "root". You might want to try setting them back to root:root and seeing if that fixes your problem. I'm not sure if there's a way to undo it on a file by file basis, and it's quite possible you borked the 32-bit install by doing that.

In the future you're going to want to only take ownership of your home directory.

---

### Post by blind2314 on 2011-08-05
> **substanceneil said:**
> Recently, I installed 11.04 64-bit in an sda7 partition alongside my existing 11.04 32-bit system on sda5.  Both installations were working quite well.  (I was trying to assess which is better for my Thinkpad X220 i5-sandy bridge).

Using the 64-bit sda7 boot partition, I found that I could mount sda5 (to access my home folder, etc) but only read only.  After doing some research, I ran the following command from the 64-bit (sda7) boot:

sudo chown -R dngr:dngr /media/sda5

Note that in both systems, my username is dngr.  after remounting, I did have read/write access to sda5.

Now I cannot boot up in the 32-bit sda5 any longer.  Looks like the permissions change is causing a hold host of errors as ubuntu loads.

1) How do I undo the ownership change?  Who owned the sda5 partition before I assigned it to dngr?

2) How do I accomplish my goal of allowing read/write access to my home files on sda5?  In retrospect, I think I might have been better off trying

sudo chown -R dngr:dngr /media/sda5/home/dngr

Would that have been better?  Is there a way for both systems to share the same home folder, or would that screw with my program settings?

Thanks.

My fstab setings are pasted below:
--------/etc/fstab----------
# / was on /dev/sda7 during installation
UUID=afe1b267-c179-4fce-aae3-ddca725d31f1 /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda6 during installation
UUID=74af83a5-8c02-469c-bc4f-ace4a0a8ba1a none            swap    sw              0       0
# /dev/sda5 is the root partition for x86 32bit installation
/dev/sda5 /media/sda5     ext4    defaults,user        0       2

Ouch..that's unfortunate :/ 

There isn't an easy way to fix the permissions. You should NOT change everything to root:root, because that isn't correct (some files are owned by bin, some by sys, etc). The best option would be to save any data you need personally and re-install. I know it's painful, but fixing every file/directory permission under / is a losing battle.

---

### Post by WorMzy on 2011-08-05
> **substanceneil said:**
> sudo chown -R dngr:dngr /media/sda5


Short answer: Reinstall.

Long answer: You've buggered it. It'd take several hours to fix manually, with no guarantee that you've got the permissions right again. Reinstall.

Make sure that you back up any important documents first, etc.

---

### Post by JASONFUSARO on 2011-08-05
> **blind2314 said:**
> Ouch..that's unfortunate :/ 

There isn't an easy way to fix the permissions. You should NOT change everything to root:root, because that isn't correct (some files are owned by bin, some by sys, etc). The best option would be to save any data you need personally and re-install. I know it's painful, but fixing every file/directory permission under / is a losing battle.


I ran into the same problem from a straight install of Archbang and another distro  selecting a separate /home and could not boot square one and changing the permissions or user didn't do anything to improve the still unbootable situation. I am leaving it on a backburner till I hit on the solution. 

Might the solution light in setting up the users ability to access drives or something be  the underlying cause?

Does something have to be checked in users accounts to allow for such disk access, because you do need certain rights to access audio, cron, and so forth?

---

### Post by substanceneil on 2011-08-05
You've all convinced me that I should salvage my data and reinstall... luckily I have this 64-bit installation working quite well.

Thanks.
n

---

### Post by blind2314 on 2011-08-05
> **substanceneil said:**
> You've all convinced me that I should salvage my data and reinstall... luckily I have this 64-bit installation working quite well.

Thanks.
n

Sorry that it had to come to that. At least next time you'll be extra careful :D Remember, anytime you're doing any blanket changes (a -r switch on most commands should prompt extra inspection on your part), make sure you're either 100% sure of what you're doing or you have a recent backup.

---

