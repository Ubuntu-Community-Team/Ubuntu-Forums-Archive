---
title: "Copy Only Certain Files?"
date: 2011-02-14
forum: General Help
---

### Post by scottmac112 on 2011-02-14
Hi all!

I mirrored a web site with HTTrack to save all of its images. However, all of the web site is mirrored, not just the pictures. I would like to copy just the *.jpg files into a different directory. However, when I run the command that makes the most sense to me:

scott@ubuntu-one:~/websites/<website>$ cp -rf *.jpg ~/Pictures

It just spits out:

cp: cannot stat `*.jpg': No such file or directory

It seems as though it's not looking recursively, as it should. I really don't want to do this folder by folder! There has to be a better way. Thanks!

---

### Post by Habeouscorpus on 2011-02-14
From the manual: 

>  By default, `cp' does not copy directories.  However, the `-R',
`-a', and `-r' options cause `cp' to copy recursively by descending
into source directories and copying files to corresponding destination
directories.


Maybe you need to use an -a?

---

### Post by WorMzy on 2011-02-14
Try this:

```
find . -regex '.*\.jpg$' -exec cp --parents '{}' ~/Pictures \;
```

(cd to ~/websites/<website> before running)

---

### Post by asmoore82 on 2011-02-14
That should work, Or:
```
find *websites/directory* -iname "*.jpg" -print0 | xargs -0 cp -t ~/Pictures/
```

---

