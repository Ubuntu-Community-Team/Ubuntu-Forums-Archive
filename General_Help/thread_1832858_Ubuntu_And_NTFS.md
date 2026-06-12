---
title: "Ubuntu And NTFS"
date: 2011-08-25
forum: General Help
---

### Post by carmenat250 on 2011-08-25
Later today, I'm going to be working on a Windows 7 computer and saving files to a USB stick that is formatted as NTFS.  The files on the USB stick will be MS Word docs.

I believe I read that Linux can't read NTFS, so I would I access these files on my Linux System?

---

### Post by sanderd17 on 2011-08-25
Linux can read and write to NTFS, just be sure that your filenames don't contain weird characters.

---

### Post by the-new-x on 2011-08-25
> **sanderd17 said:**
> Linux can read and write to NTFS, just be sure that your filenames don't contain weird characters.
And since windows doesn't allow you to save it with weird characters, I think it is all going to be fine!

---

### Post by seawolf167 on 2011-08-25
As said previously, you won't need to worry - Ubuntu (and *nix) can read/write to NTFS formatted partitions. The only issue you may run into to is using OpenOffice or LibreOffice to edit MS Word files - the formatting doesn't always transfer over 100%.

---

### Post by Sef on 2011-08-25
As someone who has saved files on a USB stick with Ubuntu, and then opened the files on a Windows machine, no problem will exist to open the document. However, as has been mentioned, formatting can be different. 

Note:  Ubuntu Linux has been set up to read and write to NTFS. Not all Linux distros can do that out of the box.

---

### Post by SavageWolf on 2011-08-25
I think you should format the stick to FAT. I think I read somewhere that NTFS causes a lot more writes and wears the drive down faster, though I could have just made that up or something...

---

### Post by seawolf167 on 2011-08-25
> **SavageWolf said:**
> I think you should format the stick to FAT. I think I read somewhere that NTFS causes a lot more writes and wears the drive down faster, though I could have just made that up or something...

This is due to [journaling ]("http://en.wikipedia.org/wiki/NTFS#USN_Journal")on the drive, though on modern flash drives it isn't too much of any issue any more since they can handle so many reads/writes.

---

### Post by Morbius1 on 2011-08-25
> **sanderd17 said:**
> Linux can read and write to NTFS, just be sure that your filenames don't contain weird characters.[QUOTE=the-new-x;11185943]And since windows doesn't allow you to save it  with weird characters, I think it is all going to be fine!
[/QUOTE]
Ah, but Linux can add funny characters to an NTFS partition that Windows can't deal with. That's why the windows_names option was invented:
[http://www.tuxera.com/community/ntfs-3g-manual/](http://www.tuxera.com/community/ntfs-3g-manual/)

---

