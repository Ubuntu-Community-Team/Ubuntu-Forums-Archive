---
title: "strange rsync message"
date: 2010-10-06
forum: General Help
---

### Post by evaristegalois on 2010-10-06
when I sync a directory on my flash drive with my hard drive I get
these messages (file-1 to file-10 being files recently created): 

> rsync: chgrp "/media/Kingston/.file-1.fwZRAO" failed: Operation not permitted (1)
rsync: chgrp "/media/Kingston/.file-2.TI9uZ6" failed: Operation not permitted (1)
rsync: chgrp "/media/Kingston/.file-3.1UzWtp" failed: Operation not permitted (1)
rsync: chgrp "/media/Kingston/.file-4.Rh813H" failed: Operation not permitted (1)
rsync: chgrp "/media/Kingston/.file-5.D2zsJ0" failed: Operation not permitted (1)
rsync: chgrp "/media/Kingston/.file-6.287sHj" failed: Operation not permitted (1)
rsync: chgrp "/media/Kingston/.file-7.LoP6XC" failed: Operation not permitted (1)
rsync: chgrp "/media/Kingston/.file-8.F15imW" failed: Operation not permitted (1)
rsync: chgrp "/media/Kingston/.file-9.zPjOPf" failed: Operation not permitted (1)
rsync: chgrp "/media/Kingston/.file-10.bxlJoz" failed: Operation not permitted (1)
rsync: chgrp "/media/Kingston/.file-11.28ZV2S" failed: Operation not permitted (1)

but ls -a shows no such files, and when I try to remove them (as a
superuser) I get these messages:

> rm: cannot remove `/media/Kingston/.file-1.TI9uZ6': No such file or directory
rm: cannot remove `/media/Kingston/.file-2.1UzWtp': No such file or directory
rm: cannot remove `/media/Kingston/.file-3.Rh813H': No such file or directory
rm: cannot remove `/media/Kingston/.file-4.D2zsJ0': No such file or directory
rm: cannot remove `/media/Kingston/.file-5.287sHj': No such file or directory
rm: cannot remove `/media/Kingston/.file-6.LoP6XC': No such file or directory
rm: cannot remove `/media/Kingston/.file-7.F15imW': No such file or directory
rm: cannot remove `/media/Kingston/.file-8.zPjOPf': No such file or directory
rm: cannot remove `/media/Kingston/.file-9.bxlJoz': No such file or directory
rm: cannot remove `/media/Kingston/.file-10.28ZV2S': No such file or directory

What's going on? Is it a virus? I ran sophos antivirus software on the
flash drive, but the diagnostics came up clean.

---

### Post by surfer on 2010-10-06
what filesystems are you using on the source and the target directory?

---

### Post by Quarkrad on 2010-10-06
I'm a newbie so not really qualified to respond but I had a similar rsync output when copying to to backup HD.  My problem was permissions - the owner of the HD was root and I was not so rsync did no like it.  Who is the the owner of your destination drive?  It may be a case that you need to change the ownership.

---

### Post by SeijiSensei on 2010-10-06
When rsync copies a file, it creates it first as a Unix "hidden" file, one that begins with a period as the first character, then renames it when the copy is complete.  Most flash drives come formatted with the Microsoft FAT32 filesystem which doesn't support these types of filenames (or anything else like permissions, symlinks, etc.).

You've got two options.  If you're only going to be using the drive with Linux, then you should reformat it with ext4.  If you need to share the drive with Windows machines, then you need to take another approach to backups.  You can create a compressed "tarball" of the files to be backed up like this:

tar cjvpf backup.tar.bz2 /path/to/my/source/files

then copy the resulting file called backup.tar.bz2 to the flash drive with the "cp" command.

---

### Post by evaristegalois on 2010-10-08
Thank you for your help. This probably explains it. My flash drive is FAT. Although I must say that the problem only started occurring a few days ago, and I didn't have any problems with the flash drive before when it was also FAT. But I just needed to know that there isn't a virus creating mysterious files. It's just rsync. That's fine.

---

