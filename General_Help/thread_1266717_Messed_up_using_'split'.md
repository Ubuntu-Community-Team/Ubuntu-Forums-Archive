---
title: "Messed up using 'split'"
date: 2009-09-14
forum: General Help
---

### Post by Globox on 2009-09-14
Ok so I'm transferring a bunch of large .avi files to an external USB drive on my Ubuntu server machine. Some of the files are quite large and after splitting one of them into 4096m chunks I went to the next file and entered the split command, except this time I forgot to add the 'm' after the number of bytes.

So what happened is it made a ton of little pieces of the file and eventually spat this error at me:
```
split: Output file suffixes exhausted
```
Now there a ton of little pieces and I don't know how to rejoin them (I was going to transfer all of these files onto a Windows machine and use the built-in tool to join split files).

How do I rejoin the files on Linux so I can split them into larger chunks before finally joining them in Windows?

---

### Post by unutbu on 2009-09-14
split creates files named xaa ... xzz before it stops with the error
```

split: Output file suffixes exhausted
```

It does not delete the original file.
However, if you deleted the original file, then the pieces xaa ... xzz may not be enough to reconstruct the original file, since split had to stop prematurely.

There are 676 files from xaa ... xzz. If each file is 4096 bytes, then to concatenation of all 676 files would only amount to about 2 MB. 

Therefore, I don't think trying to reconstruct the original using xaa ... xzz is going to work. I hope you have the original or a backup ...

---

### Post by Globox on 2009-09-14
Oh, yeah I have the original file... I thought that it split the source file into the small pieces. Cool, thanks.

I guess I have to delete all the little pieces then and just redo it.

For future reference, though, how do you rejoin split files in Ubuntu?

Thanks a ton.

---

### Post by DaithiF on 2009-09-15
you can use the cat command to reassemble split files.
```
cat xaa xab xac >> newfile

```
or
```
cat xa* >> newfile
```
where xa* means all files beginning with xa

---

