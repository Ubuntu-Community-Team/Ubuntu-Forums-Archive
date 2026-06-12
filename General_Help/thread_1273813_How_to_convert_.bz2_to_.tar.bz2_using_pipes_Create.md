---
title: "How to convert .bz2 to .tar.bz2 using pipes? Create tar from standard input"
date: 2009-09-23
forum: General Help
---

### Post by Endolith on 2009-09-23
How do I convert a .bz2 archive of a single file into a .tar.bz2 archive?  I can't decompress the entire thing and then recompress it, since the compression ratio is huge.  I've tried every combination of "tar" "bunzip2" "|" ">" and "-" that I can think of, and it won't work.

Also, how do I determine the uncompressed size of a .bz2 file?

[related]("http://www.terrencemiao.com/Webmail/msg00557.html")

[tar manual]("http://www.gnu.org/software/tar/manual/tar.html") only describes how to read a compressed file from standard input and decompress it to a real file.

---

### Post by bogdan.veringioiu on 2009-09-24
Hi.
Indeed, tar will not read from a pipe, while trying to create an archive (-c).

This means that the following line will NOT work:
bunzip2 -c archive.bz2 | tar -cf - | bzip2 > archive.tar.bz2
I think this was what you wanted, but...:(
Bogdan

---

### Post by Endolith on 2009-09-24
Pretty much, though tar will create a .tar.bz2 with the -j option, which simplifies it.

The manual says "Starting with version 1.11.5, GNU tar uses standard input and standard output as the default device", but I don't quite understand.

[http://www.gnu.org/software/tar/manual/tar.html#SEC146](http://www.gnu.org/software/tar/manual/tar.html#SEC146)

---

### Post by Lars Noodén on 2009-09-24
I've tried a few permutations of bzip and tar as well.  

It looks like tar doesn't like to take a single file as data and you might be looking at a feature request for tar.  

The compression that tar does comes *after* making a tar file.  
tar has its own format so you may have to spend the time and uncompress the file and then recompress it.

---

### Post by Endolith on 2009-09-24
> **Lars Noodén said:**
> I've tried a few permutations of bzip and tar as well.  

It looks like tar doesn't like to take a single file as data and you might be looking at a feature request for tar.  

You can tar a single file.  I definitely did that last night, though I don't remember which command does it.

> The compression that tar does comes *after* making a tar file.  
tar has its own format so you may have to spend the time and uncompress the file and then recompress it.Right.  Tar doesn't do any compression at all, it's just a wrapper for (usually multiple) files and their metadata, which is why it wasn't used in this case, since the contents are a single file.

It's not a matter of time; it's a matter of space.  The compressed size is a few GB, but the uncompressed size is >100 GB, which I don't have space for.  

Since bzip acts on blocks, it should be possible to uncompress a block, pipe it to tar, pipe it to bzip, write to disk, read the next block, etc.  If tar doesn't support compressing from standard input, maybe it can be tricked into it by using a named pipe or something?

---

### Post by Lars Noodén on 2009-09-24
> **Endolith said:**
> You can tar a single file.  I definitely did that last night, though I don't remember which command does it.

Right.  Tar doesn't do any compression at all, it's just a wrapper for (usually multiple) files and their metadata, which is why it wasn't used in this case, since the contents are a single file.

It's not a matter of time; it's a matter of space.  The compressed size is a few GB, but the uncompressed size is >100 GB, which I don't have space for.  

Since bzip acts on blocks, it should be possible to uncompress a block, pipe it to tar, pipe it to bzip, write to disk, read the next block, etc.  If tar doesn't support compressing from standard input, maybe it can be tricked into it by using a named pipe or something?


Yes you can tar a single file, but as everyone here notices not as a pipe.  

Named pipes where one of the things I tried in many permutations.  No dice.  There are other times, though, that named pipes can be useful.

---

### Post by Endolith on 2009-09-24
Is there a way to print the uncompressed size?

---

