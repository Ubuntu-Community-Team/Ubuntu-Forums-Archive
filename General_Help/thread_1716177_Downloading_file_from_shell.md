---
title: "Downloading file from shell?"
date: 2011-03-28
forum: General Help
---

### Post by nkae100 on 2011-03-28
How can I download a file via HTTP from a shell?

---

### Post by lisati on 2011-03-28
With the "wget" command. I have rarely used it directly myself, so you might have to do "man wget" to check out the options.

---

### Post by nkae100 on 2011-03-28
"wget <file>"

> wget [http://ubuntuforums.org/images/misc/ubuntulogo.png](http://ubuntuforums.org/images/misc/ubuntulogo.png)

---

### Post by mkhurram92 on 2011-03-28
> **nkae100 said:**
> "wget <file>"

you might want to download some large files with wget, and be able to log out and have these files still download for you. 

then u could use
 
nohup wget [http://www.example.com/some_large_file](http://www.example.com/some_large_file) &

to have wget download these files in the background, and continue to do so even after you log out.

---

