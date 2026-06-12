---
title: "Problem extracting files"
date: 2010-08-01
forum: General Help
---

### Post by beliyyal on 2010-08-01
I have been having a problem extracting files lately. Sometimes archives will extract fine, and sometimes they won't. And it's not just one single archive type that has problems, it's several different ones; like .rar, .ace, .zip, .7z etc. I have all the proper programs to extract/mount these files, but sometimes they don't work right. I am running 10.04, this is among one of the few problems I have found. Is anyone else having this problem? Earlier I tried to extract a .ace file, and it gave an error with no command line output. Does anyone have an idea of how to fix this? I can provide more information if needed.

---

### Post by sikander3786 on 2010-08-01
Hi.

From where did you get those compressed files? Download? Are you sure they are not broken. Are they from authentic sources?

---

### Post by jerenept on 2010-08-01
What error messages are you getting? the error messages open in a window after file-roller attempts to open an archive.

Maybe the helper applications are not installed? 

```
 sudo aptitude install unace-nonfree unrar p7zip
```

Other than that, and with no more info; I really can't help.

---

### Post by richardh9936 on 2010-08-09
Thanks, .rar fixed.

---

