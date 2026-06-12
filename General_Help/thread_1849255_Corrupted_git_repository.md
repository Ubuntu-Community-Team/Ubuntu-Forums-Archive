---
title: "Corrupted git repository"
date: 2011-09-24
forum: General Help
---

### Post by mfans on 2011-09-24
For some reason my git repository was corrupted (probably some irresponsible "rm -f" by me). All I am left now is a .git directory containing only an objects directory.

I've followed these steps:

* Created a new directory and ran git init
* Copied the objects directory I had to the new .git/objects directory
* Ran git fsck command.

The output of the above steps produced the following msg:

notice: HEAD points to an unborn branch (master)
notice: No default references
dangling commit 0b2c7d52b6a7e6d4e2858e9ebf207c315407c87c
dangling commit 8dceafea1634c923069f6d4b925839c28d92c4e5
dangling commit dd7bdd04c557a018c15fd0948075121f181decd1
When I try to run git log at this stage I get fatal: bad default revision 'HEAD'.

So I then added a file under /refs/heads called master containing one of the dangling commits HASH.

The msg I got in return was fatal: 
"unable to read tree 3c864da48b16ad0dc5f8ae585380270a708a1e56"

Any ideas if I can still recover from this situation?

------
UPDATE:

If I run 
"git cat-file -p 0b2c7d52b6a7e6d4e2858e9ebf207c315407c87c"
 then I see the commit message, then I can go to the tree hash, use "cat-file -p" again and eventually I can see all my files... The only question is how the hell I can restore the files as a git repository? :)

---

### Post by dino99 on 2011-09-24
seems it still try to read the old .git: remove it.

---

### Post by mfans on 2011-09-24
I deleted the old repository but it still doesn't work

---

