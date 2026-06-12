---
title: "File Date Modified Field - how to reset"
date: 2009-06-29
forum: General Help
---

### Post by MSwal2846 on 2009-06-29
Here is my environment:

  Running Ubuntu 9.04 on a Lenovo X200 thinkpad with 2G of memory

  I have running Windows 7 under Virtualbox v2.2.4 r47978

My situation:

Windows 7 McAfee (antivirus) has been complaining for several weeks that it hadn't had a complete scan of the system.  Finally, I went ahead and let it do it's scan.  I discovered that it not only scanned the files on the Windows 7 side, but it also scanned the files that I had shared via virtualbox on the Linux side.   The problem is that McAfee reset the modified date on the Linux side for each and every file to 1913-05-09 05:38:01.  (Lovely, right?)  It did this for only the files (not the directories)

My question:

I have a fairly recent backup of all of these files.  I could restore these files and get back the time stamp, I think.  I was wondering if there was any other way...

Thanks for any suggestions!
Mark

---

### Post by Celauran on 2009-06-29
If you need to get back the original timestamps, you may need to use your backups. If you just want to set the timestamps to something sane, you could use touch. For instance, navigate to that directory and type:

```
for i in *; do touch "$i"; done
```

This will set the date of all files in that directory to today. You can poke though man touch if you want to tweak the date/time a little more. You could also combine this with find to do it recursively through any subdirectories.

---

### Post by MSwal2846 on 2009-06-29
Mmm, wonder if I could use it to ping off of my backup and then reset the date ....

---

