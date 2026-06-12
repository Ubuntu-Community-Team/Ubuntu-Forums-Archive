---
title: "Copy files"
date: 2010-12-09
forum: General Help
---

### Post by MartijnBangor on 2010-12-09
Hi,

I'm struggling with terminal (sorry I'm a beginner). I want to copy files of a specific type (for example *.txt) from one directory to another while leaving the sub-dir structure intact.

Example

/months/jan/test.txt
/months/feb/test2.txt
/months/feb/test2.mov
/months/feb/test4.mov

--> How can I only copy the *.txt files inside the correct subdir?

For example copy to temp:
/temp/months/jan/test.txt
/temp/months/feb/test2.txt


Many thanks,

Martijn

---

### Post by gmargo on 2010-12-09
The trick is to copy through an archive format that will create the destination directories as needed, so use either **tar** or **cpio**.  Here is an example using tar to copy from /months/... to /temp/...:

```

cd /
find ./months -type f -iname '*.txt' -print | tar -T - -cf - | tar -C /temp -xf -

```

---

