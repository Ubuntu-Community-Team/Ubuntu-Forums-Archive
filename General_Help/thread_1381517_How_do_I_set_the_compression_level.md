---
title: "How do I set the compression level?"
date: 2010-01-14
forum: General Help
---

### Post by mazz0 on 2010-01-14
You right click on a file and choose Compress.  How do you select the compression level for algorithms that support different levels?  If you can't, what compression level does it use?

---

### Post by ankspo71 on 2010-01-15
Hi,
I don't think I can give you the answer you are looking for, but I do know that.....

compress into *.tar  = no compression at all
compress into *.tar.gz = equivalent of standard compression 
compress into *.tar.bz2 = equivalent of maximum compression

You can also install p7zip-full to give you a few more archives to select from. Unfortunately, I don't see a way to choose a  compression level with those either. :(

Hope this helps.

---

### Post by Puzzled Guy on 2010-01-15
The default compression level should probably be normal compression.

---

### Post by mazz0 on 2010-01-15
Thanks guys.

I assume they decided not to offer compression levels in the default compression tool to keep it simpler for new users.

Wow, just did a quick test - bz2 is a LOT faster than gz or lzma isn't it?

---

### Post by mister_playboy on 2010-01-15
> **mazz0 said:**
> Thanks guys.

I assume they decided not to offer compression levels in the default compression tool to keep it simpler for new users.

Wow, just did a quick test - bz2 is a LOT faster than gz or lzma isn't it?

Bzip2 should be slower than gzip since it compresses more effectively.  There is no free lunch with compression.

[http://en.wikipedia.org/wiki/Bzip2](http://en.wikipedia.org/wiki/Bzip2)

---

### Post by oldmankit on 2011-01-18
I actually do want to select compression level!

I'm using ```
tar -cvjf file.7z directory_to_recurse
```I am doing long-term backups and want to select the maximum level of compression (slowest). (I would also like to test a few different levels to compare.)

This is easily selectable if I use the command 'bzip2' by using the option -9.  However, I can't see how to recurse a whole set of directories using 'bzip2' as a command.  I want all directories preserved in the archive, so I can't just use 'find' and pass the output of that to bzip2.  This is why I reverted to using 'tar', as recursion is automatic.

This should be easy...

---

### Post by stinkeye on 2011-01-19
You can set the compression level for file-roller in gconf-editor
/apps/file-roller/general/compression_level

---

### Post by oldmankit on 2011-01-19
> **stinkeye said:**
> You can set the compression level for file-roller in gconf-editor
/apps/file-roller/general/compression_level

Thanks for that.   I'm really looking for a command-line based solution, if there is one...

---

### Post by pqwoerituytrueiwoq on 2011-01-19
> **oldmankit said:**
> Thanks for that.   I'm really looking for a command-line based solution, if there is one...

if you are making a script this will be helpful
```
gconftool --type String --set /apps/file-roller/general/compression_level maximum
```
very_fast, fast, normal, or maximum

---

### Post by oldmankit on 2011-01-26
> **pqwoerituytrueiwoq said:**
> if you are making a script this will be helpful
```
gconftool --type String --set /apps/file-roller/general/compression_level maximum
```very_fast, fast, normal, or maximum

Thank you again.

I was keen to use use tar or bzip2 straight from the terminal, without calling any other programs, since there should be a simple solution.  I have found a way to do this.

First I create the tar file, uncompressed, using 
```
tar cvf archive.tar [directory to be tarred]
```Then I used the bzip2 command directly on the tarball:
```
bzip2 -kv9 archive.tar
```This set the highest level of compression.  Remove -k to delete the old (uncompressed) tarball.

On a tar file sized 438M, it reduced it to 432M!  Not particularly impressive!  The file only contained jpegs, which I suppose are already compressed.

---

### Post by genegold2 on 2011-01-27
try this one to tar and bz2 with one-line:

 tar -jcvf archive_name.tar.bz2 directory_to_compress

---

### Post by oldmankit on 2011-01-28
> **genegold2 said:**
> try this one to tar and bz2 with one-line:

 tar -jcvf archive_name.tar.bz2 directory_to_compress
Which will use which compression level?

---

### Post by psusi on 2011-01-28
> **oldmankit said:**
> 
I'm using ```
tar -cvjf file.7z directory_to_recurse
```

Wrong extension.  That should be .tar.bz2.  The -j means bzip2.  A 7-zip archive is something else entirely.

If you want to specify the level then you need to invoke bzip2 directly.  This means you either run it on the .tar file once tar is done building it with no compression, or you have tar pipe it to an instance of bzip2.

---

### Post by oldmankit on 2011-01-30
> 
If you want to specify the level then you need to invoke bzip2 directly.   This means you either run it on the .tar file once tar is done  building it with no compression, or you have tar pipe it to an instance  of bzip2.

That's what I'd concluded.  I thought it was a bit funny that there was no option to do it with tar, but nevermind!

---

### Post by swilwerth on 2011-02-16
Did you try something like?:

```

tar cvf - <dir or file> | gzip -1 - > file.tar.gz
```

Or if you want to split the output in multiple files of 2048M you can do:

```

tar cvf - <dir or file> | gzip -1 - | split -d -b 2048M - file.tar.gz.
```

Then, te output will be: 
file.tar.gz.00 
file.tar.gz.01 .. file.tar.gz.NN

To join it again simply use cat.

```

for i in *.tar.gz.*
do
   cat $i >> file.tar.gz
done
```

Also, you can change gzip to bzip2 or p7zip.
See the man pages of these for setting the compression level.

---

### Post by oldmankit on 2011-02-16
> **swilwerth said:**
> Did you try something like?:

```

tar cvf - <dir or file> | gzip -1 - > file.tar.gz
```Or if you want to split the output in multiple files of 2048M you can do:

```

tar cvf - <dir or file> | gzip -1 - | split -d -b 2048M - file.tar.gz.
```Then, te output will be: 
file.tar.gz.00 
file.tar.gz.01 .. file.tar.gz.NN

To join it again simply use cat.

```

for i in *.tar.gz.*
do
   cat $i >> file.tar.gz
done
```Also, you can change gzip to bzip2 or p7zip.
See the man pages of these for setting the compression level.

That's a very comprehensive system; thanks for posting it.

I am doing a backup of all my photos to DVDs.  I tried using bzip but the compression was almost negligible.  I expect this is because they are mainly jpegs.  Now that I shoot in RAW, maybe it will be of more benefit.

---

