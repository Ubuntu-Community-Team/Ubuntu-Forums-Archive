---
title: "Looking for an alternative to RAR..."
date: 2011-11-28
forum: General Help
---

### Post by PopSmith on 2011-11-28
I'm currently using RAR to compress backups of Wii games I buy but it is *_so slow_*. I'm hoping to find a faster alternative with comparable compression but have one problem, I'm hoping it's compatible with (Win)RAR...

For comparison I tried a couple other compressors and here are the results:
rar -m5:
32m24.850s File size: 2.3 GB (2477389909 bytes)

7zip using -mx9:
32m16.169s File size: 2.3 GB (2504647320 bytes)

lbzip2
14m9.110s File size: 2.3 GB (2483616486 bytes)

lrzip using -l and -p 1 (unfortunately this format is Linux-only):
06m11.257s File size: 2.3 GB (2481667764 bytes)

I know (Win)RAR supports tar.gz2 and tar.bz2 archives but AFAIK it's not possible to compress an archive and then split it with TAR. :(

I was hoping that using TAR + BZip2 would work similar to RAR but TAR doesn't support multi-volume splits with compression. :( This surprised me as I thought it would just split the archives when necessary during compression like RAR does... I know about Split but I don't want to use it as the output is not compatible with WinRAR, AFAIK.

Any suggestions?

---

### Post by mutley89 on 2011-11-28
You can use split, then reassemble the pieces with cat.  If you need to put it back together on windows some googling suggests the following at a command prompt is equivalent to cat:
```

copy /B piece1 + piece2 + piece_etc output_file.tgz

```You could then use winrar on the result.

---

### Post by PopSmith on 2011-11-30
Thanks for the suggestion, that should work and I'll probably give it a shot.

I was really hoping that there would be a compressor that is (much) quicker than RAR but supports multi-volume archives that are automatically "connected" like RAR files are. They are nice as it's easy for even those with little computer knowledge to extract the data. I think the biggest problem with what I am looking for is I want it to be compatible with Windows... (and, preferably, via WinRAR).

However, I'm thinking that RAR is the only way of doing that at the moment. :( If you (or anyone else) can think of another solution please let me know. :)

---

### Post by mastablasta on 2011-11-30
why do you need to split files? are you putting them on floppy disks? :-)
 
i am not sure if these work in linux but there are:
ACE
LHA
UC2
ARJ

---

### Post by mutley89 on 2011-11-30
> **PopSmith said:**
> Thanks for the suggestion, that should work and I'll probably give it a shot.

I was really hoping that there would be a compressor that is (much) quicker than RAR but supports multi-volume archives that are automatically "connected" like RAR files are. They are nice as it's easy for even those with little computer knowledge to extract the data. I think the biggest problem with what I am looking for is I want it to be compatible with Windows... (and, preferably, via WinRAR).

However, I'm thinking that RAR is the only way of doing that at the moment. :( If you (or anyone else) can think of another solution please let me know. :)

Are you sure that WinRAR wont handle split archives?  If not something like [7zip]("http://www.7-zip.org/") or [peazip]("http://sourceforge.net/projects/peazip/") should do.

---

### Post by PopSmith on 2011-12-01
> **mutley89 said:**
> Are you sure that WinRAR wont handle split archives?  If not something like [7zip]("http://www.7-zip.org/") or [peazip]("http://sourceforge.net/projects/peazip/") should do.

I ran the bz2 file (<filename>.iso.bz2) through Split so it produced this:
<filename>.iso.bz2.part-aa -> af

WinRAR opened part aa OK but when it finishes that part it says "Unexpected end of archive". I tried selecting all the files and clicking "Extract to specific folder" and "Extract without confirmation" but it always says "Unexpected end of archive" at the end of part aa.

---

