---
title: "rsync not maintaining file ownership"
date: 2011-05-16
forum: General Help
---

### Post by georgebrough on 2011-05-16
I have an Ubuntu machine running NFS4 server and a plugapps (arch linux) machine connecting as the client.  The plugbox is running an rsync job to backup the home directory from Ubuntu to a local USB HDD.  

All of the files in the destination have owner nobody and group nobody.  

Ubuntu /etc/exports:

```
/home 192.168.2.1/24(rw,sync,no_subtree_check,no_root_squash)
```plugbox /etc/fstab

```
192.168.2.2:/home       /mnt/daisy      nfs4    defaults        0       0
```plugbox backup command

```
rsync -av --progress --delete --log-file=/rsync.log /mnt/daisy/george /home
```also on the plugbox I have edited /etc/rsyncd.conf to have 

```

uid = root
gid = root
```

Can any one suggest how I can mantain the file owners.  I have the UID's and passwords sync'd between the two machines for both root and the user who's home dir is being backed up.

Thanks

George

---

### Post by collisionystm on 2011-05-16
excerpt from rsync --help

```
c:~$ rsync --help
rsync  version 3.0.7  protocol version 30
Copyright (C) 1996-2009 by Andrew Tridgell, Wayne Davison, and others.
Web site: [http://rsync.samba.org/](http://rsync.samba.org/)
Capabilities:
    64-bit files, 64-bit inums, 64-bit timestamps, 64-bit long ints,
    socketpairs, hardlinks, symlinks, IPv6, batchfiles, inplace,
    append, ACLs, xattrs, iconv, symtimes

rsync comes with ABSOLUTELY NO WARRANTY.  This is free software, and you
are welcome to redistribute it under certain conditions.  See the GNU
General Public Licence for details.

rsync is a file transfer program capable of efficient remote update
via a fast differencing algorithm.

Usage: rsync [OPTION]... SRC [SRC]... DEST
  or   rsync [OPTION]... SRC [SRC]... [USER@]HOST:DEST
  or   rsync [OPTION]... SRC [SRC]... [USER@]HOST::DEST
  or   rsync [OPTION]... SRC [SRC]... rsync://[USER@]HOST[:PORT]/DEST
  or   rsync [OPTION]... [USER@]HOST:SRC [DEST]
  or   rsync [OPTION]... [USER@]HOST::SRC [DEST]
  or   rsync [OPTION]... rsync://[USER@]HOST[:PORT]/SRC [DEST]
The ':' usages connect via remote shell, while '::' & 'rsync://' usages connect
to an rsync daemon, and require SRC or DEST to start with a module name.

Options
 -v, --verbose               increase verbosity
 -q, --quiet                 suppress non-error messages
     --no-motd               suppress daemon-mode MOTD (see manpage caveat)
 -c, --checksum              skip based on checksum, not mod-time & size
 -a, --archive               archive mode; equals -rlptgoD (no -H,-A,-X)
     --no-OPTION             turn off an implied OPTION (e.g. --no-D)
 -r, --recursive             recurse into directories
 -R, --relative              use relative path names
     --no-implied-dirs       don't send implied dirs with --relative
 -b, --backup                make backups (see --suffix & --backup-dir)
     --backup-dir=DIR        make backups into hierarchy based in DIR
     --suffix=SUFFIX         set backup suffix (default ~ w/o --backup-dir)
 -u, --update                skip files that are newer on the receiver
     --inplace               update destination files in-place (SEE MAN PAGE)
     --append                append data onto shorter files
     --append-verify         like --append, but with old data in file checksum
 -d, --dirs                  transfer directories without recursing
 -l, --links                 copy symlinks as symlinks
 -L, --copy-links            transform symlink into referent file/dir
     --copy-unsafe-links     only "unsafe" symlinks are transformed
     --safe-links            ignore symlinks that point outside the source tree
 -k, --copy-dirlinks         transform symlink to a dir into referent dir
 -K, --keep-dirlinks         treat symlinked dir on receiver as dir
 -H, --hard-links            preserve hard links
 -p, --perms                 preserve permissions
 -E, --executability         preserve the file's executability
     --chmod=CHMOD           affect file and/or directory permissions
 -A, --acls                  preserve ACLs (implies --perms)
 -X, --xattrs                preserve extended attributes
 -o, --owner                 preserve owner (super-user only)
 -g, --group                 preserve group
     --devices               preserve device files (super-user only)
     --specials              preserve special files
 -D                          same as --devices --specials
 -t, --times                 preserve modification times
 -O, --omit-dir-times        omit directories from --times
     --super                 receiver attempts super-user activities
     --fake-super            store/recover privileged attrs using xattrs
 -S, --sparse                handle sparse files efficiently
 -n, --dry-run               perform a trial run with no changes made
 -W, --whole-file            copy files whole (without delta-xfer algorithm)
 -x, --one-file-system       don't cross filesystem boundaries
 -B, --block-size=SIZE       force a fixed checksum block-size
 -e, --rsh=COMMAND           specify the remote shell to use
     --rsync-path=PROGRAM    specify the rsync to run on the remote machine
     --existing              skip creating new files on receiver
     --ignore-existing       skip updating files that already exist on receiver
     --remove-source-files   sender removes synchronized files (non-dirs)
     --del                   an alias for --delete-during
     --delete                delete extraneous files from destination dirs
     --delete-before         receiver deletes before transfer, not during
     --delete-during         receiver deletes during transfer (default)
     --delete-delay          find deletions during, delete after
     --delete-after          receiver deletes after transfer, not during
     --delete-excluded       also delete excluded files from destination dirs
     --ignore-errors         delete even if there are I/O errors
     --force                 force deletion of directories even if not empty
     --max-delete=NUM        don't delete more than NUM files
     --max-size=SIZE         don't transfer any file larger than SIZE
     --min-size=SIZE         don't transfer any file smaller than SIZE
     --partial               keep partially transferred files
     --partial-dir=DIR       put a partially transferred file into DIR
     --delay-updates         put all updated files into place at transfer's end
 -m, --prune-empty-dirs      prune empty directory chains from the file-list
     --numeric-ids           don't map uid/gid values by user/group name
     --timeout=SECONDS       set I/O timeout in seconds
     --contimeout=SECONDS    set daemon connection timeout in seconds
 -I, --ignore-times          don't skip files that match in size and mod-time
     --size-only             skip files that match in size
     --modify-window=NUM     compare mod-times with reduced accuracy
 -T, --temp-dir=DIR          create temporary files in directory DIR
 -y, --fuzzy                 find similar file for basis if no dest file
     --compare-dest=DIR      also compare destination files relative to DIR
     --copy-dest=DIR         ... and include copies of unchanged files
     --link-dest=DIR         hardlink to files in DIR when unchanged
 -z, --compress              compress file data during the transfer
     --compress-level=NUM    explicitly set compression level
     --skip-compress=LIST    skip compressing files with a suffix in LIST
 -C, --cvs-exclude           auto-ignore files the same way CVS does
 -f, --filter=RULE           add a file-filtering RULE
 -F                          same as --filter='dir-merge /.rsync-filter'
                             repeated: --filter='- .rsync-filter'
     --exclude=PATTERN       exclude files matching PATTERN
     --exclude-from=FILE     read exclude patterns from FILE
     --include=PATTERN       don't exclude files matching PATTERN
     --include-from=FILE     read include patterns from FILE
     --files-from=FILE       read list of source-file names from FILE
 -0, --from0                 all *-from/filter files are delimited by 0s
 -s, --protect-args          no space-splitting; only wildcard special-chars
     --address=ADDRESS       bind address for outgoing socket to daemon
     --port=PORT             specify double-colon alternate port number
     --sockopts=OPTIONS      specify custom TCP options
     --blocking-io           use blocking I/O for the remote shell
     --stats                 give some file-transfer stats
 -8, --8-bit-output          leave high-bit chars unescaped in output
 -h, --human-readable        output numbers in a human-readable format
     --progress              show progress during transfer
 -P                          same as --partial --progress
 -i, --itemize-changes       output a change-summary for all updates
     --out-format=FORMAT     output updates using the specified FORMAT
     --log-file=FILE         log what we're doing to the specified FILE
     --log-file-format=FMT   log updates using the specified FMT
     --password-file=FILE    read daemon-access password from FILE
     --list-only             list the files instead of copying them
     --bwlimit=KBPS          limit I/O bandwidth; KBytes per second
     --write-batch=FILE      write a batched update to FILE
     --only-write-batch=FILE like --write-batch but w/o updating destination
     --read-batch=FILE       read a batched update from FILE
     --protocol=NUM          force an older protocol version to be used
     --iconv=CONVERT_SPEC    request charset conversion of filenames
 -4, --ipv4                  prefer IPv4
 -6, --ipv6                  prefer IPv6
     --version               print version number
(-h) --help                  show this help (-h works with no other options)

Use "rsync --daemon --help" to see the daemon-mode command-line options.
Please see the rsync(1) and rsyncd.conf(5) man pages for full documentation.
See [http://rsync.samba.org/](http://rsync.samba.org/) for updates, bug reports, and answers
:~$ 


```Look at the ones pertaining to permissions.



```

-H, --hard-links            preserve hard links
 -p, --perms                 preserve permissions
 -E, --executability         preserve the file's executability
     --chmod=CHMOD           affect file and/or directory permissions
 -A, --acls                  preserve ACLs (implies --perms)
 -X, --xattrs                preserve extended attributes
 -o, --owner                 preserve owner (super-user only)
 -g, --group                 preserve group
     --devices               preserve device files (super-user only)
     --specials              preserve special files

```

---

### Post by georgebrough on 2011-05-16
Hi,

I selected archive mode which should preserve owner, group,  permissions.  Just comparing archive against the ones you highlighted,  the ones it doesn't include are H, A, X, E, I have just added those to  the command and the owner is still nobody.

---

### Post by georgebrough on 2011-05-17
Anyone have any suggestions how I can get around this?

---

### Post by SeijiSensei on 2011-05-17
What happens if you run the rsync job in the other direction -- from the Ubuntu server to the plugbox?

The uid/gid settings in rsyncd.conf only apply if you're running rsync in "daemon" mode.  I'd guess the plugbox is running the rsync job as the nobody user.  Can you add users to the plugbox?  Can you get it to run the rsync job as root?

---

### Post by georgebrough on 2011-05-18
If I run in the other direction the files end up with the owner who run's the rsync, i.e. me if I run 

```
rsync -a [source] [dest]
```and root if i run 

```
sudo rsync -a [source] [dest]
```I don't understand what you mean when you say "deamon" mode?

I have run the rsync on the plugbox both in a cron job as root and manually as root.  Always results in the owner and group being nobody.


I have now noticed that when I browse the ubuntu machine from the plugbox "ls -l" shows the uid and gid's as nobody.  Therefore I now assume that the problem is the NFS mount rather than rsync.  I removed the "no_squash_root" option from the NFS server, and I could no longer access the files owned by me while logged in as root, if I log in to the plugbox as me I can access my files so the server seems to be checking the permissions correctly.  However when logged in as me "ls -l" still shows the uid and gid as nobody.

I'm really struggling to understand what I've done wrong!

---

### Post by collisionystm on 2011-05-18
> **georgebrough said:**
> Hi,

I selected archive mode which should preserve owner, group,  permissions.  Just comparing archive against the ones you highlighted,  the ones it doesn't include are H, A, X, E, I have just added those to  the command and the owner is still nobody.

It is not showing an actual owner name because the owner does not exist on the other system. It should give a set of numbers for the owner, group, etc...


Look at your /etc/passwd file and you will see the number for your username match to the number on the file, on the backup server.

---

### Post by georgebrough on 2011-05-18
The users are sync'd between the two machines with the same username, same UID and same password.  As is the users primary group.  It's not that it's showing the ID (I know what you mean about this but in this case it is not what is happening), it's actually showing that the owner of the group is the user named nobody.  The nobody user exists on both machines but with differed UID's

---

### Post by collisionystm on 2011-05-18
> **georgebrough said:**
> The users are sync'd between the two machines with the same username, same UID and same password.  As is the users primary group.  It's not that it's showing the ID (I know what you mean about this but in this case it is not what is happening), it's actually showing that the owner of the group is the user named nobody.  The nobody user exists on both machines but with differed UID's

Try

rsync -rqaHpEAXogt


thats what I use to make sure I get everything.

---

### Post by georgebrough on 2011-05-18
I've tried your suggestion but I get the same results.  I think the problem is the mount not the rsync command.

---

### Post by georgebrough on 2011-05-19
Anyone have any other ideas on this one??

---

### Post by SeijiSensei on 2011-05-20
> **georgebrough said:**
> I don't understand what you mean when you say "deamon" mode?

Run "man rsyncd.conf" for details.  Running rsync as a daemon might actually solve the permissions problem for you if you set things up right.

---

### Post by Irihapeti on 2011-05-20
What is the destination drive formatted as? If it is FAT32 (or FAT16) then that could be causing problems.

---

