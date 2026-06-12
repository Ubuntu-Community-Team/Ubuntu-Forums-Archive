---
title: "FTP Help"
date: 2012-04-04
forum: General Help
---

### Post by SHOUTcastUK on 2012-04-04
Hey all, 

Im trying to setup a backup server for a few admins and friends,  for ftp access only, ive got the servers, all installed with 10.04 and all running VSFTPD 

Now my questions are... 

1) How can i set up the accounts to only allow compressed files? (.zip/.rar for example)
2) How can i limit the amount of disk space per user? 
3) How can i setup the other servers to download from the upload server so they are creating a second backup of the files? 

How we want the system to work...

Lets imagine we have 2 servers... 1)Upload Server & 2)backup server

Admin1 comes along with his backup and uploads it onto the **"Upload Server"** which all goes fine. His backup is now sitting there on the **''Upload Server"** Now what needs to happen is... Something needs to grab the data from the **"Upload Server"** and make a copy of it and then transfer it to the **"Backup Server"** ... Meaning that Admin1 will not just have one copy of his backup but 2 copies should anything happen to the upload server (because of public use ETC) then i can go to the backup server and make his data available via a new or repaired upload server!

As you may have noticed i am kind of new to ubuntu so looking for as much help as possible :-) 
Im sorry i have these crazy ideas and draw them on paper... quick enough to come up with the ideas... putting them into action is a slightly more difficult :-)

Look forward to your reply's

---

### Post by hughr2005 on 2012-04-04
Hi SHOUTcastUK,

If you give each user the permissions to only be able to modify files in their home directory, you can monitor the disk-usage, by home directory of each user. You can also cron a script to delete all files that do not have the right kind of extension. It would be something like:
```

echo "Using this script will delete all files in all home directories that do not end in .tar.gz or .zip"
echo "Use with *EXTREME* caution".
ls -l -R /home | grep -v .tar.gz >> /root/noncompressedfiles.txt
cat /root/noncompressedfiles.txt | grep -v .zip > /root/noncompressedfiles.txt

cat /root/noncompressedfiles.txt |while read line; do rm "${line}"; done

```

You'd need to execute that command as root.

The other idea though, I'm not sure... You'd need to cron an ftp script. Or you may need to modify and recompile the ftp server and whenever it ends a communication to run a script to copy the file to the equivalent directory on the backup server.

I hope that helps :)

---

### Post by SHOUTcastUK on 2012-04-04
Thanks very much for that im sure its going to help alot :-)

I was thinking of setting up the backup server as a RDP and using a WGET script... but im not 100% sure if it can be used to grab file from a FTP server... Was something that popped into my head... 

Thanks again

---

### Post by hughr2005 on 2012-04-04
I guess that's a way of doing it. Would the backup server be local to that network or somewhere else? If you can find an FTP library for python and write a script for it that way, you could set up a specific FTP user for the script that has access to everything. As long as you set up permissions and security properly you'll be fine :P

---

