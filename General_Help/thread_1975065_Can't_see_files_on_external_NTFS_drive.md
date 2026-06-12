---
title: "Can't see files on external NTFS drive"
date: 2012-05-06
forum: General Help
---

### Post by Sith Lord Kyle on 2012-05-06
This is an odd problem I've not seen before.  We were moving files to an external NTFS drive just fine.  They folders and files were visible.

We unmounted the drive and plugged it into another Ubuntu machine and it mounted.  However, when opened, it said there were 0 files but the appropriate amount of space was used.  They are definitely there.

Both machines are set up identically: hardware, version of Ubuntu, installed software, etc.

Any ideas why they aren't visible?

---

### Post by IparryU on 2012-05-07
> **Sith Lord Kyle said:**
> This is an odd problem I've not seen before.  We were moving files to an external NTFS drive just fine.  They folders and files were visible.

We unmounted the drive and plugged it into another Ubuntu machine and it mounted.  However, when opened, it said there were 0 files but the appropriate amount of space was used.  They are definitely there.

Both machines are set up identically: hardware, version of Ubuntu, installed software, etc.

Any ideas why they aren't visible?

Open disk utility
Find your hard drive:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=217453&stc=1&d=1336370883[/IMG]

Then click 'Mount Volume'

You may have to do something in the fstab file (correct me if I am wrong) but dont try if you are not sure... I am not sure myself so I just go to disk utility and mount if needed be.

Hope I was of some help.

---

### Post by Sith Lord Kyle on 2012-05-09
> **IparryU said:**
> Open disk utility
Find your hard drive:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=217453&stc=1&d=1336370883[/IMG]

Then click 'Mount Volume'

You may have to do something in the fstab file (correct me if I am wrong) but dont try if you are not sure... I am not sure myself so I just go to disk utility and mount if needed be.

Hope I was of some help.

Thanks for the reply.  We tried mounting via Terminal, but no go.  Disk Utility didn't seem to do anything different either.  And the fstab file, I believe is only really for automatic mounting.

However, when plugged into a Windows system, the files show up fine... just not in Linux anymore.  I'm guessing I'll just have to copy them off in Windows, reformat, then put them back on.

---

