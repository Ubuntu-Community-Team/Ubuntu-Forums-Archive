---
title: "Finding Similarities in Two text documents"
date: 2010-09-22
forum: General Help
---

### Post by jjjjeremy on 2010-09-22
Hello,

What program can I use to find similarities between two documents? I've tried diff and colordiff, but I have no idea how to read the output. As well, they show the differences, and I want to look for similarities and common phrases. I'm a law student editing an article, and one of the citations that I have says that a certain statute takes language from a supreme court case, and I don't want to manually compare the entire case to the entire statute.

This has to exist, but I can't find it anywhere. I thought that I would be able to find it in some sort of plagiarism program, but I can't find anything for Ubuntu.

Thanks for your help,

- Jeremy

---

### Post by ajgreeny on 2010-09-22
This may still not be quite what you are after, but ```
diff -y file1 file2
``` will show both files, side by side in two columns which may make it easier to see similarities.

EDIT:
I've also just come across a package called **docdiff** which does the same thing but even better than plain **diff**.

I think it's in the repos, but I'm using Linux Mint Debian Edition (LMDE) at the moment so can't be sure about ubuntu repos.

---

