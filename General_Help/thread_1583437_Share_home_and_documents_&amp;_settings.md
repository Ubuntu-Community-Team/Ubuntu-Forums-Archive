---
title: "Share /home and \documents &amp; settings?"
date: 2010-09-27
forum: General Help
---

### Post by drfox on 2010-09-27
One of my employees has got a new laptop with Windows 7 on it. She has asked me to "set it up."  What's the best way to dual boot so that her Windows "Documents and Settings" and Linux /home are on the same partition? Is that possible? Can I just point her Documents to \sda6\her_name (or whatever it is)? Will that work for other Windows users so long as they have the identical name in Windows and Linux?

Thanks.

Larry

---

### Post by rhoparkour on 2010-09-27
I believe it IS possible. I have seen people do this:

Two partition for system files (installed programs, OS stuff in general):
1 partition for Windows 7 operative system
1 partition for Ubuntu operative system

And another one just for the saved files:
1 partition that is usable by windows as My Documents and is used by Ubuntu as home

And the swap partition, of course.

I don't know how to do this, but that's the way I've seen it...

---

### Post by Mark Phelps on 2010-09-27
> **drfox said:**
> One of my employees has got a new laptop with Windows 7 on it. She has asked me to "set it up."  What's the best way to dual boot so that her Windows "Documents and Settings" and Linux /home are on the same partition? Is that possible? 

No that is not possible.  The Linux /home partition needs to be on a Linux filesystem so it can manage permissions properly.  What you are calling Documents and Settings (which actually no longer exists as such under Win7) has to be on an NTFS filesystem so Win7 can manage its permissions properly.

Furthermore while Ubuntu CAN read NTFS partitions, Windows can NOT read Ext4 partitions.  So, there's no way files in /home in Ubuntu can be shared with Windows on the same machine.

> Can I just point her Documents to \sda6\her_name (or whatever it is)? Will that work for other Windows users so long as they have the identical name in Windows and Linux?
If you mess around with Win7 user folders using, Linux, you run the risk of hosing up Win7 and making it unbootable. Bad idea.

If you just want to have a shared set of data files, the best approach is to create a new NTFS partition, copy the files there you want to share, and mount that partition in Ubuntu.

---

### Post by WorMzy on 2010-09-28
It's possible to use fstab to automatically mount the Windows partition at boot, and then bind the Windows Documents directory over the top of the Linux Documents directory. Etc.

However, due to limitations with the NTFS filesystem on Linux, it wouldn't work well with multiple users. You would need to set fstab to give everyone with mounted documents read and write permissions to the NTFS partition; therefore effectively making everybody's documents publicly readable/editable/deletable, as well as opening up the Windows system files to the same treatment.

In short: it's not advisable.

You can use a shared partition, as Mark suggested, and use the fstab method with that instead. That way at least the Windows system files would be more-or-less untouchable (to all except sudo users at least). You still have the problem of public documents though.

---

