---
title: "Reading rsync log files"
date: 2009-11-30
forum: General Help
---

### Post by dunkar70 on 2009-11-30
I have been trying to find an explanation for reading the output of the rsync log files. The content I have been able to find is limited to explaining how to create the log, not how to read it. 

I would like to query the log files and prepare a summary report of the changes. If anyone has an existing link or an explanation, please provide it. 

For example, the output contains lines similar to:
```
2009/11/30 13:01:22 [29673] >f..T...... Path/To/File.txt
```

I suspect the ">f" means the item is a file while "cd" appears to represent a directory. What do the remaining items mean?

Thanks.

---

### Post by StuartN on 2009-11-30
> **dunkar70 said:**
> I suspect the ">f" means the item is a file while "cd" appears to represent a directory.

Yes, in column 2 an f is file, d is directory. In column 1 a c is change and > is copied to destination.

Take a look at the -i, --itemize-changes option in **man rsync** for the full description.

---

### Post by dunkar70 on 2009-11-30
@StuartN

Thanks for your reply. I have checked the man page. It describes how to set the format, but not which options are available or how to interpret the standard format. I have found a couple of messages that discuss options like %h and %a, but they are usually posted as issues. They do not explain what each option means or include a complete list of options.

        ```
-i, --itemize-changes       output a change-summary for all updates
            --out-format=FORMAT     output updates using the specified FORMAT
            --log-file=FILE         log what we’re doing to the specified FILE
            --log-file-format=FMT   log updates using the specified FMT
            --password-file=FILE    read password from FILE
            --list-only             list the files instead of copying them
            --bwlimit=KBPS          limit I/O bandwidth; KBytes per second
            --write-batch=FILE      write a batched update to FILE
            --only-write-batch=FILE like --write-batch but w/o updating dest
            --read-batch=FILE       read a batched update from FILE
            --protocol=NUM          force an older protocol version to be used
            --checksum-seed=NUM     set block/file checksum seed (advanced)
```

---

### Post by StuartN on 2009-11-30
> **dunkar70 said:**
> It describes how to set the format, but not which options are available or how to interpret the standard format.

My man page looks very much like this (around line 1987-), where YXcstpoguax both sets and describes the output, namely X is modified according to operation Y, specifically (c)hecksum differs, (s)ize differs, updated (t)ime, (p)ermission, (o)wner, (g)roup, (u)nused, (a)cls, e(x)tended attribute:

```
 -i, --itemize-changes
              Requests a simple itemized list of the changes  that  are  being
              made to each file, including attribute changes.  This is exactly
              the same as specifying --out-format='%i %n%L'.   If  you  repeat
              the option, unchanged files will also be output, but only if the
              receiving rsync is at least version 2.6.7 (you can use -vv  with
              older  versions  of  rsync, but that also turns on the output of
              other verbose messages).

              The "%i" escape has a cryptic output that is  11  letters  long.
              The  general  format  is like the string YXcstpoguax, where Y is
              replaced by the type of update being done, X is replaced by  the
              file-type,  and  the other letters represent attributes that may
              be output if they are being modified.

              The update types that replace the Y are as follows:


              o      A < means that a file is being transferred to the  remote
                     host (sent).

              o      A  >  means that a file is being transferred to the local
                     host (received).

              o      A c means that a local change/creation is  occurring  for
                     the  item  (such  as  the  creation of a directory or the
                     changing of a symlink, etc.).

              o      A h means that the item is a hard link  to  another  item
                     (requires --hard-links).

              o      A  .  means that the item is not being updated (though it
                     might have attributes that are being modified).

              o      A * means that the rest of the itemized-output area  con-
                     tains a message (e.g. "deleting").


              The  file-types  that replace the X are: f for a file, a d for a
              directory, an L for a symlink, a D for a device, and a S  for  a
              special file (e.g. named sockets and fifos).

              The  other  letters  in  the string above are the actual letters
              that will be output if the associated attribute for the item  is
              being  updated or a "." for no change.  Three exceptions to this
              are: (1) a newly created item replaces each letter with  a  "+",
              (2)  an identical item replaces the dots with spaces, and (3) an
              unknown attribute replaces each letter with a "?" (this can hap-
              pen when talking to an older rsync).

              The attribute that is associated with each letter is as follows:


              o      A c means either that a  regular  file  has  a  different
                     checksum (requires --checksum) or that a symlink, device,
                     or special file has a changed value.  Note  that  if  you
                     are sending files to an rsync prior to 3.0.1, this change
                     flag will be present only for checksum-differing  regular
                     files.

              o      A  s  means  the  size of a regular file is different and
                     will be updated by the file transfer.

              o      A t means the modification time is different and is being
                     updated  to  the  sender's  value (requires --times).  An
                     alternate value of T means  that  the  modification  time
                     will  be  set  to the transfer time, which happens when a
                     file/symlink/device is updated without --times and when a
                     symlink  is  changed and the receiver can't set its time.
                     (Note: when using an rsync 3.0.0 client,  you  might  see
                     the  s  flag combined with t instead of the proper T flag
                     for this time-setting failure.)

              o      A p means the permissions are  different  and  are  being
                     updated to the sender's value (requires --perms).

              o      An o means the owner is different and is being updated to
                     the sender's value (requires --owner and super-user priv-
                     ileges).

              o      A  g means the group is different and is being updated to
                     the sender's value (requires --group and the authority to
                     set the group).

              o      The u slot is reserved for future use.

              o      The a means that the ACL information changed.

              o      The  x  means  that  the  extended  attribute information
                     changed.


              One other output is possible:  when  deleting  files,  the  "%i"
              will  output  the string "*deleting" for each item that is being
              removed (assuming that you are talking to a recent enough  rsync
              that  it  logs deletions instead of outputting them as a verbose
              message).



```

(online version from [http://www.manpagez.com/man/1/rsync/](http://www.manpagez.com/man/1/rsync/))

---

### Post by dunkar70 on 2009-11-30
Thanks StuartN! I either missed it or didn't recognize it when I skimmed over it.

---

### Post by lucidsystems on 2010-01-26
You may also be interested in LBackup : [http://www.lbackup.org](http://www.lbackup.org)

LBackup has support for logging changes for each backup into a change log file.

---

