---
title: "USB devices not mounting when switchign users / logging on with different user"
date: 2010-02-28
forum: General Help
---

### Post by cwb1627 on 2010-02-28
Hello,

Sorry for the bother - I am new to this...
I have an external USB drive that is NTFS.  It mounts fine under my account and my wife's, but only if I fully shut-down the computer between switching.
While switching users or logging out then in with a different account it will not mount the drive.

I am not sure what to do... but we both access data from the same drive.

Thanks in advance for the time and effort - appreciate any help.

---

### Post by dcstar on 2010-02-28
> **cwb1627 said:**
> Hello,

Sorry for the bother - I am new to this...
I have an external USB drive that is NTFS.  It mounts fine under my account and my wife's, but only if I fully shut-down the computer between switching.
While switching users or logging out then in with a different account it will not mount the drive.

I am not sure what to do... but we both access data from the same drive.

Thanks in advance for the time and effort - appreciate any help.

And you do unmount it before switching users, don't you?

---

### Post by cwb1627 on 2010-03-03
I have figured that one out... had to brush up on my Linux a bit... but now I have another item...  Every once and a while the /dev/sdb* changes... can I manually force it to remain constant (almost as if it is a random generated number).  I am writing an S and K script in the rc2.d to take care of the mount / unmount but having issues with determining the /dev path.

Thanks in advance
Chris

---

