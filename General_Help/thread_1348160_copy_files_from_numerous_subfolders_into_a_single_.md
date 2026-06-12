---
title: "copy files from numerous subfolders into a single folder"
date: 2009-12-06
forum: General Help
---

### Post by kilee on 2009-12-06
Hi friends!
I have thousands of jpgs in numerous subfolders within a folder called pictures. I would like to copy all of the files into a single folder. Is there an easy way to do this?

This was already answered in [this post]("http://ubuntuforums.org/showthread.php?t=671220") this way:
find ~/Pictures -name "*.jpg" -exec cp \{\} ~/All_Pictures/ \;
[B]My question is how to copy only files with a minimum size of 100k for example?
Can some instruction be added to this one? 
Thanks a lot!!
[/B]

---

### Post by kaibob on 2009-12-07
> **kilee said:**
> [B]My question is how to copy only files with a minimum size of 100k for example?
Can some instruction be added to this one? 
Thanks a lot!!
[/B]
The find command has a -size option. The sytax would be -size +100k.  See the find man page for detail.

---

### Post by kilee on 2009-12-07
Thanks a lot!

---

