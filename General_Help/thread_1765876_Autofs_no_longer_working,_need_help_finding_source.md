---
title: "Autofs no longer working, need help finding source of problem and fix."
date: 2011-05-23
forum: General Help
---

### Post by shoryuken on 2011-05-23
Hi folks, 

After several days of searching, reading and re-installing, I'm at a complete loss as to why autofs has suddenly stopped working. 
Basically, I can see the shared folders on the host computer but as soon as I try to cd into the folders I get "-bash: cd: [directory]: No such file or directory" (where [directory] = shared drive.

The setup used to work and the exact same setup on another computer computer works flawlessly. 

I'm running Ubuntu 11.04

Here is the content of auto.cifs:
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
mountopts="-fstype=cifs,file_mode=0644,dir_mode=0755,uid=shoryuken,gid=users,iocharset=utf8"
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

Here is the content of auto.master
```

+auto.master
/home/shoryuken/TerraDrive	/etc/auto.cifs  --timeout=600

```


and credentials are stored in /etc/auto.smb.goblin (where goblin = name of windows computer sharing folders.


When I do "ls -l /home/shoryuken/TerraDrive/goblin" I get:
```

ls: /home/shoryuken/TerraDrive/goblin/print$: No such file or directory
ls: /home/shoryuken/TerraDrive/goblin/Z$: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/TerraDrive: No such file or directory
ls: /home/shoryuken/TerraDrive/goblin/Shared Documents: No such file or directory
ls: /home/shoryuken/TerraDrive/goblin/Music: No such file or directory
ls: /home/shoryuken/TerraDrive/goblin/MediaMall: No such file or directory
ls: /home/shoryuken/TerraDrive/goblin/Linksys_Logs: No such file or directory
ls: /home/shoryuken/TerraDrive/goblin/I$: No such file or directory
ls: /home/shoryuken/TerraDrive/goblin/H$: No such file or directory
ls: /home/shoryuken/TerraDrive/goblin/GW_Share: No such file or directory
ls: /home/shoryuken/TerraDrive/goblin/G$: No such file or directory
ls: /home/shoryuken/TerraDrive/goblin/G: No such file or directory
ls: /home/shoryuken/TerraDrive/goblin/F$: No such file or directory
ls: /home/shoryuken/TerraDrive/goblin/E$: No such file or directory
ls: /home/shoryuken/TerraDrive/goblin/D-Drive: No such file or directory
ls: /home/shoryuken/TerraDrive/goblin/D$: No such file or directory
ls: /home/shoryuken/TerraDrive/goblin/C$: No such file or directory
ls: /home/shoryuken/TerraDrive/goblin/ADMIN$: No such file or directory
total 0
drwxr-xr-x 2 root root 0 2011-05-23 14:01 ADMIN$
drwxr-xr-x 2 root root 0 2011-05-23 14:01 C$
drwxr-xr-x 2 root root 0 2011-05-23 14:01 D$
drwxr-xr-x 2 root root 0 2011-05-23 14:01 D-Drive
drwxr-xr-x 2 root root 0 2011-05-23 14:01 E$
drwxr-xr-x 2 root root 0 2011-05-23 14:01 F$
drwxr-xr-x 2 root root 0 2011-05-23 14:01 G
drwxr-xr-x 2 root root 0 2011-05-23 14:01 G$
drwxr-xr-x 2 root root 0 2011-05-23 14:01 GW_Share
drwxr-xr-x 2 root root 0 2011-05-23 14:01 H$
drwxr-xr-x 2 root root 0 2011-05-23 14:01 I$
drwxr-xr-x 2 root root 0 2011-05-23 14:01 Linksys_Logs
drwxr-xr-x 2 root root 0 2011-05-23 14:01 MediaMall
drwxr-xr-x 2 root root 0 2011-05-23 14:01 Music
drwxr-xr-x 2 root root 0 2011-05-23 14:01 print$
drwxr-xr-x 2 root root 0 2011-05-23 14:01 Shared Documents
d????????? ? ?    ?    ?                ? TerraDrive
drwxr-xr-x 2 root root 0 2011-05-23 14:01 Z$

```

Now if I try to "cd" into any of the shared drives (like D-Drive, GW_Share or TerraDrive) I get the following:
```

-bash: cd: D-Drive: No such file or directory

```

A second or subsequent attempt at "ls -l" results in:
```

ls: cannot access /home/shoryuken/TerraDrive/goblin/Linksys_Logs: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/I$: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/H$: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/GW_Share: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/G$: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/G: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/F$: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/E$: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/D-Drive: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/D$: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/C$: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/ADMIN$: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/print$: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/Z$: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/TerraDrive: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/Shared Documents: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/Music: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/MediaMall: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/Linksys_Logs: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/I$: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/H$: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/GW_Share: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/G$: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/G: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/F$: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/E$: No such file or directory
ls: cannot access /home/shoryuken/TerraDrive/goblin/D-Drive: No such file or directory
total 0
d????????? ? ? ? ?                ? ADMIN$
d????????? ? ? ? ?                ? C$
d????????? ? ? ? ?                ? D$
d????????? ? ? ? ?                ? D-Drive
d????????? ? ? ? ?                ? D-Drive
d????????? ? ? ? ?                ? E$
d????????? ? ? ? ?                ? E$
d????????? ? ? ? ?                ? F$
d????????? ? ? ? ?                ? F$
d????????? ? ? ? ?                ? G
d????????? ? ? ? ?                ? G
d????????? ? ? ? ?                ? G$
d????????? ? ? ? ?                ? G$
d????????? ? ? ? ?                ? GW_Share
d????????? ? ? ? ?                ? GW_Share
d????????? ? ? ? ?                ? H$
d????????? ? ? ? ?                ? H$
d????????? ? ? ? ?                ? I$
d????????? ? ? ? ?                ? I$
d????????? ? ? ? ?                ? Linksys_Logs
d????????? ? ? ? ?                ? Linksys_Logs
d????????? ? ? ? ?                ? MediaMall
d????????? ? ? ? ?                ? Music
d????????? ? ? ? ?                ? print$
d????????? ? ? ? ?                ? Shared Documents
d????????? ? ? ? ?                ? TerraDrive
d????????? ? ? ? ?                ? Z$

```

Note the question marks that are now everywhere.

I'm not sure where to look to find out why this is failing. The shared drive are visible, but then disappear when I try to access them. The same exact setup, on another machine works perfectly fine. :confused:

I'd appreciate any lead to trying to figure out the source of the problem.

TIA

Shoryuken

---

### Post by kalyp on 2011-06-10
I'm having the same problem. Did you figure out the solution? Thanks in advance!!

---

### Post by shoryuken on 2011-06-10
> **kalyp said:**
> I'm having the same problem. Did you figure out the solution? Thanks in advance!!

No solution yet. At this point my plan is to re-install OS.

---

### Post by kalyp on 2011-06-10
I have it working better. Mounting it as root but at least I can see and browse and the question marks don't appear anymore. I think what fixed it is the part about/etc/nsswitch.conf and winbind in [this thread]("http://ubuntuforums.org/showthread.php?t=288534") (pre-work). I tried other things in between so that I'm not 100% sure but I think that's it...

To avoid the root thing, I mount it directly in autofs as 
```
mnt_point	-fstype=smbfs,gid=mygid,uid=mygid,nounix,noserverino	://server/share
```
(that comes from the same tutorial).

---

### Post by shoryuken on 2011-06-12
So I figured out what the problem was. It looks like during an upgrade, the system added something to the auto.master file:
> 
+auto.master


Once I commented that out, everything seems to be back to normal. I knew it had to be something simple ;)

Cheers

---

