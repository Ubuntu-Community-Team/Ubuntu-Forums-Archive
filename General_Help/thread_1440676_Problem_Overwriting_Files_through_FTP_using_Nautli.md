---
title: "Problem Overwriting Files through FTP using Nautlius"
date: 2010-03-27
forum: General Help
---

### Post by robwgibbons on 2010-03-27
I am experiencing a bug when overwriting files on FTP servers using the default nautilus FTP client.

When I upload a file to replace an existing file via FTP, after I confirm the prompt asking me to overwrite, the content of the newly uploaded file is appended to the existing file's contents. The resulting file contains the content from both files. In order to fix this bug, I am forced to delete the existing file before uploading the new file.

If I upload the same file multiple times, the error will continue to occur and append the new file to the existing file.

I am using 64-bit Ubuntu 9.10 which is up to date.

I would appreciate any suggestions, or a shout from anyone else experiencing this problem.

---

### Post by hannenz on 2010-05-25
Hi! Unfortunately no solution - but I have the exactly same problem here; it seems not to be Ubuntu Specific but rather GNOME / Nautilus specific, since I had the same issue under 32bit Arch Linux as well as now on a Lucid Machine (64bit).

---

