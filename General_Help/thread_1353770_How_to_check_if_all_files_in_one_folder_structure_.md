---
title: "How to check if all files in one folder structure exists in another folder structure"
date: 2009-12-13
forum: General Help
---

### Post by Krislarsen on 2009-12-13
Hello!

I am looking for the easiest way to do check if all files in a folder structure exists in another folder structure, and list the files and folders that don't.

I have about 20.000 files in each library. One of the folder structures is cleaned up manually (lots of work..), but a few files was deleted accidently.

A script using md5sum might be a solution. Any better ideas?

---

### Post by lawenlerk on 2009-12-13
> **Krislarsen said:**
> Hello!

I am looking for the easiest way to do check if all files in a folder structure exists in another folder structure, and list the files and folders that don't.

I have about 20.000 files in each library. One of the folder structures is cleaned up manually (lots of work..), but a few files was deleted accidently.

A script using md5sum might be a solution. Any better ideas?
I think there are linux commands that can do so but python ought to do the job too.

If you know python, then just a "filename checking" script will do.

I'd be happy to help. I remember writing such a script b4.

Tho i wont be free until a while.

---

### Post by john newbuntu on 2009-12-13
I miss dircmp in linux that we used to have in Unix.  Anyway, see if "diff -r dir1 dir2" makes any sense to you.

---

### Post by geirha on 2009-12-13
You could use rsync in dry-run mode (-n). It will output which files that differ or does not exist on the destination. And of course, just remove the -n to have those files copied :)
```
( cd /path/to/dir1 && rsync -avn . /path/to/dir2 )
```


A simple sh for-loop could also do the trick, though this doesn't check if the files are identical, only if there exists a file by the same name
```
cd /path/to/dir1 &&
for f in *; do
    [ -e "/path/to/dir2/$f" ] || echo "Missing: $f"
done

```

---

### Post by Krislarsen on 2009-12-13
The question was maybe a little bit unclear. I have two different folder structures with the same files. More specific: the folder names are completely different (because of re-organization).

md5deep from the repository (apt-get..) might be what I'm looking for.. Any experience with this program?

---

### Post by Krislarsen on 2009-12-13
I think md5deep can work, if used like this:


[LIST=1]
[*]Run the following command in the master directory (where all our files shall be):
```
md5deep -r -l * > md5sums-master.md5
```

[*]Run the following command in the folder to be deduplicated. All files that DO EXIST in the master-directory will be listed, they can safely be deleted (and will be if running the xargs rm-line...)
```
md5deep -r -m ../../master-folder/md5sums-master.md5 * > duplicates.list
xargs rm < duplicates.list
```
[/LIST]

This would probably be better as a script with two input folders..

Anyway; does it look like a safe way to perform file-deduplication?

---

### Post by Bonster on 2009-12-14
You can use meld, it has file and folder options

> sudo apt-get install meld

or for KDE i think is called

> sudo apt-get install kompare

---

### Post by Krislarsen on 2009-12-14
> **Bonster said:**
> You can use meld, it has file and folder options

or for KDE i think is called
Looks nice, but as far as I can see, it doesn't find duplicates when they are placed in folders with different names..

---

