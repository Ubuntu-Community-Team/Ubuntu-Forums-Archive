---
title: "Deleted file still there, somewhere, taking up space"
date: 2010-05-16
forum: General Help
---

### Post by kudzu on 2010-05-16
Hey everyone,

I recently made the dumb mistake of using tar to make a backup of my "/" on my "/" when my "/" didn't have near enough space to store the backup.  I received a warning message, so I canceled the terminal process and used nautilus to delete what amount of the backup had already been saved.  That didn't seem to free up any space on my "/" like it should have, though.  In an effort to find any hidden trash files that needed to be deleted, I used this terminal command:

```
jake@JakeLaptop:~$ ls -al /
total 104
drwxr-xr-x  22 root root  4096 2010-05-16 15:09 .
drwxr-xr-x  22 root root  4096 2010-05-16 15:09 ..
drwxr-xr-x   2 root root  4096 2010-01-29 14:24 bin
drwxr-xr-x   3 root root  4096 2010-04-30 00:43 boot
lrwxrwxrwx   1 root root    11 2008-07-09 04:10 cdrom -> media/cdrom
drwxr-xr-x  15 root root  3800 2010-05-16 17:15 dev
drwxr-xr-x 154 root root 12288 2010-05-16 17:15 etc
drwxr-xr-x   4 root root  4096 2010-02-17 14:41 home
drwxr-xr-x   2 root root  4096 2008-07-02 19:16 initrd
lrwxrwxrwx   1 root root    33 2010-04-30 00:43 initrd.img -> boot/initrd.img-2.6.31-21-generic
lrwxrwxrwx   1 root root    33 2010-03-07 16:34 initrd.img.old -> boot/initrd.img-2.6.31-20-generic
drwxr-xr-x  19 root root 12288 2010-02-05 02:30 lib
drwx------   2 root root 16384 2008-07-09 04:10 lost+found
drwxr-xr-x   3 root root  4096 2010-05-16 17:15 media
drwxr-xr-x   2 root root  4096 2008-04-15 14:53 mnt
drwxr-xr-x   7 root root  4096 2010-03-24 23:56 opt
dr-xr-xr-x 185 root root     0 2010-05-17 02:14 proc
drwxr-xr-x  25 root root  4096 2010-03-24 23:55 root
drwxr-xr-x   2 root root  4096 2010-04-14 23:58 sbin
drwxr-xr-x   2 root root  4096 2009-03-07 01:21 selinux
drwxr-xr-x   3 root root  4096 2010-01-09 18:05 srv
drwxr-xr-x  12 root root     0 2010-05-17 02:14 sys
drwxrwxrwt  15 root root  4096 2010-05-16 17:16 tmp
drwxr-xr-x  12 root root  4096 2010-02-05 03:07 usr
drwxr-xr-x  15 root root  4096 2008-07-02 19:34 var
lrwxrwxrwx   1 root root    30 2010-04-30 00:43 vmlinuz -> boot/vmlinuz-2.6.31-21-generic
lrwxrwxrwx   1 root root    30 2010-03-07 16:34 vmlinuz.old -> boot/vmlinuz-2.6.31-20-generic
jake@JakeLaptop:~$ 

```

As you can see, though, there don't appear to be any trash files.  Further investigating the problem, I used GParted to look at my partitions and I also discovered that I cannot shrink my "/" partition at all (my "/" partition is about 11GIB, but my filesystem is less than 5GIB).  On reboot I received the low storage space message again.

Any ideas how to solve this mystery and get my space back?

---

### Post by rjcroy on 2010-05-16
have you tried using the Disk Usage Analyzer application (baobab) to find what files are taking all the space? 

The command line alternative program would be du.

---

### Post by kudzu on 2010-05-16
Ok, I tried Disk Usage Analyzer but now I'm more confused.  It seems to be telling me that I have free space and that I don't have free space at the same time, and that most of the space that's currently in use is taken up by files on "/home," but I have "/home" on a different partition.  I don't have much experience with Disk Usage Analyzer, though, so I could be misinterpreting things.  I took a screenshot and I've attached it here, along with a screenshot of my Disk Utility.  If it helps, I think the backup was about 4-5GB when I deleted it.

---

### Post by plucky on 2010-05-16
This [guide](http://ubuntuforums.org/showthread.php?t=898573&highlight=drs305) is useful for finding missing hard disk space.

Good Luck

---

### Post by kudzu on 2010-05-16
Hey, that's a great guide.  I used one of their commands to find the file that's causing me problems:

```
jake@JakeLaptop:~$ sudo find / -name '*' -size +3G
find: `/proc/3569/task/3569/fd/5': No such file or directory
find: `/proc/3569/task/3569/fdinfo/5': No such file or directory
find: `/proc/3569/fd/5': No such file or directory
find: `/proc/3569/fdinfo/5': No such file or directory
/root/.local/share/Trash/files/backup.tgz
find: `/home/jake/.gvfs': Permission denied
jake@JakeLaptop:~$ 

```

It's the /root/.local/share/Trash/files/backup.tgz file that I meant to delete.  I used the guide's commands ("sudo chown -R jake /root/.local/share/Trash/" and "rm -rf ~/.local/share/Trash") to take ownership of the file and delete it, but it still shows up though.  It won't delete.  Any idea what I'm doing wrong here?

---

### Post by plucky on 2010-05-16
> It's the /root/.local/share/Trash/files/backup.tgz file that I meant to delete. I used the guide's commands ("sudo chown -R jake /root/.local/share/Trash/" and "rm -rf ~/.local/share/Trash") to take ownership of the file and delete it, but it still shows up though. It won't delete. Any idea what I'm doing wrong here?

The path to the file is incorrect.

cd /root/.local/share/Trash/files/

is not the same as

cd ~/.local/share/Trash/files/

The first one goes to root Trash whereas the second one goes to the Trash in your home partition,so the command "rm -rf ~/.local/share/Trash" is deleting the Trash in your home partition,not in the /root partition.

Try ```
cd /root/.local/share/Trash/files/
ls -l
sudo rm -rf backup.tgz

```

The ls -l makes sure you are in the right directory if you can see the backup.tgz file,because the "sudo rm -rf" command is a very powerful command that can delete your system if used incorrectly,so be careful.


Good Luck

---

### Post by kudzu on 2010-05-17
Ah, that did the trick.  Thanks a ton.  I'm still working on my understanding of the file tree.  While removing backup.tgz I also noticed a bunch of other old files in my root trash.  Some of them wouldn't remove, for some reason, when I attempted to remove them using their exact file location (they were old photos I had named with spaces and commas).  So, I used "rm -rf" for the whole root trash directory.  That took care of it, but apparently the root trash directory no longer exists.  That isn't a problem, is it?  Will root recreate its trash directory by itself as the need arises?

---

### Post by plucky on 2010-05-17
> So, I used "rm -rf" for the whole root trash directory. That took care of it, but apparently the root trash directory no longer exists. That isn't a problem, is it? Will root recreate its trash directory by itself as the need arises?

I think it will re-create itself as the need arises.

Good Luck

---

### Post by kudzu on 2010-05-17
Cool, thanks.

---

### Post by kipjones on 2010-08-05
Hey, thanks a lot.  This forum consistently rocks; folks here are really great about taking the time to explain issues and solve problems.

Cheers!  I've got my mystery 6GB back!

---

### Post by ixifx on 2010-11-05
I noticed this problem deleting a .rar file today after I had extracted it's contents to another physical disk.  the file I'm looking for doesn't show up by name, but I'm curious what these files are -

find: `/proc/2992/task/2992/fd/5': No such file or directory
find: `/proc/2992/task/2992/fdinfo/5': No such file or directory
find: `/proc/2992/fd/5': No such file or directory
find: `/proc/2992/fdinfo/5': No such file or directory

---

