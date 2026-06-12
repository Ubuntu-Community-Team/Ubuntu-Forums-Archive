---
title: "tar options"
date: 2010-05-20
forum: General Help
---

### Post by Alex Farber on 2010-05-20
Let's say I execute this command:

tar cfz files.tar.gz file0 folder1/file1 folder2/file2

I get files.tar.gz file with the following structure:

```

folder1
    file1
folder2
    file2
file0

```When I right-click on this file and select "Extract here", it extracts everything to the files directory:

```

files
    folder1
        file1
    folder2
        file2
    file0

```

How can I make this archive by such way, that "Extract here" will not create files directory? Maybe I need to extract this archive from the command line, with some switch preventing files directory creation? This is OK also.

---

