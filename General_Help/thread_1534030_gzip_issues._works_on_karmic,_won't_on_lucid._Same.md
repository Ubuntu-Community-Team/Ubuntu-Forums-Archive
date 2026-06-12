---
title: "gzip issues. works on karmic, won't on lucid. Same files MD5 checked."
date: 2010-07-18
forum: General Help
---

### Post by schmick on 2010-07-18
Hi!
I was about to install a program that requiered zlib to compile.
Easy. Went to zlib.net, copied the url, wget the tar.gz.
All normal, but it wouln't tar xvzf.
```

tar xvzf zlib-1.2.5.tar.gz
<long list omitted>
gzip: stdin: invalid compressed data--crc error

```
hmmmm. gunzip it first?
```

gunzip zlib-1.2.5.tar.gz
gzip: zlib-1.2.5.tar.gz: invalid compressed data--crc error

```

My assumption.. bad file.
let's check MD5
```
md5sum zlib-1.2.5.tar.gz 
c735eab2d659a96e5a594c9e8541ad63  zlib-1.2.5.tar.gz

```
File is ok... 
I ssh into other server.
got the SAME file (md5 checked) through wget, and no crc error.

gzip version?
nope.. same version.
corrupt gzip?
```

md5sum `which gunzip`
c8c75748b1d02c5f79848f7fba3dfe0c  /bin/gunzip

```
nope.. same files.

Next I though FileSystem!
plugged in a pendrive and wget and tried to gunzip on it.
Didn't work either.. same crc.

Memory?
Ran the memtest for 3 passes... no errors.
The only thing different is that it fails on Lucid but works on Karmic.

I'm puzzled.

---

