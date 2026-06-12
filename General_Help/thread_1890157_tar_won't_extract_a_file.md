---
title: "tar won't extract a file"
date: 2011-12-02
forum: General Help
---

### Post by Synoc on 2011-12-02
I regularly at the end of my terms in school make a tarball of my term's work and offload it onto my server. as it turns out I need one of those files to help a fellow student who has the class now. I've unzipped it to sp2011.tar and I'm trying to get the file with 
```
 tar -xvf /tmp/sp2011 sqlw2.txt 
``` but it says it can't find the file. what am I doing wrong?

the full path... within the tar is ```
/home/synoc/Documents/College/sp2001/sqlw2.txt
```

any thoughts?

---

### Post by staf0048 on 2011-12-02
Not sure if this will help or not, but are you sure the tar file you got off the server is in /tmp?

---

### Post by Synoc on 2011-12-02
I unzipped it and put it in /tmp

---

### Post by The Cog on 2011-12-03
Just a guess - try the full file path name that you're trying to extract. Since tar normally strips the leading '/', that would be:
```
tar -xvf /tmp/sp2011 home/synoc/Documents/College/sp2001/sqlw2.txt
```

Failing that, use brute force - extract the whole tar into a folder somewhere and then dig out the file you want before deleting the folder again. But it would be more satisfying to get the single file extract working.

---

### Post by Synoc on 2011-12-03
thank you! amazing how easy it is NOT to see one little / and how much a PITA it is.

new question. tar -t /tmp/sp2011 produces a blank line I have to CTRL C out of the --list option does the same. what am I missing? (I should just use the GUI... but you can't learn Linux from a GUI. unless you count web browsing.

---

### Post by The Cog on 2011-12-04
With "tar -t /tmp/sp2011" you didn't give the filename to read, so it's reading from stdin. Try "tar -tf /tmp/sp2011"

---

### Post by Synoc on 2011-12-04
that did the trick. thank you very much.

---

