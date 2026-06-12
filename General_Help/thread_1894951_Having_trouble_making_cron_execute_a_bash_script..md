---
title: "Having trouble making cron execute a bash script."
date: 2011-12-13
forum: General Help
---

### Post by terryit3 on 2011-12-13
I have a bash file with some backup commands in it:

```
#!/bin/bash
#!/bin/bash
sudo mount -t smbfs //10.1.1.12/file /mnt/file-backup/ -o username=admin,password=pasword here for testing

mv /mnt/file-backup/etc_old /mnt/file-backup/etc_old2
mv /mnt/file-backup/home_old /mnt/file-backup/home_old2
mv /mnt/file-backup/var_old /mnt/file-backup/var_old2
mv /mnt/file-backup/root_old /mnt/file-backup/root_old2

mv /mnt/file-backup/etc /mnt/file-backup/etc_old
mv /mnt/file-backup/home /mnt/file-backup/home_old
mv /mnt/file-backup/var /mnt/file-backup/var_old
mv /mnt/file-backup/root /mnt/file-backup/root_old

mkdir /mnt/file-backup/etc
mkdir /mnt/file-backup/home
mkdir /mnt/file-backup/var
mkdir /mnt/file-backup/root

rsync -av --progress --log-file=/home/tech/Desktop/backuplogs/$(date +%Y%m%d)_rsync.log --exclude "/etc/X11/"  --exclude "/var/cache/" --exclude "/home/tech/.gvfs" /home /etc /root /var /mnt/file-backup/

rm /mnt/file-backup/etc_old2 -R
rm /mnt/file-backup/home_old2 -R
rm /mnt/file-backup/var_old2 -R
rm /mnt/file-backup/root_old2 -R

umount /mnt/file-backup

```

I am trying to have this script executed via the /etc/crontab with a line that reads, 

43 16   * * *   root    cd /root/cron && ./rsync-shell.sh

The file is located in /root/cron (from previous testing), and has 755 file permissions. It was set to 700, but I added more privilege for testing.

Log file says:

2011/12/13 16:43:02 [867] receiving file list
2011/12/13 16:43:02 [867] rsync: symlink "/mnt/file-backup/etc/grub.conf" -> "/boot/grub/menu.lst" failed: Operation not supported (95)
2011/12/13 16:43:02 [867] .d..t...... etc/
2011/12/13 16:43:02 [867] rsync: symlink "/mnt/file-backup/etc/motd" -> "/var/run/motd" failed: Operation not supported (95)
2011/12/13 16:43:02 [867] >f+++++++++ etc/.pwd.lock
2011/12/13 16:43:02 [867] >f+++++++++ etc/adduser.conf
2011/12/13 16:43:03 [867] >f+++++++++ etc/adjtime
2011/12/13 16:43:03 [867] rsync: writefd_unbuffered failed to write 4 bytes [generator]: Broken pipe (32)
2011/12/13 16:43:03 [867] rsync error: received SIGUSR1 (code 19) at log.c(230) [generator=2.6.9]


Any advice?

---

### Post by papibe on 2011-12-13
This is what I think is happening:

You are trying to create a symbolic link in a remote share. Since there's no 'network links', what it is created is a link to /boot/grub/menu.lst in the remote system. That by itself is a security issue, thus it is being block.

One simple solution would be to tell rsync to copy the content of the linked file instead of try to create the link. To do that use the option --copy-links (or -L for short). For example:
```
rsync -avL --progress ...
```
BTW, a couple of pointers:
[LIST]
[*]The use of smbfs is no longer recommended, use cifs instead (read about it [here]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")).
[*]Since you are running the script as root, sudo is not necessary to mount the share.
[/LIST]
I hope that helps. Tell us how it goes.
Regards.

---

### Post by terryit3 on 2011-12-14
Your advice seems to have fixed it! Thank you.

---

### Post by terryit3 on 2011-12-14
I may have spoken too soon.

The majority of the files were backed up, but when it started backing up my admin users home directory, it failed with the errors: Note: I was logged in as the admin user when the script failed. I'm not sure of this had anything to do with it.)


2011/12/14 11:09:50 [26472] rsync error: received SIGUSR1 (code 19) at main.c(1182) [generator=2.6.9]

2011/12/14 11:09:50 [26472] rsync: writefd_unbuffered failed to write 78 bytes [generator]: Broken pipe (32)

I've seen these two errors before, but there doesn't seem to be a definite cause for it (that I could find).

---

### Post by papibe on 2011-12-14
I haven't seen that error before.

Let's try to get more information, add more verbose to your command, and add file log. Something like:
```
rsync -aL -vvv --log-file=/path/to/log ...
```
Then check the log and tell us what you see. Paste the parts that may give us some clues.

If I have to guess, could a filename with special characters or a timeout on the connection.

Regards.

---

### Post by terryit3 on 2011-12-15
These were the last few lines of the log file.

2011/12/15 12:52:56 [14199] generate_files finished
2011/12/15 12:52:56 [14199] rsync error: some files could not be transferred (code 23) at main.c(872) [generator=2.6.9]
2011/12/15 12:52:56 [14199] _exit_cleanup(code=0, file=main.c, line=872): about to call exit(23)

---

### Post by terryit3 on 2011-12-15
After reading up on this error, all evidence points to RSYNC actually completing, but has file permission denied errors.

[http://lists.samba.org/archive/rsync/2008-July/021314.html](http://lists.samba.org/archive/rsync/2008-July/021314.html)

---

