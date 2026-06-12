---
title: "Bulk renaming"
date: 2011-12-11
forum: General Help
---

### Post by ledererster on 2011-12-11
I'm trying to rename all the files in a directory with the name command.

```


~/qBT_dir/Community$ ls
Community.S01E01.Pilot.HDTV.XviD-FQM.avi
Community.S01E02.Spanish.101.HDTV.XviD-FQM.avi
Community.S02E09.HDTV.XviD-LOL.avi
Community.S02E10.HDTV.XviD-LOL.avi
Community.S03E01.HDTV.XviD-LOL.avi
Community.S03E02.HDTV.XviD-LOL.avi
Community.S03E03.HDTV.XviD-LOL.avi
Community.S03E04.HDTV.XviD-LOL.avi
Community.S03E05.HDTV.XviD-LOL.avi
Community.S03E06.HDTV.XviD-LOL.[VTV].avi
Community.S03E07.HDTV.XviD-LOL.avi
Community.S03E08.HDTV.XviD-LOL.avi
Community.S03E09.HDTV.XviD-LOL.avi
Community.S03E10.HDTV.XviD-LOL.avi

```

i'm trying to get rid of all the extra crap. I just want
Community_S##E##.avi

here's what I have. I am terrible with regex by the way.

```


rename -n 's/\S{11}(\d{2})\S{1](\d{2})\.avi$/Community_S$1E$2\.avi/' *.avi

```

no matter what I tweak I can't get any files to list.

---

### Post by spiky001 on 2011-12-11
I found this [http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal](http://tips.webdesign10.com/how-to-bulk-rename-files-in-linux-in-the-terminal)

---

### Post by ledererster on 2011-12-11
Thanks. But I have already read through this site. The rename command isn't the issue. It's my ignorance with regex. With the help of several online tutorials I have constructed the command above, but I have no idea why it's not working.

---

### Post by Lars Noodén on 2011-12-11
Can you test your regex first with [egrep](http://manpages.ubuntu.com/manpages/oneiric/en/man1/egrep.1.html) or [sed](http://manpages.ubuntu.com/manpages/oneiric/en/man1/sed.1posix.html)?  Then once it's working try transferring it to [rename](http://linux.die.net/man/1/rename)

Edit: Can you show an example of what you want the renamed file name to look like?

---

### Post by ledererster on 2011-12-11
I want the file to be Community_S##E##.avi 

so for example, Community_S01E02.avi

---

### Post by sisco311 on 2011-12-11
This seems to work:
```
prename -n 's/.*(S[0-9]{2}E[0-9]{2}).*/Community_$1.avi/' Comm*

```

---

### Post by ledererster on 2011-12-11
works perfectly!! Thanks alot!

---

### Post by lechien73 on 2011-12-11
Modifying your original example, you could also do:


```
rename -n 's/\S{11}(\d{2})\S{1}(\d{2}).*/Community_S$1E$2\.avi/' *.avi

```

For future regular expressions you could run them through the regular expression tester here: [http://www.regular-expressions.info/javascriptexample.html](http://www.regular-expressions.info/javascriptexample.html)

Running your original example through, it was starting to evaluate the expression from the right hand side of the filename, because of the presence of \.avi$

---

