---
title: "Selecting which files to extract from archive"
date: 2011-06-07
forum: General Help
---

### Post by jaiagreen on 2011-06-07
I need to extract some files from a number of large, compressed archives (.tgz). Just decompressing all the files would be easy but would result in huge disk space usage. Is there a way to tell gzip (or another utility) to only extract those files inside each .tgz file that have names starting with "a"?

---

### Post by Morderwurst on 2011-06-07
[http://www.gnu.org/software/tar/manual/tar.html#SEC26](http://www.gnu.org/software/tar/manual/tar.html#SEC26)

[LEFT][U][B]
[SIZE=3]tl;dr version[/SIZE][/B][/U]
[/LEFT]
 
List files in collection.tar:

```
tar --list --file=collection.tar

```

extract specific file "example.txt" from collection.tar:

```

tar --extract --file=collection.tar example.txt
```

extract all files beginning with the letter "a" from collection.tar:

```

tar -x -f collection.tar --wildcards --no-anchored 'a*'
```

---

### Post by sisco311 on 2011-06-07
```

cd /path/to/dir
for file in *.tgz
do
  tar xfvz "$file" --wildcards --no-anchored 'a*'
done
```

Where,
[list]
[*]x: instructs tar to extract files.
[*]f: specifies filename / tarball name.
[*]v: Verbose (show progress while extracting files).
[*]z: filter archive through gzip, use to decompress .gz files.
[*]--wildcards: instructs tar to treat command line arguments as globbing patterns.
[*]--no-anchored: informs it that the patterns apply to member names after any / delimiter.
[/list]

See:
[http://www.cyberciti.biz/faq/linux-unix-extracting-specific-files/](http://www.cyberciti.biz/faq/linux-unix-extracting-specific-files/)

---

### Post by jaiagreen on 2011-06-07
Thanks, sisco. That looks like it should work.

---

