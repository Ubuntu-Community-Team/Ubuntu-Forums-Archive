---
title: "Automatically copying a file to a Windows Server"
date: 2009-07-01
forum: General Help
---

### Post by Lotekk on 2009-07-01
Hello all, been looking for a solution to this and haven't found anything really helpful yet, my apologies if it has been discussed already and I missed it...

I've got a shell script to create a backup file of my wiki's files and database (via mysqldump). It places a nice neat ZIP in a directory thanks to cron, every day.

What I'm looking to do now is have the new file copied to a share on a Windows Server on the local network. I just don't know the syntax or how to go about doing this, whether it be adding more to the shell script or even a new cron job.  Can anyone offer some ideas or a how-to, to get these daily files moved to the Windows Server?

I can view the Windows Server fine via the GUI File Browser, I am able to drag'n'drop files into it through that. Just want to automate that.

---

### Post by wojox on 2009-07-01
Read this link

[http://www.linuxjournal.com/article/4360](http://www.linuxjournal.com/article/4360)

---

### Post by ronaldprettyman on 2009-07-01
> **Lotekk said:**
> Hello all, been looking for a solution to this and haven't found anything really helpful yet, my apologies if it has been discussed already and I missed it...

I've got a shell script to create a backup file of my wiki's files and database (via mysqldump). It places a nice neat ZIP in a directory thanks to cron, every day.

What I'm looking to do now is have the new file copied to a share on a Windows Server on the local network. I just don't know the syntax or how to go about doing this, whether it be adding more to the shell script or even a new cron job.  Can anyone offer some ideas or a how-to, to get these daily files moved to the Windows Server?

I can view the Windows Server fine via the GUI File Browser, I am able to drag'n'drop files into it through that. Just want to automate that.

Mount the windows share as a directory say
/share/windows
add it to your /etc/fstab
add to your script 
```
`cp $ZIPFILENAME /share/windows/$ZIPFILENAME`
```

/etc/fstab
```
//ntserver/share /share/windows smbfs username=username,password=password 0 0 
```
source [http://linuxpoison.blogspot.com/2007/10/mount-samba-share-using-fstab.html](http://linuxpoison.blogspot.com/2007/10/mount-samba-share-using-fstab.html)
you can even go as far as to add a stamp of count or something to the end of the file something like
$VARIBLEFOR STAMP
cp $ZIPFILENAME $PATHTOSHARE/$VARIBLEFORSTAMP.$ZIPFILENAME

---

### Post by sedawk on 2009-07-01
There is a tool similar to ftp or sftp to copy files using the
samba protocol: smbclient.
This tool was designed for non-interactive use, but you might
try to use it from a shell script, sending input with a "here document".

```

smbclient <lots of options and parameters>  <<ENDOFINPUT
go_to_correct_directory
send_the_correct_file
command_to_close_session_like_exit_or_quit
ENDOFINPUT

```

Alternatively you can try to mount the samba share to your linux
box permanently and then simply copy the file "locally" to that directory.
(mount -t smb ...)

My favourite solution would be (no password in a script, no permanent
mount needed) to run sshd on windows (e.g. inside of cygwin environment)
and use rsync (over ssh) or scp to copy the file and to add my local linux
box to the authorized hosts so no password is needed.

---

### Post by Lotekk on 2009-07-01
Awesome, thank you all very much!

---

