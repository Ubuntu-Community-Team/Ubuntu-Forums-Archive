---
title: "Network shares are missing when I try to use autofs and CIFS shares"
date: 2010-08-23
forum: General Help
---

### Post by b0z02003 on 2010-08-23
I tried to configure autofs so it could "automount" my samba shares, but I have a problem. The server is successfully detected (some shares are accessible), but some are missing.

Here is my /etc/auto.master
```
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#
#/misc	/etc/auto.misc
#
# NOTE: mounts done from a hosts map will be mounted with the
#	"nosuid" and "nodev" options unless the "suid" and "dev"
#	options are explicitly given.
#
#/net	-hosts
#
# Include central master map if it can be found using
# nsswitch sources.
#
# Note that if there are entries for /net or /misc (as
# above) in the included master map any keys that are the
# same will not be seen as the first read key seen takes
# precedence.
#
+auto.master

/mnt/cifs /etc/auto.cifs --timeout=60

```

My /etc/auto.cifs
```
#!/bin/bash
# $Id$
# This file must be executable to work! chmod 755!
key="$1"
# Note: create a cred file for each windows/Samba-Server in your network
#       which requires password authentification.  The file should contain
#       exactly two lines:
#          username=user
#          password=*****
#       Please don't use blank spaces to separate the equal sign from the
#       user account name or password.
credfile="/etc/auto.smb.$key"
# Note: Use cifs instead of smbfs:
mountopts="-fstype=cifs,uid=xbmc,gid=xbmc"
smbclientopts=""
for P in /bin /sbin /usr/bin /usr/sbin
do
        if [ -x $P/smbclient ]
        then
                SMBCLIENT=$P/smbclient
                break
        fi
done
[ -x $SMBCLIENT ] || exit 1
if [ -e "$credfile" ]
then
        mountopts=$mountopts",credentials=$credfile"
        smbclientopts="-A "$credfile
else
        smbclientopts="-N"
fi
$SMBCLIENT $smbclientopts -gL $key 2>/dev/null \
   | awk -v key="$key" -v opts="$mountopts" -F'|' -- '
        BEGIN   { ORS=""; first=1 }
	/Disk/  { if (first) { print opts; first=0 };
		  gsub(/ /, "\\ ", $2);
		  sub(/\$/, "\\$", $2);
		  print " \\\n\t /" $2, "://" key "/" $2 }
        END     { if (!first) print "\n"; else exit 1 }
        '

```

The result of a "smbclient -L B0Z0PC"

```
Domain=[B0Z0PC] OS=[Windows 7 Professional 7600] Server=[Windows 7 Professional 6.1]

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Administration Ã* distance
        Albums          Disk
        C$              Disk      Partage par dÃ©faut
        D$              Disk      Partage par dÃ©faut
        E$              Disk      Partage par dÃ©faut
        I$              Disk      Partage par dÃ©faut
        IPC$            IPC       IPC distant
        Mangas          Disk
        Movies          Disk
        print$          Disk      Pilotes dâimprimantes
        TV              Disk
        Users           Disk
Domain=[B0Z0PC] OS=[Windows 7 Professional 7600] Server=[Windows 7 Professional 6.1]

        Server               Comment
        ---------            -------

        Workgroup            Master
        ---------            -------

```

And the content of the directory that should contains the shares:

```

root@b0z0-MediaCenter:/mnt/cifs/B0Z0PC# ls
ADMIN$  C$  Mangas  Movies  print$  Users

```

As you can see, some shares, such as "Albums" and "TV" are missing. I really hope that someone has knowledge on this issue. Thank you and please excuse me for my bad english !

---

