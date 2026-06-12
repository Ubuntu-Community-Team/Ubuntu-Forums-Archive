---
title: "Creating directory inside tar file"
date: 2009-11-02
forum: General Help
---

### Post by geo909 on 2009-11-02
Hello all,

I have a question, any help would be much appreciated.

Say I have a bunch of files
```
file1 file2 file3
``` 
among many others in the same folder, and I want to make a tar.gz file of these files. If I remember correctly, I could do something like
```
tar -czf my_compressed_file.tar.gz file1 file2 file3 
```
 but I would rather put everything in a folder *inside* the compressed file. In other words the contents of the compressed file should be
```

my_directory
my_directory/file1
my_directory/file2
my_directory/file3

```

Is there a way to do that with one command and without creating temporary folders and stuff?

Finally, say I have my compressed file as I want, and then I decide that I want to put *file4* inside the already created folder *my_directory* of the compressed file. Can I do that without using many commands again?

Many thanks in advance

---

### Post by falconindy on 2009-11-02
You can either make an exclusion list (which accepts wildcards), or if you're going to do this often, make a phony directory with symlinks and use the -h flag to dereference them.

'man tar' has everything you need to know.

---

