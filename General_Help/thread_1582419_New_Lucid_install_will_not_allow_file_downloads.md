---
title: "New Lucid install will not allow file downloads"
date: 2010-09-26
forum: General Help
---

### Post by meanmrmustard on 2010-09-26
No matter what site I try to get a file from, when trying to download - let's say - a .pdf file, I get a dialog box that tells me that the file could not be saved,"because the source file could not be read. Try again later, or contact the server administrator."

This is on my laptop only, a clean install of Lucid Lynx, the files download fine on either of my desktop machines, each an earlier Ubuntu release.
I'm using Firefox and cannot try another browser since I'm unable to download one.
Can't seem to find anything relevant in the log files.
What could be happening?
Thanks

---

### Post by TeoBigusGeekus on 2010-09-26
It's a firefox problem.
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1568728]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1568728")

---

### Post by anirudhtomer on 2010-09-26
I think since you are able to browse it means the http request are not filtered but since you try to download a PDF file(which can be using either FTP or HTTP) & if the FTP port requests are filtered then that can be reason that you get that error.

Try to download that using wget command on the shell.

I am not sure about the exact reason of such behavior.ah!:confused: just guessing the possible reasons.

---

