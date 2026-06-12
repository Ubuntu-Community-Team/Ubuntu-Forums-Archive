---
title: "Mount network ntfs share"
date: 2011-07-27
forum: General Help
---

### Post by swift100 on 2011-07-27
hi,

would anyone advise on how to properly mount a samba share using a script which i'd run whenever i wanted to map it? I was trying to write one but with no joy...I tried having read many pages about mount / smbmount / mount.cisf / fstab etc. but I didn't achieve what I need and now I'm totally cofused...:frown: 

My goal is to have a script file, like a Win .bat, which i would use as myself to map a share to a directory. I would like to be able to mount it as non-root and umount as non-root as well. The level of access should be rw so i could copy and delete files.

Would you please advise which command to use best as from what i've learnt one is more suitible that another, one is outdated and so on...?

 many thanks!

---

### Post by Azdour on 2011-07-27
Hi,

I would probably recommend you mounting the samba share via fstab, there is a guide here:

[http://ubuntuforums.org/showthread.php?t=1658828](http://ubuntuforums.org/showthread.php?t=1658828)

I am pretty sure that you cannot mount/unmount without sudo, unless anyone else can tell me otherwise :)

Update: you may want to look at:

[http://ubuntuforums.org/showthread.php?t=878387](http://ubuntuforums.org/showthread.php?t=878387)

---

### Post by Wayne_V on 2011-07-27
you can also use autofs:

sudo apt-get install autofs smbfs smbclient

sudo vi /etc/auto.master and add "/smb /etc/auto.smb --timeout=600"

sudo vi /etc/auto.smb.<your smb servername> and add
username=yourusername
password=yourpassword

then 'sudo chmod 600 /etc/auto.smb.<your smb servername>'

then, modify /etc/auto.smb to use the credentials file.  This should be your new /etc/auto.smb:

> #!/bin/bash
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
mountopts="-fstype=cifs,file_mode=0644,dir_mode=0755,uid=1000,gid=1000"
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



start everything with "sudo /etc/init.d/autofs restart"

and now you should be able to "ls /smb/<servername>/<sharename>"

see here for more details:  [http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs](http://www.howtoforge.com/accessing_windows_or_samba_shares_using_autofs)

---

