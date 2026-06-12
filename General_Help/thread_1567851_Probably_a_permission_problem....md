---
title: "Probably a permission problem..."
date: 2010-09-04
forum: General Help
---

### Post by violin.yanev on 2010-09-04
Hello,

Hopefully this is the right place to put this in... I am trying hard to repair my Ubuntu installation, since it is kind of... unstable in the past few weeks. I suspect it is a general permission/user/group problem since it affects several, seemingly not related areas.

Firstly, sometimes it fails to load the alsa sound drivers. Trying to restart them in the command prompt says "...no permission to open /dev/snd/seq.." or similar. Sometimes the sound works, but at some point (which is random) they stop working.

Secondly, when the sound fails, the computer refuses to shut down or restart. Upon using these commands, ubuntu just logs out. I tried to check the kernel log, but it says nothing relevant to the problem (or I fail reading it).

Finally, when I try opening the "Users and groups" panel in system->administration, it does NOT prompt me for a password, and the buttons in the panel don't work (probably because I dont have permission).

And one more thing - I can't mount my other HD-partitions in the Places-menu - it says "No permission" or similar. However, I can sudo-mount them in the console. Formerly I used to mount them from "Places" and I have not change any permissions...

Do you guys have any ideas where the problem might be?

---

### Post by buddy_t on 2010-09-06
Have the same problem with Lucid after updating last night, rebooted, cannot mount by clicking other drives that I used prior to reboot says unable to mount c (or D) Not Authorized. I go to user manager and can't change any of the settings or add another user.  I reinstalled it this time after it started this last week. This must be a bug.  Any ideas?  I have Windows 7 installed on a different partition.  I can't even click and mount an external hard drive.  Also cannot restart or shutdown, just returns to the initial log in page. Thank you.

---

