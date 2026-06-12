---
title: "sed wildcard syntax?"
date: 2009-08-28
forum: General Help
---

### Post by DejitaruJin on 2009-08-28
Okay, I have a list of all the files located in a tar file - and it's over 6MB in size. But I don't need to worry about all the individual files, just the much smaller number of main subdirectories.

Now, the command...
```
sed '/\/mnt\/250GB\/LinuxDocs\// d'
```... will delete everything that involves /mnt/250GB/LinuxDocs/ . That much I have working. But it's far too much hassle to check the text file I have it routed to, write down the lone subdirectory listed before all its contents, and then run sed again to delete the directory (and its contents), then check the new top-listed directory. I would much rather just wipe all the contents.

The problem is, I can't figure out how. I know it needs to start with '/\/mnt\/250GB\/ , but from there I can't for the life of me figure out how to get wildcards working. I thought that...
```
'/\/mnt\/250GB\/[A-Z]+\/[A-Z]+/ d'
```... would at least do something - with the intended effect of deleting everything that goes beyond one directory with any name - but it doesn't even change the file at all, nor does it give an error.

What the heck is the syntax for this?

---

### Post by DaithiF on 2009-08-28
you need to escape '+' in 
```
[A-Z]+

```
'+' will match a literal '+' character
'\+' will match '1 or more of the preceding expression', which is what you want.

cheers
d

---

### Post by DejitaruJin on 2009-08-29
Interesting, I'm surprised that wasn't mentioned in any of the pages I saw. But, it works, and now all my data is exactly where it should be. I hope.

---

