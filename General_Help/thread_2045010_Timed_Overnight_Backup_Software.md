---
title: "Timed Overnight Backup Software?"
date: 2012-08-20
forum: General Help
---

### Post by SeanDS on 2012-08-20
Hello, I have been searching for a script or program in Ubuntu (server edition) that allows me to mirror a folder on the local filesystem with a remote FTP one, and does so overnight.

The reason is that I backup my personal folders in encrypted form to my home server, but I then want these backups mirrored on an off-site FTP server I've got access to. Overnight usage between 12am and 8am does not count against my ISP's monthly allowance, and since we're talking about hundreds of gigabytes, I obviously need the ability to have a scheduled backup (much like the way Transmission allows you to specify on an hour-by-hour basis when and when not to download/upload torrents).

I've thought about writing a script myself and making a cron job for it, but I don't know how I would go about handling the scheduling aspect, i.e. getting it to *stop* uploading stuff after 8am.

Any suggestions of existing software, or ideas for writing a script, would be greatly appreciated! Thanks.

---

### Post by dragonfly41 on 2012-08-20
I was browsing this forum yesterday (backup software for cloud) and read about luckyBackup which you'll find in Synaptic Package Manager.

It is a GUI for rsync and has a schedule option under Profile.

---

### Post by SeanDS on 2012-08-20
> **dragonfly41 said:**
> I was browsing this forum yesterday (backup software for cloud) and read about luckyBackup which you'll find in Synaptic Package Manager.

It is a GUI for rsync and has a schedule option under Profile.
Thanks for the reply. Is it possible to use rsync for an FTP server backup? I don't have SSH access to this server, only FTP.

The GUI is also potentially an issue. I've kept the server headless so far to avoid extra memory/CPU usage so I'd rather not install Gnome.

---

### Post by SeijiSensei on 2012-08-20
You could write a simple script to upload the files to the FTP server with [ncftpput]("http://linux.die.net/man/1/ncftpput"), part of the ncftp package.  Though I don't use FTP much any more, ncftp has always been my favorite command-line FTP client.  Running "sudo apt-get install ncftp" will install all the various parts of the ncftp suite.

Then create an entry in your [crontab]("https://help.ubuntu.com/community/CronHowto") to run the script each night.

---

### Post by thnewguy on 2012-08-20
I have a few suggestions. One is to use rsync and FUSE to mount the remote FTP site as a local folder. Start the backup with one cron job and then force it to stop with another cron job, in case it runs past 8am. A backup script might look like this

```

#!/bin/bash

mkdir -p /home/youruser/Remote
curftpfs ftp://your-username@your-password@servername.com/your-folder /home/youruser/Remote
rsync /path/to/your/data /home/youruser/Remote
fusermount -u /home/youruser/Remote


```

I've done similar transactions to backup remote websites and it has worked pretty well. A word of caution though, when you're backing up to/from FTP, all your data, passwords, etc are sent in plain text. This is a bit of a security concern.

To make sure your backup script stops on time, run a second script around 7:50am which says

```

#!/bin/bash

killall rsync
pkill name-of-your-backup-script

```


To make sure both rsync and the proper FUSE modules are installed, run

sudo apt-get install rsync curlftpfs

Cheers!

---

### Post by 1clue on 2012-08-20
Hundreds of gigabytes?

Speaking from a lot of years of trying to back things up remotely, you're going to find that hard to maintain.  Especially in a world where ISPs throttle your bandwidth when you get too greedy with it.

I built my box with a slot-loaded SATA drive bay.

I have a permanent archives folder where I make a single-copy uncompressed local backup (basically a folder copy that preserves permissions) of stuff that's important to me.  The database needs to be an actual backup, but everything else in my case is a usable copy of a real file.

I then plug in a 1.5 TB drive to the bay, make a folder whose name is today's date (2012-08-20) and drag my archives into it, again preserving permissions.  If the drive is full I throw away the oldest folder.  Unmount/unplug the drive and throw it in my backpack.

When I get to my remote storage site, I swap the drive in my backup with another drive.  I rotate through so even if the drive in my backpack is lost, the other drives have data which is no more than N backup cycles old, where N is the number of drives I'm rotating through.

Here are some observations:
[LIST=1]
[*]Automatic backups mean you automatically forget what's being backed up.  Too soon, your needs change and you're backing up something that stopped mattering 2 years ago, and not backing up the new project that replaced it.  You won't find out that's happened until you need to restore a backup of the new project.  Ask me how I know.
[*]Backup software is usually better at making backups than it is at restoring them.  I used to use a tape backup for years, and then found out that I couldn't restore a backup which was made on a new tape.  Probably had been that way from the beginning.  I found out because somebody I knew had a crash and couldn't restore HIS tape.
[*]The fewer magic spells involved in your backup, the more reliable your backup is.
[*]Your backup strategy should be somewhat manual so it stays in your conscience.  It should also be easy enough that you keep doing your manual portion of it.
[/LIST]

IMO your backup technology should be simple and something you use every day.  Today, for me, that means a SATA drive.  I spent years writing scripts and buying software and pushing data through a wire, and now all I do is a recursive copy to a removable SATA drive.

Every time I add a backup, I browse through the old ones and make sure I can still get at a few things.

My strategy means my data exists in 3 places:  My computer, my alternate storage site, and my backpack.  If there's a fire my laptop goes into the bag, I grab it and go down the steps.  My data is with me.

The only real fatal failure point here is me.  If I fail to drag a folder over, I lost my data.  Otherwise none of those strategies I spent thousands of dollars on since the late 80's does anything my current strategy does, and my current strategy is amazingly simple, fast, redundant, reliable and cheap.

---

### Post by SeanDS on 2012-08-20
> **SeijiSensei said:**
> You could write a simple script to upload the files to the FTP server with [ncftpput]("http://linux.die.net/man/1/ncftpput"), part of the ncftp package.  Though I don't use FTP much any more, ncftp has always been my favorite command-line FTP client.  Running "sudo apt-get install ncftp" will install all the various parts of the ncftp suite.

Then create an entry in your [crontab]("https://help.ubuntu.com/community/CronHowto") to run the script each night.
That would work except for the fact that I need it to finish at 8am if it's still running.

> **thnewguy said:**
> I have a few suggestions. One is to use rsync  and FUSE to mount the remote FTP site as a local folder. Start the  backup with one cron job and then force it to stop with another cron  job, in case it runs past 8am. A backup script might look like this

```

#!/bin/bash

mkdir -p /home/youruser/Remote
curftpfs ftp://your-username@your-password@servername.com/your-folder /home/youruser/Remote
rsync /path/to/your/data /home/youruser/Remote
fusermount -u /home/youruser/Remote


```I've done similar transactions to backup remote websites and it  has worked pretty well. A word of caution though, when you're backing up  to/from FTP, all your data, passwords, etc are sent in plain text. This  is a bit of a security concern.

To make sure your backup script stops on time, run a second script around 7:50am which says

```

#!/bin/bash

killall rsync
pkill name-of-your-backup-script

```To make sure both rsync and the proper FUSE modules are installed, run

sudo apt-get install rsync curlftpfs

Cheers!
This sounds like it might work, thanks very much. The plaintext issue isn't really that important as the files that will be getting sent are already encrypted. I use deja dup for a local network backup to the home server, and this encrypts the incremental backups. All I wish to do is mirror these encrypted backups onto the remote FTP.

A particular benefit of your method is that I can use the **--partial** flag with rsync which will delete partially transferred files off of the FTP. This is useful to ensure data integrity.

I'll try it tonight and get back to you. Thanks again!

---

### Post by drmrgd on 2012-08-20
Along those lines, I might suggest having a look at rsnapshot.  It's based on rsync with some nice little management capabilities like storing multiple backups (say 1 for every day of the week before rotating for example), and transfer / storage options.  It's also very easy to customize and runs as a script that can be launched very easily as a cron job.  Rsync, IMHO, is definitely the way to go, and you might find some of the added customizations in rsnapshot worthwhile.

---

### Post by SeanDS on 2012-08-20
> **1clue said:**
> Hundreds of gigabytes?

Speaking from a lot of years of trying to back things up remotely, you're going to find that hard to maintain.  Especially in a world where ISPs throttle your bandwidth when you get too greedy with it.

I built my box with a slot-loaded SATA drive bay.

I have a permanent archives folder where I make a single-copy uncompressed local backup (basically a folder copy that preserves permissions) of stuff that's important to me.  The database needs to be an actual backup, but everything else in my case is a usable copy of a real file.

I then plug in a 1.5 TB drive to the bay, make a folder whose name is today's date (2012-08-20) and drag my archives into it, again preserving permissions.  If the drive is full I throw away the oldest folder.  Unmount/unplug the drive and throw it in my backpack.

When I get to my remote storage site, I swap the drive in my backup with another drive.  I rotate through so even if the drive in my backpack is lost, the other drives have data which is no more than N backup cycles old, where N is the number of drives I'm rotating through.

Here are some observations:
[LIST=1]
[*]Automatic backups mean you automatically forget what's being backed up.  Too soon, your needs change and you're backing up something that stopped mattering 2 years ago, and not backing up the new project that replaced it.  You won't find out that's happened until you need to restore a backup of the new project.  Ask me how I know.
[*]Backup software is usually better at making backups than it is at restoring them.  I used to use a tape backup for years, and then found out that I couldn't restore a backup which was made on a new tape.  Probably had been that way from the beginning.  I found out because somebody I knew had a crash and couldn't restore HIS tape.
[*]The fewer magic spells involved in your backup, the more reliable your backup is.
[*]Your backup strategy should be somewhat manual so it stays in your conscience.  It should also be easy enough that you keep doing your manual portion of it.
[/LIST]

IMO your backup technology should be simple and something you use every day.  Today, for me, that means a SATA drive.  I spent years writing scripts and buying software and pushing data through a wire, and now all I do is a recursive copy to a removable SATA drive.

Every time I add a backup, I browse through the old ones and make sure I can still get at a few things.

My strategy means my data exists in 3 places:  My computer, my alternate storage site, and my backpack.  If there's a fire my laptop goes into the bag, I grab it and go down the steps.  My data is with me.

The only real fatal failure point here is me.  If I fail to drag a folder over, I lost my data.  Otherwise none of those strategies I spent thousands of dollars on since the late 80's does anything my current strategy does, and my current strategy is amazingly simple, fast, redundant, reliable and cheap.
Thanks for your detailed post.

This remote backup of mine is more of an absolute failsafe (well, as much as you can use the word 'absolute' when it comes to cloud storage).

My backup strategy is pretty much as follows:


[LIST=1]
[*]The important stuff on my everyday computer that I want to backup is mirrored in unencrypted form onto another hard drive within the same machine. Only I use this computer.
[*]The same important stuff is also backed up using deja dup to my home server, which will eventually have other users accessing it (with sudo access). These backups are therefore encrypted, and I have a weekly scheduled backup but I have found myself manually running it twice weekly. Changes since the last backup are backed up incrementally - a feature of deja dup.
[*]I now wish to have the encrypted incremental backups on my home server mirrored onto a remote FTP site.
[/LIST]
I was given free access to Livedrive from my workplace, but Livedrive don't make a Linux version of their (simple but powerful) software and I don't want to install Wine on my headless Ubuntu server. They do, however, provide FTP access to the raw folder tree within my account. You have to pay extra for SFTP or SSH access, but I don't care enough to pay for it, especially when my backups will be encrypted before they are sent to the FTP.


The remote backup is very much the last line of defence, for cases where all of my computers are stolen or the house burns down. I intend to 'set and forget' this remote backup script, because all it does is mirror a set of backups that I have a lot more manual input with. Therefore I believe my strategy includes the important human intervention element you refer to.

> **drmrgd said:**
> Along those lines, I might suggest having a look  at rsnapshot.  It's based on rsync with some nice little management  capabilities like storing multiple backups (say 1 for every day of the  week before rotating for example), and transfer / storage options.  It's  also very easy to customize and runs as a script that can be launched  very easily as a cron job.  Rsync, IMHO, is definitely the way to go,  and you might find some of the added customizations in rsnapshot  worthwhile.
Thanks, I'll maybe have a look at that. The solution mentioned by thnewguy seems pretty flexible in terms of how you conduct the backup once the fuseftpfs folder is mounted, so once I've got a basic system working I might experiment with other solutions. Cheers.

---

### Post by SeanDS on 2012-08-21
Hmmm... I created those scripts and had them run overnight. It successfully uploaded the files to the FTP server, but the files are empty (size 0 bytes).

When I run the script, rsync seems to 'upload' the files way too quickly - reporting 50Mbps etc. I think rsync thinks it's uploading the files properly, so it's probably a problem with curlftpfs. I've managed to create individual files and folders within the curlftpfs directory and it's worked fine - I've been able to access the files and their contents on the FTP using FileZilla. The problem seems to be when loads of files are being transferred at once.

I thought this might be a buffering issue, so I set rsync's temp directory to use /var/tmp/rsync and not a folder within the curlftpfs directory. Doesn't seem to have worked though.

Does anyone have any ideas as to what is going on?

Here are my two cron jobs:

**remotebackupstart.sh**
```
#!/bin/bash

cd ~

mkdir -p /home/sean/.livedrive
mkdir -p /var/tmp/rsync
curlftpfs ftp://ftp.livedrive.com/ /home/sean/.livedrive
rsync --progress --no-perms --no-owner --no-group --recursive --temp-dir=/var/tmp/rsync /home/sean/Backup/* /home/sean/.livedrive/Backup/



```**remotebackupstop.sh**
```
#!/bin/bash

cd ~

killall rsync
pkill remotebackupstart.sh

fusermount -u /home/sean/.livedrive


```**remotebackupstart.sh **is scheduled to run at 00:05 daily, and **remotebackupstop.sh** is scheduled to run at 07:55 daily.

I get a warning "fusermount: failed to open /etc/fuse.conf: Permission denied" when I run the cron first cron job - but /etc/fuse.conf is empty anyway so I don't think this matters. Nonetheless it seems to successfully mount the FTP directory in the correct place.

**EDIT**: Ok I've found what I think is the problem: after rsync 'transfers' the complete list of files, it then prints a load of errors afterwards, like this: **rsync: open "/home/sean/.livedrive/Backup/some/file": No such file or directory (2)**. Any ideas?

---

