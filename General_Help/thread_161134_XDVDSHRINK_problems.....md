---
title: "XDVDSHRINK problems...."
date: 2006-04-16
forum: General Help
---

### Post by MJSOnline on 2006-04-16
Hi all.  I am trying to install XDVDSHRINK from source.  I have unpacked it into a folder but cant get any further...  I get the message below.  What am I missing? What do I do to install this package so I can burn my VOB files?
[B]```
Try `install --help' for more information.
matthew@server:/media/SD/DLoads/dvdshrink$ install - help
install: cannot stat `-': No such file or directory
matthew@server:/media/SD/DLoads/dvdshrink$ install --help
Usage: install [OPTION]... SOURCE DEST           (1st format)
  or:  install [OPTION]... SOURCE... DIRECTORY   (2nd format)
  or:  install -d [OPTION]... DIRECTORY...       (3rd format)
In the first two formats, copy SOURCE to DEST or multiple SOURCE(s) to
the existing DIRECTORY, while setting permission modes and owner/group.
In the third format, create all components of the given DIRECTORY(ies).

Mandatory arguments to long options are mandatory for short options too.
      --backup[=CONTROL] make a backup of each existing destination file
  -b                  like --backup but does not accept an argument
  -c                  (ignored)
  -d, --directory     treat all arguments as directory names; create all
                        components of the specified directories
  -D                  create all leading components of DEST except the last,
                        then copy SOURCE to DEST;  useful in the 1st format
  -g, --group=GROUP   set group ownership, instead of process' current group
  -m, --mode=MODE     set permission mode (as in chmod), instead of rwxr-xr-x
  -o, --owner=OWNER   set ownership (super-user only)
  -p, --preserve-timestamps   apply access/modification times of SOURCE files
                        to corresponding destination files
  -s, --strip         strip symbol tables, only for 1st and 2nd formats
  -S, --suffix=SUFFIX override the usual backup suffix
  -v, --verbose       print the name of each directory as it is created
      --help     display this help and exit
      --version  output version information and exit

The backup suffix is `~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control method may be selected via the --backup option or through
the VERSION_CONTROL environment variable.  Here are the values:

  none, off       never make backups (even if --backup is given)
  numbered, t     make numbered backups
  existing, nil   numbered if numbered backups exist, simple otherwise
  simple, never   always make simple backups

Report bugs to <bug-coreutils@gnu.org>.
matthew@server:/media/SD/DLoads/dvdshrink$
```[/B]
Thanks. M

---

### Post by marcos89 on 2006-04-16
Install k9copy from add/remove

---

### Post by MJSOnline on 2006-04-16
[QUOTE=marcos89]Install k9copy from add/remove[/QUOTE]
How and why?

---

### Post by 8bit on 2006-04-16
I've read that xdvdshrink is no longer supported. Don't quote me on that. 

I installed k9copy and it shrinks the dvd's down to dvd5 but when I burn them and try to play   them in totem, it doesn't recognize the format. If I try to play them in my Sony DVD player, it plays but freezes every few seconds and is unwatchable. I'm using good media BTW.

I can't get wine to work after upgrading to dapper. DVDShrink in wine works great! 

Can anyone explain why k9copy is not working? My DVD drive is only a month old and burns everything else just fine.

---

### Post by MJSOnline on 2006-04-16
Anyone? M

---

### Post by elamericano on 2006-04-16
Is there a Gnome equivalent to K9copy?

---

