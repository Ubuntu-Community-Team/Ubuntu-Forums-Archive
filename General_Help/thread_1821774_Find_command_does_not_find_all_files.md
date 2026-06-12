---
title: "Find command does not find all files"
date: 2011-08-09
forum: General Help
---

### Post by ketchemr on 2011-08-09
The find command does not seem to find all files in my directory hierarchy. My home directory is automounted from a server. The command to illustrate this is:
find | sed -e 's/^\.\///' | sed -e 's/\/.*//' | sort -u
The result misses several directories. Likewise, a find of a particular file, like:
find . -iname \*sample\* -print
where sample_file.txt resides in one of the directories that is missing in the first find command, finds nothing. Any ideas?

---

### Post by papibe on 2011-08-09
Interesting, could you post the full path of that file?
Is there any link (symbolic or hard) on the path?
Is the filesystem ext4 or NTFS?

Regards.

BTW, I would call 'find' like this:
```
$ find -iname '*sample*'
```

---

### Post by ketchemr on 2011-08-10
Find does not find half of my directories, so a great many files with a great many paths would have to be listed. But a sample would be /home/ketchemr/stuff/sample.txt.
None of the missing directories or files are symbolic links.
The file system is ext4, but my home is automounted on a server.

I tried a test in a colleague's home directory that has his files local on a redhat machine, but I was in his home via Ubuntu automounting. find could see all of his files. Is there something special I need to have in nsswitch.conf or auto.master?

---

### Post by ketchemr on 2011-08-11
I should add that the remote file system is on a NetApp device.

---

### Post by ketchemr on 2011-08-18
I copied the "find" program from a Redhat Enterprise machine and tried it on my Ubuntu installation with my home directory on NetApp. It worked fine and found all files. There seems to be a bug in the Ubuntu find.

---

