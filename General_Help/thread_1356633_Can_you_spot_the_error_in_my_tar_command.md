---
title: "Can you spot the error in my tar command?"
date: 2009-12-16
forum: General Help
---

### Post by hashbangbinbash on 2009-12-16
I'm using the following command in a script run by crontab to backup my server...

```
#!/bin/bash

tar -cvpzf server.tar.gz --exclude=/home/jam/server.tar.gz --exclude=/proc --exclude=/lost+found --exclude=/sys --exclude=/mnt --exclude=/media --exclude=/home/jam/backup --exclude=/home/jam/stuff /

HOST='backupbox.net'
USER='jam'
PASSWD='marmalade'
FILE='server.tar.gz'

ftp -n $HOST <<END_SCRIPT
quote USER $USER
quote PASS $PASSWD
put $FILE
quit

#rm -rf /home/jam/server.tar.gz

END_SCRIPT
exit 0
```

/home/jam is my home directory, and backupbox.net is another server on which I have an account that I access via ftp to store the backup, and those "--exclude" directories are just directories I don't want in the backup. Aside from them everything under "/" is supposed to be backed up.

The command does actually create the file server.tar.gz, and sends it to the backup server ok. But if I try to open the archive on the Ubuntu Desktop of the server making the backup, I get this error:

> 
gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors

If I run ```
tar -tv ./server.tar.gz
``` on the command line in Terminal to just list the contents of the archive, it just hangs. 

Any body can give me a clue what I'm doing wrong? Or is there just a limit to the size of archive that tar can reliably create?

---

### Post by john newbuntu on 2009-12-16
Does tar -tv on the source box give the right result?  Did the ftp happen in binary mode?  Does the cksum match on source and dest? Do you want to exclude /dev and /proc directories also?

---

### Post by ean5533 on 2009-12-16
> **john newbuntu said:**
> Does tar -tv on the source box give the right result?  Did the ftp happen in binary mode?  Does the cksum match on source and dest? Do you want to exclude /dev and /proc directories also?
He's already excluding /proc :)

---

### Post by hashbangbinbash on 2009-12-16
> **john newbuntu said:**
> Does tar -tv on the source box give the right result?  Did the ftp happen in binary mode?  Does the cksum match on source and dest? Do you want to exclude /dev and /proc directories also?

Hi John,

On the source box I tried 

> sh-4.0$ tar -ztvf server.tar.gz

and got

> gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Exiting with failure status due to previous errors
sh-4.0$ 

The archive I'm unable to open is the copy before it even gets sent out, so the ftp stuff isn't relevent here, I guess I just showed that FTP bit in case I was missing a terminator or something. 

And yes I do want to exclude those directories like /dev and /proc.

---

### Post by john newbuntu on 2009-12-16
Now, in your script that is run from the cron, I would first suggest you to trap the error (#?) and also redirect stdout and stderr to a file.  This way, we will know if the tar process itself went ok.  Problems like space issues, bad disk etc may cause it to fail at times.  Now, assuming that part went clean and that there exists a bug in either tar or gzip, what does the command:
file server.tar.gz
give you?  If it is says "gzip compressed data, from Unix", then I am assuming that both tar and gzip went ok.  Otherwise, if it says "POSIX tar archive (GNU)", then I am assuming that the gzip portion failed, although the tar may have succeeded.  In that case, rename the file to server.tar and check contents using tar -tvf server.tar.  Once again, these are just my guesses.

---

### Post by hashbangbinbash on 2009-12-17
> **john newbuntu said:**
> Now, in your script that is run from the cron, I would first suggest you to trap the error (#?) and also redirect stdout and stderr to a file.  This way, we will know if the tar process itself went ok.  Problems like space issues, bad disk etc may cause it to fail at times.  Now, assuming that part went clean and that there exists a bug in either tar or gzip, what does the command:
file server.tar.gz
give you?  If it is says "gzip compressed data, from Unix", then I am assuming that both tar and gzip went ok.  Otherwise, if it says "POSIX tar archive (GNU)", then I am assuming that the gzip portion failed, although the tar may have succeeded.  In that case, rename the file to server.tar and check contents using tar -tvf server.tar.  Once again, these are just my guesses.

Ok... I'm not sure how to do that, googling about traps now.

To redirect to stnout, shall I add after the tar command (and all it's flags, targets and exlcusions) " > 2> /home/jam/backup_log_file"?

---

### Post by john newbuntu on 2009-12-17
The script pseudo-code is:

#!/bin/bash
{
    tar ....
    status=$?
    echo "STATUS = $status"
    ...more code...
} >> /home/userid/logfile 2>&1
exit 0

---

### Post by kjohri on 2009-12-17
> ```
tar -tv ./server.tar.gz
```

Try,
```
tar -tvzf ./server.tar.gz
```

to get a list of files in the archive. The "-f" option tells that the next argument is the name of the archive. Otherwise it thinks stdin is the archive and waits (hangs), 

To copy the files from the archive to the hard disk,

```
tar -xvzf ./server.tar.gz 
```

---

