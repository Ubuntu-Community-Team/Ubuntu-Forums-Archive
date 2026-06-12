---
title: "7zipfs?"
date: 2009-12-08
forum: General Help
---

### Post by undecim on 2009-12-08
is it possible to mount a 7zip archive as a filesystem? (i.e. so that I could just point any program to ~/archive/file so that it would be accessing "file" from ~/archive.7zip)

Some filesystems like reiserfs support gz or bz2 compression on the fly, but this isn't what I'm looking for. I need the archive and my home folder to share the same partition, so that when I move a file from ~/ to ~/archive, the the difference between the compressed and uncompressed file is freed from my home partition. If I have to set aside space for it, it kind of defeats the purpose.

I would also like to use 7zip, because it has the best compression ratio of any compression algorithm I have found. It involves a lot of overhead, but I won't be accessing this folder much, so that isn't a problem.

Anyone have any ideas?

---

