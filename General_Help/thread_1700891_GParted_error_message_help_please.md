---
title: "GParted error message help please?"
date: 2011-03-05
forum: General Help
---

### Post by Bealz on 2011-03-05
[LEFT]*Accounting clusters...*
[/LEFT]
* Cluster accounting failed at 3339 (0xd0b): extra cluster in $Bitmap*

*3 other cluster errors listed , then:..

[I]Filesystem check failed! Totally 4 accounting cluster mismatches,
ERROR NTFS is inconsistant. Run Chkdsk /f on Windows then reboot it TWICE![/I]

Fine, so I ran chkdsk /f , it found no errors. I downloaded the Seagate hard drive check software, it found no errors.

I can open and access my files in ubuntu on that partition, no problem.

I just can't make GParted finish off the unallocated space on the other partition and add it to that one.
Any ideas? :confused:

---

### Post by srs5694 on 2011-03-05
It sounds like you're trying to resize an NTFS partition. If so, I recommend you try a Windows resizing utility. This ability is built into the Windows disk partitioner for some versions of Windows, so check there, or look for third-party software to do the job. If it's a boot partition, a Windows tool is likely to be a little safer, anyhow, since Windows is very finicky about the location of files on its boot partition, and Windows tools don't always preserve those locations in a way that Windows likes.

---

### Post by seawolf167 on 2011-03-05
If its an NTFS formatting error, you'll also want to get

```
sudo apt-get install ntfsprogs
```then rerun GParted and see if that helps.

---

