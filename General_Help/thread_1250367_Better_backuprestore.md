---
title: "Better backup/restore"
date: 2009-08-26
forum: General Help
---

### Post by lduperval on 2009-08-26
Hi,

I have been using simple backup to do my backups. It does a fine job, but I am less than thrilled about the restore part of the equation.

I am restoring portions of a system and I need to pick a file here and there to restore, instead of restoring everything. However, the simple restore procedure doesn't allow me to piock and choose the files I want. I can either pick on file or one directory. I can't select using Ctrl-click.

My questions:
[LIST]
[*]Is there a way to select multiple files when extracting information? What tool can I use for that?
[*]Is there a better backup procedure, which is as simple to set up and run daily?
[/LIST]

Thanks,

L

---

### Post by fishy6969 on 2009-08-26
Are you backing up to a removable disk or network drive?

Either way, good old rsync might be the simplest way. It stores the files individually rather than in a big tar.gz file. There are GUI's for it but they are not much cop IMHO. Better to use the command line and run periodically as a cron job. There's a number of tutorials around - an OK one is here [http://sial.org/howto/rsync/](http://sial.org/howto/rsync/)

---

### Post by lduperval on 2009-08-26
Removable disk.

Thanks. Any idea if a different gui/system can work to extract only the files I want from the tar file? Otherwise, I'll just figure it out with the -F flag for tar.

Thanks,

L

---

### Post by fishy6969 on 2009-08-26
Not really. The gui tools I've tried can't seem to handle the large tar files simple backup produces.

---

