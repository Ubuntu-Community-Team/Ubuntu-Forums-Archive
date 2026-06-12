---
title: "Using DIFF: Output filenames only"
date: 2011-06-16
forum: General Help
---

### Post by askeuhd on 2011-06-16
I am using the diff command with the -r option, to compare a large number of files and files in subdirectories. 

My main interest is to find out **which** files have been changed, and not what the actual changes are, and since a lot of files has been changed, it would be a lot easier to view the file names only. 

Is there and option for diff that might do this, or does there exist a similar tool/command that could do the job?

Thanks a lot,

Aske

---

### Post by Dave_L on 2011-06-16
-q or --brief

Output only whether files differ.

---

