---
title: "how do you find out how much free space you have?"
date: 2009-12-20
forum: General Help
---

### Post by yawnmoth on 2009-12-20
I downloaded a large file with Firefox and tried to download another only to get a "you don't have sufficient free space" error. I deleted what I downloaded but I'm still getting the error.

In Windows, you'd have to empty the Recycle Bin as well. In Ubuntu... i have no clue. Any ideas?

Also, it'd be nice to see the full capacity of a filesystem - not just the available free space (which is all that the File Browser tells you and even that's not dependable since right now the File Browser isn't telling me anything).

---

### Post by Puck7 on 2009-12-20
In System>Administration>System Monitor's File Systems tab you can see how much space you have on your harddrive(s). In ubuntu you can simply clear the Trash also.

---

### Post by Jonwenger on 2009-12-20
Open a Terminal (Alt + T) and type the command: ```
df -h
``` This displays your free disk space + size + used disk space and the directory.

---

