---
title: "Any good &quot;rsync --exclude&quot; tutorials?"
date: 2010-02-22
forum: General Help
---

### Post by wolfv6 on 2010-02-22
Please recommend a "rsync --exclude" tutorial for backups.

How did you learn to --exclude?

Thank you.

---

### Post by quixote on 2010-02-24
How I learned to --exclude was with a lot of searching and cobbling together bits and pieces. :D   A good thorough explanation would be nice!  The [howto at everythinglinux]("http://everythinglinux.org/rsync/") is good, but doesn't go very far with --excludes.

One thing I've never had any luck with is using an exclude file.  rsync just ignores it for me.  I've always had to include the whole list right in the command.

Some perhaps useful examples:
> --exclude ".*/"      *.......to exclude hidden dot directories in the home dir (that path assumes rsync starts from /home/user)*
--exclude ".*"     [I].......would exclude hidden files, but not hidden directories
other useful excludes for home dirs: [/I]
--exclude ".gvfs" --exclude "*Trash*/" --exclude ".thumbnails/" --exclude ".mozilla/*/*/Cache/"  --exclude="*~"  *.......(that last dumps gedits duplicate files)*

--exclude "/dev/" --exclude "/lost+found/" --exclude "/media/" --exclude "/mnt/" --exclude "/proc/" --exclude "/tmp/"  *.......to exclude temporary or recreated dirs when doing a system backup, as well as any other filesystems that could be mounted on /media or /mnt* 

---

### Post by Blackbird_13 on 2010-02-24
Not found any comprehensive tutorial. Mainly relied on trial & error.
I've created a file Exclude.txt which excludes 2 directory paths:

- Images/**
- simplebackup/**

-    means,  exclude
/** means, exclude sub directories (I think it applies to all sub directories, but I've not really tested this)

my rsync command is:

rsync -rtpv --exclude-from=/home/blackbird/bin/Exclude.txt -e ssh /home/blackbird blackbird@***.***.*.**:/home/

It seems to work ok.

---

### Post by elcico on 2011-10-11
Hello *,
First post here!
As I also had to search quite a lot before finding a solution to exclude directories (but not folders with the same name of excluded dirs), just wanted to add that I had to do this to make rsync work:

--exclude '/Documents and Settings'

My complete command was:

rsync -av --progress --exclude '/Documents and Settings' --exclude '/Programs' --exclude '/WINDOWS' /home/user/mount/origin/ /home/user/mount/destination/


where the directories "Documents and Settings"  "Programs" and "WINDOWS" were mounted directly under the mount point.

To make it clear... I mounted a windows drive with samba under /home/user/mount/origin/
so, for example, "Documents and Settings" complete path was:

/home/user/mount/origin/Documents and Settings

In this way other directories, named like the ones to be excluded by rsync, are not excluded; if you only insert, in the exclude option, the name of the dir without the initial slash, other dirs with the same name will be excluded too instead.

Also rsync can deal with spaces in folder names, so no additional characters are needed for dirs with spaces in the name.

Hope it can help!
Namastè! :)

---

