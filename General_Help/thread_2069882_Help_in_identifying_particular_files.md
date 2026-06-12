---
title: "Help in identifying particular files"
date: 2012-10-11
forum: General Help
---

### Post by ahougie on 2012-10-11
Here's the problem.  I have had some file corruption on one of the drives on my server.  I have a (partial) duplicate drive but it is on an NTFS-formatted external drive. I need to identify which files need restoring. I believe "rsync -nuI" might normally be able to do this but (possibly because the external drive is NTFS-formatted) it generates a list of every file and not just the ones that differ.

I think I know the underlying logic of the script I need but not how to implement it.  I think the logic is:


[LIST]
[*]for each directory and subdirectory in /path/on/backup/drive [e.g. /mnt/extdrive/backup/dir1/dir2/]
[/LIST]
 
[LIST]
[*]for each file in /path/on/backup/drive
[LIST]
[*]is there a file with the same name in /similar/path/on/server (e.g. /mnt/intdrive/server/dir1/dir2/
[*]if so, is the file on the server newer than the one on the backup drive
[LIST]
[*]if yes, ignore and go to next file
[*]if not, 'diff -q                 /path/on/backup/drive/file /similar/path/on/server/file >> logfile'
[*]proceed to next file
[/LIST]
 
[*]if there is not a file with the same name in /similar/path/on/server proceed to next file
[*]proceed to next directory and subdirectory in /path/on/backup/drive
[/LIST]
 
[/LIST]
It has been suggested to me that "diff -q" for binary files isn't sensible and md5sum or cmp would be better or more reliable, although it then becomes another task to create the logfile entry.

"diff -q" only generates a message if the files differ and it then generates a message listing both files and paths making it simple to restore the relevant files manually.


Can anyone help?


Many thanks

---

### Post by ahougie on 2012-10-11
How about this?

#!/bin/bash
extpath=/mnt/path/on/backup/drive/
serverpath=/mnt/similar/path/on/server/
logfile=/path/to/photo-diff-log
cd $extpath
dirs=`find -type d`
    for d in "$dirs"
        # test whether directory exists on server path
        if [ -d "$serverpath$d" ] ; then
            # create file list in directory
            cd "$extpath$d"
            files=`ls`
            for f in "$files"
                # test whether file exists on server
                if [ -e "$serverpath$d$/file" ] ; then 
                    # test whether file on server is newer
                    if [! "$serverpath$d/$file" -nt "$extpath$d/$file" ]
                    diff -q "$extpath$d/$file" "$serverpath$d/$file" >> $logfile
                    fi
                fi
            done
        fi
    done
exit

---

