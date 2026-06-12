---
title: "Ubuntu 10.04 - 'Date Modified' changed on file copy to NTFS partition"
date: 2011-07-06
forum: General Help
---

### Post by Steve Francis on 2011-07-06
[B]Prior to making a fresh install of 10.04, I made a back up of all my documents by copying them to a NTFS partition. I did this my selecting files in File Browser, then right clicking and selecting the Copy command.

When I came to move the files back after the fresh install, I was mortified to find that all the file modification dates had changed to the date I copied them!

I've lost all the original file dates, which was the principal way I sorted my files.

I guess there's no way of getting it back? It seems that Linux does not store File Creation dates either so I'm stuffed. :mad:
[/B]

---

### Post by Ad@m on 2011-07-06
Unfortunately I can't replicate your outcome. Moving or copying files from my NTFS partition to my Ubuntu EXT4 partition is preserving the modified date.

How did you move the files from your NTFS partition?

---

### Post by ajgreeny on 2011-07-06
I seem to remember in a previous verrsion of ubuntu that this was a bug that was quickly sorted out after release, but I thought it was some time before 10.04, so I am baffled why this has happened.  I have not been able to see this happen on my 10.04 either so just like Ad@m, find this somewhat surprising.

How did you copy the files?  Using nautilus drag and drop?

---

### Post by Steve Francis on 2011-07-06
> **Ad@m said:**
> Unfortunately I can't replicate your outcome. Moving or copying files from my NTFS partition to my Ubuntu EXT4 partition is preserving the modified date.

How did you move the files from your NTFS partition?

My partition was Ext3. (I had upgraded from Jaunty-->Karmic-->Lucid and then had some problems so went for a fresh install. Prior to the fresh install though, my Linux partitions were Ext3.)

I copied all files using the File Browser GUI ("Select All" then right-click and Copy, navigate to NTFS partition and Paste).

I see that others have experienced similar problems on earlier Ubuntu versions:
[http://adventuresinswitching.blogspot.com/2008/05/file-modification-dates-changed-in.html](http://adventuresinswitching.blogspot.com/2008/05/file-modification-dates-changed-in.html)

---

