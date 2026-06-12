---
title: "Using an FTP server with ext3 and NTFS filesystems"
date: 2009-10-19
forum: General Help
---

### Post by theluddite on 2009-10-19
**Here's the situation:**

You're at a friend's house and want to access one of your files on your external hard drive at home -- without installing anything on your friend's machine (i.e. putty).

**Here's my solution:**

[LIST=1]
[*]I've set up ProFTPD 1.3.1 on my ubuntu box using [this]("http://ubuntuforums.org/showthread.php?t=79588") tutorial since even windows has a native ftp utility.
[*]I mounted my external hard drive to a mount point within the server's directories.
[*]I can log in to the server and download files just fine.
[/LIST]

**Here's my problem:**

I can't open the file.  Obviously it works fine with linux, but with windows I've never been able to play the file, not even with VLC media player.

**Here's my guess:**

My external HD is formatted as ext3.  Could it be that using ftp to download the file to an NTFS filesystem is causing the problem?

---

### Post by theluddite on 2009-10-27
Anybody?  I'm sure this has a simple solution.  I really just want to know if anyone knows why ftp wouldn't work between two different filesystems.

---

### Post by Grim76 on 2009-10-27
You might try an md5sum of both files to make sure they are the same.

---

