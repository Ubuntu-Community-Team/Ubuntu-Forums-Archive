---
title: "Konserve problems"
date: 2006-01-30
forum: General Help
---

### Post by olale on 2006-01-30
Hi!

I have tried to use konserve for making backups, but I seem to fail miserably every time. The only thing that happens when I set up a backup scheme and then test it is that a 2 byte file is created with the name of the destination, but nothing else happens. If I want to redo the backup, konserve complains that there is already a file with the same name as the destination.. This is the simplest possible use case, with a folder of 1 file as source that I have created on my desktop just to test konserve, and the destination is also a (new) folder on my desktop.

I'm using KDE 3.5 from the official sources and konserve 0.10.3 if that's any help..

---

### Post by wanger123 on 2006-02-04
I also had this prob once. Can't quite remember the solution but I think if you tell it to backup up to a file, you also have to put the file type (tar.gz) in the backup path
eg /home/backup/mybackup.tar.gz

cheers
wanger

---

### Post by olale on 2006-02-08
I didn't think I should specify a file but rather a directory as destination. Or how is konserve supposed to work?

---

