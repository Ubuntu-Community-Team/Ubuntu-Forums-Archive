---
title: "Error while backing up with TAR"
date: 2010-06-26
forum: General Help
---

### Post by bgutt3r on 2010-06-26
I have tried multiple times to backup my entire Ubuntu system partition into a tarball with the following command;

sudo tar -cvpzf ubuntu-system-backup-6-25-2010.tar.gz --exclude=/ubuntu-system-backup-6-25-2010.tar.gz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/dev --exclude=/root/.local/share/Trash --exclude=/home/brandon/.local/share/Trash --ignore-failed-read /

...but every single time, TAR fails with a "file changed as we read it" error. To say the least, --ignore-failed-read did little to help this type of error. Also, it always occurs on the file /lib32/libssl.xxxwhatever, except for the one time i excluded it, when it instead failed on /lib32/libcrypto.xxx, the very next file. I don't think it would be a useful backup if i excluded all of /lib32, and i'm worried it may even do the same for /lib64. anyone solve an issue like this?

---

### Post by dandnsmith on 2010-06-26
Better not to try the job from the system partition that you're currently running from. You always have this error possibility. If you separate out all the variable stuff, you stand a much better chance - standard practice when mainframe Unix was the thing.

---

### Post by bgutt3r on 2010-06-26
So, basically, try running it from a live cd? are there any special precautions or just cd to the root of the partition and run the tar?

It would sure be nice to figure this out though, then I could schedule automatic backups...

---

### Post by gmargo on 2010-06-26
It's a waste of time and space to backup binary files that can be easily reloaded from scratch.  I would backup /etc, /root, /var/lib/dpkg, /var/log, /var/mail, /var/spool/cron, /var/www, /home, and the output of dpkg -l for the list of installed packages.  I believe it's a poor choice to compress on the fly too; I keep that separate.  Also any databases should not be backed up as binary unless the database program is stopped; you're better off dumping the important records to a file and back that up.

---

