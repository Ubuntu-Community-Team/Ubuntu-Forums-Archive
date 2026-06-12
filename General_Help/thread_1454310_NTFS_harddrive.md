---
title: "NTFS harddrive"
date: 2010-04-14
forum: General Help
---

### Post by Gauze on 2010-04-14
I run Ubuntu 9.10 from a USB flashdrive and had some issues with NTFS filesystem harddrives.
 
I had a 500 gig external harddrive. I transferred about 5 gigs of files from my USB to the external. Next time I tried it, the drive wouldn't mount and said chkdsk needed to be ran. So I did and it was alright except for a few missing folders.
 
I thought that might have been due me handling the external a little roughly while transporting it.
 
But then, when I tried to space a bunch of files onto another NTFS harddrive, another problem occured. From Ubuntu, every seemed fine. But when I tried to boot Windows, it would complain about corrupted files in areas of the harddrive that I didn't even use. Windows recommended using chkdsk on the harddrive.
 
Are these two events related? Or am I just unlucky?

---

### Post by Mark Phelps on 2010-04-15
You're not unlucky -- these kinds of problems happen all the time.

With an external drive, the writes are buffered.  If you simply unplug the drive, you run the risk that the writes didn't actually take place.

Instead, you have to do a "safe removal" of the drive by clicking the icon on the desktop and selecting that option.  That will force the buffered writes to take place before you unplug the drive.

---

