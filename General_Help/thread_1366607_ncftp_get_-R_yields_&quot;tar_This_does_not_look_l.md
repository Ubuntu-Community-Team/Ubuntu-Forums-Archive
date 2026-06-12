---
title: "ncftp get -R yields &quot;tar: This does not look like a tar archive&quot;"
date: 2009-12-28
forum: General Help
---

### Post by Xnyper on 2009-12-28
First of all, thanks for taking a look here, I really appreciate your help.

I am trying to make a backup of my site via ftp.  I learned that the standard ftp doesn't get directories recursively, so I installed NcFTP.

ncftp allows me to log-in just fine, and when I go the the folder I want to back up I type:
```
get -R foldername
```
Which yields:
```
tar: This does not look like a tar archive
tar: Error exit delayed from previous errors
foldername/index.php:                                  397.00 B    1.84 kB/s  
// output omitted
foldername/xmlrpc.php:                                  91.25 kB   98.18 kB/s
```

When I look at the directory that everything was downloaded to all of the files are present within the folder and all of it's subfolders are also present.  However, all of the subfolders are empty.  As if it only recursed one level.

I searched around on this and found nothing useful, am I doing something wrong?  please advise.

---

### Post by fargle on 2009-12-28
Well, I'm not sure about NcFTP (although I used to work with the author, Mike Gleason), but since you just installed it and don't appear to be heavily invested, might I suggest you try Filezilla instead?  I think it will do what you want with a nice graphical interface to boot.

---

### Post by Xnyper on 2009-12-28
Thanks fargle! worked like a charm.

I think a lot of users look for a gui solution first, so to balance them out I usually look for a CLI solution first.  Perhaps I should break that habit: this gui tool did save me some time...

---

### Post by synapsys on 2009-12-28
> **Xnyper said:**
> Thanks fargle! worked like a charm.

I think a lot of users look for a gui solution first, so to balance them out I usually look for a CLI solution first.  Perhaps I should break that habit: this gui tool did save me some time...

Yeah, but then you get some applications where the command line saves you time over the gui. I usually use both (where available) and remove the one I don't like.

---

### Post by AirOnSkin on 2010-12-17
I just had the same problem and switching to another tool is not an option. For people who like to stick to ncftp and are annoyed with the tar message, try the option -T:

from man: "-T      Do  not  use  automatic on-the-fly TAR mode for downloading whole directory trees.  ncftpget uses TAR whenever possible since this usually preserves symbolic links and file permissions.  TAR mode can also result in faster transfers for directories containing many small files, since a single data connection can be used rather than an FTP data connection for each small file.  The downside  to  using  TAR  is that it forces downloading of the whole directory, even if you had previously downloaded a portion of it earlier, so you may want to use this option if you want to resume downloading of a directory."

Have fun :)

Air

---

