---
title: "Using cat recursively"
date: 2011-12-16
forum: General Help
---

### Post by leemid on 2011-12-16
Hi,

Following a really nasty experience with a Deja-Dup backup, I've used the [manual restore procedure]("http://live.gnome.org/DejaDup/Help/Restore/WorstCase") to get what appears to be all of my files back. However, I now have literally thousands of folders containing parts of files which need to be stitched together. The article suggests looking up the manual page for rdiff to do this... but this doesn't really seem to give me any clues as to how to use the command in this situation.

I have used cat successfully, and think this might be easier. However, I need to find a way to use cat recursively, for example to combine files in ~/restore/foo1.txt/ as well as ~/restore/photos/2011/01/01/foo.jpg/

I've had a look on various websites but most guides seem to concatenate everything into one file, whereas I want to end up with hundreds of files of different types. Can anyone help me on this, please?

---

### Post by leemid on 2011-12-20
Sorry to bump, but I was planning on fixing this over Christmas... does anyone have any ideas or am I doomed to type one command 1000 times? :)

---

### Post by SlugSlug on 2011-12-20
> **leemid said:**
> Sorry to bump, but I was planning on fixing this over Christmas... does anyone have any ideas or am I doomed to type one command 1000 times? :)


what is the one command your typing?

---

### Post by leemid on 2011-12-20
How silly of me not to include that! So the contents of one particular file is stored in a folder with a name like ~/restore/foo.txt/ and that contains file fragments named 0, 1, 2 and so on.

To combine I've been using ```
cd ~/restore/foo.txt/ 
cat * > ~/output/output.ext
```

 This seems to work almost all the time - but it was a dodgy backup, so I'm not expecting every file to be perfect. Something really helpful would be the ability to make output.ext the name of the containing folder (because that's what the original filename was). That might make sorting everything a little easier later on. I don't know if that's possible, though...

---

