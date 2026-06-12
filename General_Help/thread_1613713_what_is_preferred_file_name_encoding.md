---
title: "what is preferred file name encoding?"
date: 2010-11-04
forum: General Help
---

### Post by pieter_dt on 2010-11-04
Hi,

I have a disk (JFS formatted) which contains files with accented characters. Those characters show garbled in my terminal. I went searching and found the convmv tool to change the encoding of file names. This tool says that the filename is already UTF-8 encoded. When i convert it to iso-8859-1, then the accented characters show correctly.

My question now: i read everywhere that ISO8859-1 is something of the past, for older machines etc... nowadays you should use UTF-8.
Apparently my filenames are UTF-8 encoded, so that is fine. But they show garbled (and ok when converted to iso8859-1). Thus apparently my system is doing something wrong to show me the filenames (something like expecting iso, and garbling utf along the way)

There are 2 things i can do: 
* convert the filenames to iso8859
* fix the system to show utf-8 encoded filenames correctly. (preferred)

Also, when i adjust my locale to en_us.utf8, then an é shows as Ã©, whereas when the locale is C, it shows as 4 question marks.

any ideas?

thanks,

pieter

---

### Post by dcstar on 2010-11-05
> **pieter_dt said:**
> 
........
any ideas?

thanks,

pieter

AFAIK you can mount filesystems with specific encoding, and you also have the default encoding in your own system to deal with.

If the files already on the disk were created under one codepage and incorrectly detected - or your system doesn't have that codepage installed - then you may have issues, but I am nowhere near 100% sure on this.

---

