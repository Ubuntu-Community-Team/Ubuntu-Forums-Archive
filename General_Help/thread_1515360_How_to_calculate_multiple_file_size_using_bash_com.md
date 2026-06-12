---
title: "How to calculate multiple file size using bash command / script?"
date: 2010-06-22
forum: General Help
---

### Post by sundar_ima on 2010-06-22
I know this can be done by using stat command for a single file. Is there any other command used to calculate size of multiple files? In some cases i store few file links in a seperate text file and  want to calculata size of all linked files. How do i go about it?

---

### Post by sisco311 on 2010-06-22
Try something like:
```
tr -s '\n' '\0' < file.txt | du -sch --files0-from=-
```

---

### Post by justleen on 2010-06-22
or something like
```

du -hs *.png
du -chs file1 file2 file3 file4

```

Last example is offcourse the same as the answer above, only directly (withtout piping).
method used depends a lot on how many filesize you want to add to gether

---

### Post by sundar_ima on 2010-06-29
Thank you for your reply guys.All three method worked as stated. However there is an issue. When i calculate file/foler size from terminal it says 4.3 GB and when i calculate using GUI method (Right click -- >> Properties) it says 4.2 GB. Which one is correct and why there is a difference??

---

### Post by justleen on 2010-06-30
The "GUI" uses (like system monitor) use MiB,mebibytes. The du command uses MB, megabytes
1 MiB | 1.049 MB  (megabytes)
      | 1.049x10^6 bytes
      | 8.389 Mb  (megabits)
      | 8.389x10^6 bits

---

### Post by sundar_ima on 2010-07-01
Thank you.

---

