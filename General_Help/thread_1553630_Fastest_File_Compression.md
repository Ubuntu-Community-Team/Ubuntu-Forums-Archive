---
title: "Fastest File Compression"
date: 2010-08-15
forum: General Help
---

### Post by ffixcollector on 2010-08-15
I have a new i3 processor, and was wondering if there were any archive programs out there there that support multi cores.

---

### Post by linux18 on 2010-08-15
I believe all of the GNU tools (tar,sed,zip,dd,etc) have multithreaded support. 
However, I've noticed that it never takes full advantage of the cpu power, I suggest using either squashfs (great multithreaded support) or peazip (FREEARC ftw!)

---

### Post by ffixcollector on 2010-08-15
I want an archive format that supports "Recovery record" or some sort of error redundancy. I went with .rar, is there a better format out there?

---

### Post by linux18 on 2010-08-15
rar and freearc have the best error recovery, 7z and freearc have the best compression, bz2 has the fastest compression, freearc has the fastest decompresssion (based on ratio)

---

### Post by ffixcollector on 2010-08-15
is there a way to utilize all cores with rar?

I havn't heard of freeARC, Is it new?

---

### Post by linux18 on 2010-08-15
rar is multithreaded, but like many programs 'generic multithreading' doesn't utilize all of the available cpu power. 

freearc and nanozip are relativaly new (freearc is a continuation of an older compression format known for grreat compression ratios) nanozip is the compression program of the future, it has the highest ratios and very high compression speed, but it's still unstable

---

### Post by ffixcollector on 2010-08-15
As I'm sure many people would ask, what is the best way to create a highly compressed archive with error recovery in the shortest amount of time?

1) I will not be using my PC much while I am archiving, so the more the cpu (i3-530) is utilized the better.
2) I need error recovery
3) And a format that will be supported well into the future.

What would you suggest? I will most likely be archiving a few hundred gigabytes worth of data.

---

### Post by linux18 on 2010-08-15
either rar or arc (freearc) will suit your needs, rar is better supported but freearc, well just look at their most recent news story:
[http://www.freearc.org/News.aspx](http://www.freearc.org/News.aspx)

---

### Post by ffixcollector on 2010-08-16
FreeARC won't run. I ger error:
```
freearc: error while loading shared libraries: 
libgmp.so.3: cannot open shared object file: No such file or directory

```

---

### Post by linux18 on 2010-08-16
Are you using ubuntu 64-bit? freearc doesn't run on 64-bit yet (it's coming soon hopefully) if you really want it you'll have to  dual boot with a 32-bit os (virtualization has way too much overhead) looks like you'll have to stick to rar until freearc64

---

### Post by ffixcollector on 2010-08-18
dang, would I need freearc installed to unpack the archive?

---

### Post by linux18 on 2010-08-18
yes, you would need freearc to unpack a freearc archive. let me guess, you now have a bunch of freearc archives to unpack? In which case I need a little time to build a workaround

---

### Post by ffixcollector on 2010-08-19
If I create an archive with FreeArc, Will I need FreeArc to decompress it?

---

### Post by linux18 on 2010-08-19
> **ffixcollector said:**
> If I create an archive with FreeArc, Will I need FreeArc to decompress it?
yes

---

### Post by ffixcollector on 2010-08-19
Do I need FreeArc to _decompress_ the archives?

---

### Post by linux18 on 2010-08-19
You need freearc to decompress archives with the ".arc" extention

---

### Post by ffixcollector on 2010-08-19
how does FreeArc compare to PeaZip? Is it as fast? Does it support a Recovery Record? Will it extract FreeArc archives?

---

### Post by linux18 on 2010-08-19
peazip is a manager for freearc and many other compression formats, just like the archive manager is a frontend to zip, tar, etc.

---

### Post by ffixcollector on 2010-08-19
> **linux18 said:**
> peazip is a manager for freearc and many other compression formats, just like the archive manager is a frontend to zip, tar, etc.

**Correct me if I'm wrong**
So, FreeArc is a compression program that has reworked the old .arc format to achieve faster and tighter compression, and also added features including a "recovery record" and encryption. In order to do this the FreeArc program used multiple compression algorithms depending on the file type. The final archive is a .arc format that can only be compressed/decompressed by FreeArc, Peazip, and any other programs that claim to support FreeArc archives?

---

### Post by linux18 on 2010-08-19
> **ffixcollector said:**
> **Correct me if I'm wrong**
So, FreeArc is a compression program that has reworked the old .arc format to achieve faster and tighter compression, and also added features including a "recovery record" and encryption. In order to do this the FreeArc program used multiple compression algorithms depending on the file type. The final archive is a .arc format that can only be compressed/decompressed by FreeArc, Peazip, and any other programs that claim to support FreeArc archives?
exactly

---

### Post by Giorgio tani on 2010-08-20
> **ffixcollector said:**
> So, FreeArc is a compression program that has reworked the old .arc format 
FreeArc's .arc format is not the old SEA's .arc format (designed by Thom Henderson), just shares the same extension.
It was designed ground up by Bulat Ziganshin to feature efficient compression, recovery records and strong encryption, and released as Open Source to be free and not encumbered by patents.

As for I know the SEA's .arc format was not made free and was largely abandoned in favour of the then rising zip format which come out with less restrictive businness model, better compression and less technical limitations.
It is probably still supported by some archiving software, but due to the original licensing (if it has not changed) I doubt there are Open Source software supporting it.

---

### Post by gearond on 2011-06-22
I'm using nanozip as I type to compress a partition image. So it has no extensions to go by. Perhaps it will autodetect the content. I set up 2 threads and 2 gig of memory, otherwise it's all defaults.

The partition image is 137 gb. It's looking like it will take about 20 hours to do it. This is an I5 2.4 ghz with 8 gig of ram and 64bit Ubuntu.

---

### Post by gearond on 2011-06-23
Actually it failed at 5% into the compression. Not sure why yet. Got an error of:

Internal error: 7834538! email sami (at) nanozip.net

emailed him, now going to set up ubuntu_32bit on vbox on my 64 bit Ubuntu 10.10 and try FreeArc 0.666 (only works in 32 bit). I may actually try nanozip in that, since I can't believe it was made for 64 bit.

---

