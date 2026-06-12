---
title: "CIFS ls fails with bracket in filename"
date: 2011-04-15
forum: General Help
---

### Post by NickPrecision on 2011-04-15
I have searched around for any documentation of this and haven't found any, so I am hoping someone here might know.

I have a Windows share with a number of files that are mounted via CIFS in fstab. I noticed the file count did not match in linux how many files were in the folder. I figured out that CIFS was listing the files and folders alphabetically, and it was stopping on any file with a bracket (either [ or ]) in the name, and it won't list any more. For instance, if my files were:

a.txt
b.txt
c[c].txt
d.txt

When ls was run, it would only show
a.txt
b.txt

However, brackets can be in filenames in Linux, so I don't get what the problem is? And, it seems to be this wasn't always a problem, it could be a recent update created it? I am using Proposed updates on mythbuntu 10.10.

---

