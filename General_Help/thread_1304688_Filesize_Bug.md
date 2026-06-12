---
title: "Filesize Bug?"
date: 2009-10-29
forum: General Help
---

### Post by Psycho.mario on 2009-10-29
I have just been playing around with mksquashfs. I created a file using:
```
dd if=/dev/zero of=file bs=1024M count=1
```
This created a 1Gb file. I then moved it into a folder on it's own. However, when i ran ls -lh on the directory above the folder, it only showed the folder as 4.0K. Also, when i ran mksquashfs on the folder and created a file with that, that file was only 4.0K. Is this a bug? Or is there something i am missing. Thanks

---

### Post by albandy on 2009-10-29
it's a file full of 0s, so it's an empty file with a logical size of 1GB

---

### Post by Psycho.mario on 2009-10-29
Oooh, So how can i create a real file that is 1GB?

---

### Post by albandy on 2009-10-29
you defined a block size of 1024M, but usually a disk block size is 4096
for example, this will create a file with a block size of 1024 bytes and 1024000 block
dd if=/dev/zero of=file bs=1024 count=1024000

---

### Post by alphaniner on 2009-10-29
Directories will always show up as 4.0k.  I'm not familiar with squashfs so I don't know about the file.

If you want to make a file with actual data, you can use

```
dd if=/dev/urandom of=file bs=1024M count=1
```

but it probably will be slower than using /dev/zero.

You could also try 

```
dd if=/dev/urandom of=file bs=1M count=1024
```

you will probably see a difference in speed (for better or worse)

Also, if you want to see the progress of a dd command, do the following

```
$ dd if=/dev/zero of=file bs=1M count=1024 &
[1] **9141**
$ kill -s USR1 **9141**;echo
$ 399+0 records in
399+0 records out
418381824 bytes (418 MB) copied, 8.02935 s, 52.1 MB/s
$

```
Repeat the **kill** command to get further 'progress reports'

---

### Post by Psycho.mario on 2009-10-29
Thanks, thats very useful

---

