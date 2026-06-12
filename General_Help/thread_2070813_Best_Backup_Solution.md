---
title: "Best Backup Solution?"
date: 2012-10-13
forum: General Help
---

### Post by SamSBT on 2012-10-13
Hey there,

I'm currently using the latest Ubuntu on a computer I have, I want to use this as a backup server for the other computers in my house.

Can any of you recommend a good piece of software that runs on Windows(etc) that would backup to FTP of SFTP on the Ubuntu server? Preferably something that checks and updates only the latest version of a file. 

I've done some research and tried backup applications such as DeltaCopy with rsync and it hasn't worked well.

Any ideas are appreciated.

Thanks,
Sam

---

### Post by cryptotheslow on 2012-10-13
I think you could use Samba to access a shared directory on the Ubuntu server from your Windows machine. And then just use Windows own Backup tool using the shared directory as the destination. I believe once it has carried out the first full backup, on subsequent scheduled runs it only backups up new or changed files.

Samba:
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

Windows Backup:
[http://www.sevenforums.com/tutorials/615-backup-user-system-files.html](http://www.sevenforums.com/tutorials/615-backup-user-system-files.html)


Alternatively, I believe Windows 7 has an NFS client "Services for NFS" which you can install. You could then setup NFS on the Ubuntu box to export the shared directory and use the NFS client on the Windows box to mount it. And from there - again you can use Windows Backup (or any other Windows backup application that suits your needs), using the NFS mount as the destination. I haven't tried this myself, but I can't see why it wouldn't work.

---

### Post by cbraxton on 2012-10-13
I usually use a batch file that runs robocopy on the Windows systems to back up to a Samba share on the Linux server. Something like:

```

@ECHO OFF
SET ARGS=/MIR /R:0 /XD *CACHE* *TEMP*
SET TARGET=\\SERVER\BACKUPS\%USERNAME%
robocopy "%USERPROFILE%" "%TARGET%" %ARGS%

```

The above simple batch file code snippet backs up new and changed files in the Windows user profile, excluding directories with "cache" and "temp" in their names. The backup is placed in a subdirectory corresponding to the Windows user name on a Samba share. Obviously you'd want to tailor it to your own needs and do some error checking to make it complete if you go this route. (Windows 7 and I think Vista come with robocopy. For XP and earlier you would need to download a copy.)

---

### Post by sandyd on 2012-10-13
> **SamSBT said:**
> Hey there,

I'm currently using the latest Ubuntu on a computer I have, I want to use this as a backup server for the other computers in my house.

Can any of you recommend a good piece of software that runs on Windows(etc) that would backup to FTP of SFTP on the Ubuntu server? Preferably something that checks and updates only the latest version of a file. 

I've done some research and tried backup applications such as DeltaCopy with rsync and it hasn't worked well.

Any ideas are appreciated.

Thanks,
Sam

Duplicati.

It supports ssh/rsync, so you can setup a ssh server on the target machine and let Duplicati sync to it.

You can also use Crashplan and use the 'backup to friend' option. That is free.

---

### Post by HermanAB on 2012-10-14
Or if you want to script it, make a FTP Batch File:

Let's say you want to backup your accounting data to a server on the internet and you want the process to be so easy, that your bookkeeper can do it.

Create a batch file called backup.bat, that looks something like this:

rem FTP backup batch file
ftp -s:ftpcommands

While the ftpcommands file to backup your accounting data, should look something like this:

open ftp.example.com
janedoe
mypassword
lcd c:\accounting
cd /
bin
mput *.*
quit

Put a shortcut to the batch file on the desktop and backing up your accounting data becomes a simple double-click, that your bean counter should be able to manage.

Obviously, this isn't secure, since the password is saved in the command file, but if you are worried about security, then you should not be running MS Windows...

---

