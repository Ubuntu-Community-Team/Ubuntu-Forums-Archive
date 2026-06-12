---
title: "mount an archive"
date: 2009-06-30
forum: General Help
---

### Post by bwitherell on 2009-06-30
Hello, does anyone know of a way can mount a zip or tar archive?

Any help would be appreciated. Thank you.

---

### Post by colau on 2009-06-30
> **bwitherell said:**
> Hello, does anyone know of a way can mount a zip or tar archive?

Any help would be appreciated. Thank you.
For zip files
```

unzip filename

```
For .tar.gz files
```

tar vzxf filename.tar.gz

```

---

### Post by bwitherell on 2009-06-30
> **colau said:**
> For zip files
```

unzip filename

```
For .tar.gz files
```

tar vzxf filename.tar.gz

```

Thank you for the reply. I do not wish to extract the archive. I would like to mount it. The reason being is that extracting the entire archive takes too long.

The archive is a gziped ntfsclone disk image. what I need to do is mount the archive so I can then use mount -o loop to mount the disk image that is inside that archive.

Thanks for the help

---

### Post by jerome1232 on 2009-06-30
I'm like 98.9% positive you can't mount the image until you extract it out of the archive, especially since it's compressed.

---

### Post by Vrekk on 2009-06-30
I've always right clicked on the archive and opened it with Archive Mounter,  Works great for me

---

### Post by bwitherell on 2009-06-30
> **jerome1232 said:**
> I'm like 98.9% positive you can't mount the image until you extract it out of the archive, especially since it's compressed.

You are probably right when it comes to zip archives but there is a program called archivemount that is supposed to be able to mount tar archives. I am in the process of trying this program out. I'll post my results.

I'm hoping there is something out there that can mount gzip archives too.

---

### Post by bwitherell on 2009-06-30
> **bwitherell said:**
> You are probably right when it comes to zip archives but there is a program called archivemount that is supposed to be able to mount tar archives. I am in the process of trying this program out. I'll post my results.

I'm hoping there is something out there that can mount gzip archives too.

Yea, archivemount does not work very well for what I need. There must be a way.

---

### Post by decoherence on 2009-06-30
[fuse-zip]("http://code.google.com/p/fuse-zip/")

doesn't look like it's in the repositories...

---

### Post by bwitherell on 2009-06-30
> **decoherence said:**
> [fuse-zip]("http://code.google.com/p/fuse-zip/")

doesn't look like it's in the repositories...

any idea on how to use it once i install it? thanks.

---

### Post by decoherence on 2009-06-30
> **bwitherell said:**
> any idea on how to use it once i install it? thanks.

You got it installed already? That was quick...

man fuse-zip says the syntax is

fuse-zip *path-to-zipfile* *mountpoint*

for instance,

```
$ mkdir test-mount-point
$ fuse-zip Desktop/20041020-310_novell-macosx-10.3.zip test-mount-point/
```

works fine for me!

---

