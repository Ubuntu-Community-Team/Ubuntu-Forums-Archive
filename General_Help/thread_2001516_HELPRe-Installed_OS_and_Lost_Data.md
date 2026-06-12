---
title: "***HELP***Re-Installed OS and Lost Data"
date: 2012-06-11
forum: General Help
---

### Post by Dead_$partan on 2012-06-11
Hi,

I hope someone can help me please.  I had Windows 8 consumer preview installed on an old laptop but decided to put Linux back on.  I used 10.04 but I forgot to backup some family photos before re-installing, can anyone advise how I can recover these files?

Thanks

---

### Post by roelforg on 2012-06-11
If you are lucky enough that the data hasn't been overwritten, you might be able to get some data back as long as you know the old partition layout.
But first: Don't boot from the HD anymore!
Use the install cd (if you don't have it anymore, burn it from another computer) to boot the live env.
There should be enough online about data recovery.

---

### Post by wilee-nilee on 2012-06-11
> **Dead_$partan said:**
> Hi,

I hope someone can help me please.  I had Windows 8 consumer preview installed on an old laptop but decided to put Linux back on.  I used 10.04 but I forgot to backup some family photos before re-installing, can anyone advise how I can recover these files?

Thanks

Testdisk is commonly suggested.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Dead_$partan on 2012-06-11
Thanks for the responses.  Other than install the OS and put a video driver on, I haven't done any other modifications to the system so hopefully this will still be recoverable.

I have used test disk to recover partitions before so I hope this will work, it is pictures of my new born daughter :-(+

Thanks.

---

### Post by roelforg on 2012-06-11
> **Dead_$partan said:**
> Thanks for the responses. Other than install the OS and put a video driver on, I haven't done any other modifications to the system so hopefully this will still be recoverable.
 
I have used test disk to recover partitions before so I hope this will work, it is pictures of my new born daughter :-(+
 
Thanks.
 
Feel for ya man.
 
It doesn't matter what you've done on the hd, where data was written matters.
ntfs (windows default fs) fragments, meaning that it writes parts of the files on different locations.
This could result in the file being for one third on the beginning of the disk and the rest scattered around the disk (it's an example, it's very common to have a file scattered all over the disk), by installing (or writing) anything to the disk you might've destroyed some fragments which you can't fix.
Don't you have some other place where those pictures could be? Maybe still on the camera? (believe me, that saved my a** once or twice)

---

