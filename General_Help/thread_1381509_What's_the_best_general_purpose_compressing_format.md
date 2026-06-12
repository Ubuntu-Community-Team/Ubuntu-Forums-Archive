---
title: "What's the best general purpose compressing format?"
date: 2010-01-14
forum: General Help
---

### Post by mazz0 on 2010-01-14
Suppose I have a folder that may contain text documents, pictures, MP3s, video clips, all sorts of stuff.  Supposing that, within reason, I'm not too bothered how long it takes to compress and uncompress them.  And suppose I don't care if it's free or open source (well, has to be free as in beer).  What's the best compression format/algorithm (whatever it is that I install in Synaptic and choose from the drop down menu in the compression tool) I should use?

---

### Post by Revolutionary101 on 2010-01-14
I would suggest compressing it into a .tar.lzma or a .lzma. It may take a while to compress/decompress but it has a good compression ratio.

---

### Post by Enigmapond on 2010-01-14
They are all basically the same except the encryption is different. I use both .rar and 7zip as they have the best encryption of them all. Really depends on what you want to use it for.

---

### Post by jamesbarnhill on 2010-01-14
Linux uses tar.gz for most things, zip is more universal though.

---

### Post by prshah on 2010-01-14
> **mazz0 said:**
> What's the best compression format/algorithm 

I've always used rar formats whenever multimedia compression is involved; I've found no significant differences for any other types of files.

I suggest you use the rar format; though I've recently been hearing good things about [NanoZip]("http://www.nanozip.net/download.html"), never tried it though, rather chary of new formats since the [WinZix]("http://torrentforum.lamewire.info/viewtopic.php?t=666") days. (A legacy of my Windows days).

---

### Post by mazz0 on 2010-01-14
Wow, thanks guys, a lot of responses there! :)

jamesbarnhill - I must admit I kinda like deliberately not using zip just to annoy people on Windows :p

Right, I'm about to upgrade my AMD graphics card drivers, so if you never hear from my again you know why...

---

### Post by falconindy on 2010-01-14
gzip, bzip, and lzma are the only 3 worth mentioning.

- gzip is the fastest but has the lowest compression of the 3.
- bzip is the slower but has the best compression of the 3.
- lzma is somewhere inbetween. Not quite gzip's speed, not quite bzip's compression.

@Enigmapond: compression isn't encryption and 7zip is just lzma.

---

### Post by mazz0 on 2010-01-15
Well, I just did a quick, not very scientific test.

I compressed the files on my desktop (two PNGs, and XCF and a .log (plain text file)) as a .7z, a .tar.bz2, a .tar.gz and a .tar.lzma.

Here are the results:

2,526,990 7z
2,689,980 tar.bz2
3,208,526 tar.gz
2,357,183 tar.lzma

I didn't time them, but gz was easily fastest by a mile, which makes sense since it's the biggest.

7z and tar.lzma worked out smaller than bz2.

Interestingly, tar.lzma worked out smaller than 7z, which I found surprising if 7z uses lzma - I'd've thought if anything it would work out smaller, presumably doing something more optimized for lzma than just tarring.

---

### Post by falconindy on 2010-01-15
> **mazz0 said:**
> Well, I just did a quick, not very scientific test.

I compressed the files on my desktop (two PNGs, and XCF and a .log (plain text file)) as a .7z, a .tar.bz2, a .tar.gz and a .tar.lzma.

Here are the results:

2,526,990 7z
2,689,980 tar.bz2
3,208,526 tar.gz
2,357,183 tar.lzma

I didn't time them, but gz was easily fastest by a mile, which makes sense since it's the biggest.

7z and tar.lzma worked out smaller than bz2.

Interestingly, tar.lzma worked out smaller than 7z, which I found surprising if 7z uses lzma - I'd've thought if anything it would work out smaller, presumably doing something more optimized for lzma than just tarring.
Neat. Some more detail would have been cool (what flags were used, etc), but I'll go dig it up on my own (varying file types and whatnot). 

Not sure why 7z and lzma are coming out different. From 7z's manpage:
```
DESCRIPTION
       7-Zip  is  a file archiver with the highest compression ratio. The program supports 7z (that implements LZMA compression
       algorithm), ZIP, CAB, ARJ, GZIP, BZIP2, TAR, CPIO, RPM and DEB formats. Compression ratio in the new 7z format is 30-50%
       better than ratio in ZIP format.
```
Ironically, the first sentence without qualification is an outright lie, because raw lzma compression won in your simple test. I suppose they're referencing highest average compression ratio...

---

### Post by mazz0 on 2010-01-15
No flags, I just right clicked and chose Compress.  It doesn't give you any options - I was just talking about that in [another thread]("http://ubuntuforums.org/showthread.php?t=1381517") actually.

Maybe the boast on the 7zip man just meant that lzma offers the best compression, and they use lzma.

I think I'll test them again with bigger files, specifically some very large plain text log files from my work's servers (I often need to compress those for emailing).  On that small test I did the lack of compression from bz2 seems a price worth paying for the incredible speed, but that may not be the case with larger files...

---

### Post by falconindy on 2010-01-15
> **mazz0 said:**
> No flags, I just right clicked and chose Compress.  It doesn't give you any options - I was just talking about that in [another thread]("http://ubuntuforums.org/showthread.php?t=1381517") actually.

Maybe the boast on the 7zip man just meant that lzma offers the best compression, and they use lzma.

I think I'll test them again with bigger files, specifically some very large plain text log files from my work's servers (I often need to compress those for emailing).  On that small test I did the lack of compression from bz2 seems a price worth paying for the incredible speed, but that may not be the case with larger files...
Oh. From Gnome.. Bad assumption on my part. I don't use much of a GUI these days.

If all you're interested in is compressing is raw text files, lzma is your answer.

---

### Post by lavinog on 2010-01-15
> **falconindy said:**
> 
Not sure why 7z and lzma are coming out different. From 7z's manpage:


7z has different levels of compression (-mx=# where # can be 1-9)
I think lzma is set to maximum compression by default, while 7z balances compression with speed.
Higher settings require more resources.

tar.lzma is preferred if you wish to keep permissions.  7z drops the permissions.
In some cases rar has better compression, but I don't think it stores permission settings either.

Also different files compress differently.  Some methods would compress one type of file better than others.

---

### Post by mazz0 on 2010-01-15
Well, I've gone off topic here by only compressing text files (it's actually general purpose that I'm more interested in), but check this out:

A bunch of text files totalling 183.7mb.

7z    1m35s 11,533,335
bz2   3m35s 11,214,472
gz    0m30s 16,072,224
lzma 10m45s 9,899,431

Well, 7z gets my vote from that.  What lavinog said certainly makes sense with those results.

---

