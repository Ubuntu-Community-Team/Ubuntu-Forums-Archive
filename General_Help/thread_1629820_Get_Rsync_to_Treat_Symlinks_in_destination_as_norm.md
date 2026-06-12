---
title: "Get Rsync to Treat Symlinks in destination as normal directories"
date: 2010-11-24
forum: General Help
---

### Post by Moyamo on 2010-11-24
Hello I'm running Ubuntu on a Pc. I also have a computer that runs windows xp. I have a 8gb flash drive and a keep a Microsoft Window Briefcase on it to Backup my windows files.  I also use rsync to backup my Ubuntu files. Some files like Word and Open office documents will be on both copies. It is impractical and a waste of memory to have to copies of the exact same file in two different directories (One in the Ubuntu Backup Directory and One in the Windows Backup directory).  What I did was I created symlinks that are linked to the Windows folders in the Microsoft Window Briefcase in place of the files in the Ubuntu Backup Directory.

The problem I have is that rsync won't treat these symlinks in the destination folder as normal directories and in the end don't get backed up. Is the any way top make rsync treat these symlinks as normal directories?

Thanks in advanced

---

### Post by wt8008 on 2010-11-24
What is your rync command for creating the backups?

Please read some sections from the manpage
[http://manpages.ubuntu.com/manpages/maverick/en/man1/rsync.1.html#contenttoc21](http://manpages.ubuntu.com/manpages/maverick/en/man1/rsync.1.html#contenttoc21)
and
[http://manpages.ubuntu.com/manpages/maverick/en/man1/rsync.1.html#contenttoc11](http://manpages.ubuntu.com/manpages/maverick/en/man1/rsync.1.html#contenttoc11)
and
[http://manpages.ubuntu.com/manpages/maverick/en/man1/rsync.1.html#contenttoc12](http://manpages.ubuntu.com/manpages/maverick/en/man1/rsync.1.html#contenttoc12)
for more details.

I believe the option you need is -L or --copy-links (they both are the same thing)

---

### Post by Moyamo on 2010-11-25
You miss understand me. I don't want to copy symlinks on the source folder to the destination folder as normal directories. I want to keep symlinks on the destination folder as symlinks even if they're normal directories of the source folder. I want rsync to treat symlinks as normal directories but keep them symlinks.

---

