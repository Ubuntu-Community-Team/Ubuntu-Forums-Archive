---
title: "upacking a big compressed file on a small disk"
date: 2009-09-02
forum: General Help
---

### Post by morganpatrick on 2009-09-02
Hi,

I had a freakout yesterday when I accidentally deleted some really important information on my laptop, which is an ext3 file system. I made a [thread]("http://ubuntuforums.org/showthread.php?t=1255031") about it but I don't want to bump it again and this is a separate issue.

I used dd to copy an image of my laptop's hard drive onto an old drive I put in my dekstop. I transferred it as a gzip archive. The desktop drive holds about 180 gigabytes. The gz archive is broken into 638 megabyte chunks, 129 separate files, 80 gigabytes in all. Uncompressed, the image is 105 gigabytes.

So if I unpack it, 105gb + 80gb > 180gb.

Here's my question: how do I inflate this without running out of space? Since it's in chunks (backup.img.gz.aa through backup.img.gz.ey) I could move some of the chunks to a different drive. Can I reconsolidate a fragmented gzip drawing from more than one location? Can I get a gzip to unpack and delete itself as it goes along? 

Thank you.

---

### Post by niteshifter on 2009-09-02
Hi,

> Can I reconsolidate a fragmented gzip drawing from more than one location?

Yes:
```
**cat** /path/to/chunk.1 /some/other/path/to/chunk.2 /yet/another/path/to/chunk.3 > chunks123
```

---

