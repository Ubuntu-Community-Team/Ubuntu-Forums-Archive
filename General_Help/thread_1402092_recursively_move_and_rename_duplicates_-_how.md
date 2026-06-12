---
title: "recursively move and rename duplicates - how?"
date: 2010-02-08
forum: General Help
---

### Post by TurboRush on 2010-02-08
Hello,

I am hoping someone already has a script or knows of an app that will let me do this fairly easily - I have a fairly large folder structure that goes several levels deep, etc. In many cases there are duplicate file names that are not really different, eg.
/home/chris/folder/folder1/doc1.doc
/home/chris/folder/folder2/folder3/doc1.doc

I want to recursively go through /home/chris/folder and move EVERYTHING to /home/chris/another_location/ without subfolders and renaming duplicates as appropriate, e.g.,
/home/chris/another_location/doc1.doc
/home/chris/another_location/doc1_1.doc

Anybody have everything pre-existing I can use or know of an application out there?

Thanks,

Chris

---

### Post by darolu on 2010-02-08
You should be able to do it with "mmv", install it with:
```
sudo apt-get install mmv
```

This links should help you to do what you need:
[http://linux.dsplabs.com.au/mmv-copy-append-link-move-multiple-files-under-linux-shell-bash-by-wildcard-patterns-p5/](http://linux.dsplabs.com.au/mmv-copy-append-link-move-multiple-files-under-linux-shell-bash-by-wildcard-patterns-p5/)
[http://linux.die.net/man/1/mmv](http://linux.die.net/man/1/mmv)

---

