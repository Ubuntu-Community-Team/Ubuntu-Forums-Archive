---
title: "Simple Backup software not so simple..."
date: 2011-02-24
forum: General Help
---

### Post by mkowske on 2011-02-24
Help! I downloaded and installed "Simple Backup" as I wanted ... well, a simple backup solution and am having lots of problems.

1) I can backup something like my home directory no problem.
2) If I try to backup / (with reasonable excludes: /mnt, /media, /proc, etc) it bails with a TAR error. I figured this is because of permissions so ...
3) If I run with sudo, it looks like sbackup is now in "Administrator" mode, but when you actually go to RUN the backup it drops you back to your normal user priveliges (as indicated by stdout) and I still get the TAR error... 

So, how do I do a full system backup???  Here is the log of my failure:

```

Indicator application started (PID: 4160)
Updating GPG_AGENT_INFO to: None
Indicator application was started as superuser (EUID=0).
Now dropping privileges (to user 'mkowske').
drop privileges: running as mkowske/mkowske
Another `Simple Backup Indicator` is already running.
2011-02-24 00:25:45,696 - INFO: Log output for [Default Profile] is directed to file '/var/log/sbackup/sbackup.2011-02-24_00.25.45.695139.log'.
2011-02-24 00:25:45,697 - INFO: Profile settings are being read from file '/etc/sbackup.conf'.
2011-02-24 00:25:45,705 - INFO: Preparation of backup process
2011-02-24 00:25:45,706 - INFO: Initializing GIO File Access Manager.
2011-02-24 00:25:45,771 - INFO: Backup destination: /media/My Book/sbackup
2011-02-24 00:25:45,774 - INFO: Perform tests at specified location
2011-02-24 00:25:45,779 - INFO: Checking for snapshots stored in old formats
2011-02-24 00:25:45,781 - INFO: Corrupt snapshot `2011-02-24_00.12.18.495140.ubuntu.corrupt` found. Skipped.
2011-02-24 00:25:45,781 - INFO: Corrupt snapshot `2011-02-24_00.14.56.988485.ubuntu.corrupt` found. Skipped.
2011-02-24 00:25:45,782 - INFO: Invalid snapshot `2011-02-24_00.24.29.272245.ubuntu.ful` found: Unable to read mandatory file `ver`.
2011-02-24 00:25:45,782 - INFO: Invalid snapshot `2011-02-24_00.24.29.272245.ubuntu.ful` is being renamed.
2011-02-24 00:25:45,788 - INFO: Corrupt snapshot `2011-02-24_00.12.18.495140.ubuntu.corrupt` found. Skipped.
2011-02-24 00:25:45,788 - INFO: Corrupt snapshot `2011-02-24_00.14.56.988485.ubuntu.corrupt` found. Skipped.
2011-02-24 00:25:45,789 - INFO: Corrupt snapshot `2011-02-24_00.24.29.272245.ubuntu.corrupt` found. Skipped.
2011-02-24 00:25:45,790 - INFO: Snapshot '2011-02-24_00.25.45.789349.ubuntu.ful' is being made.
2011-02-24 00:25:45,790 - INFO: Setting packages File.
2011-02-24 00:25:45,901 - INFO: Setting Excludes File.
2011-02-24 00:25:45,902 - INFO: Setting compression format to `gzip`
2011-02-24 00:25:45,902 - INFO: Option 'Follow symbolic links' is disabled.
2011-02-24 00:25:45,902 - INFO: Inspect file system and collect file infos
2011-02-24 00:25:45,905 - INFO: Summary of backup
2011-02-24 00:25:45,905 - INFO: Number of directories: 0.
2011-02-24 00:25:45,905 - INFO: Total number of files: 0.
2011-02-24 00:25:45,906 - INFO: Number of symlinks: 0.
2011-02-24 00:25:45,906 - INFO: Number of files included in snapshot: 0.
2011-02-24 00:25:45,906 - INFO: Number of new files (also included): 0.
2011-02-24 00:25:45,906 - INFO: Number of files skipped in incremental snapshot: 0.
2011-02-24 00:25:45,907 - INFO: Number of items forced to be excluded: 0.
2011-02-24 00:25:45,907 - INFO: Number of items to be excluded by config: 0.
2011-02-24 00:25:45,907 - INFO: Maximum free size required is '0 MiB 0 KiB'.
2011-02-24 00:25:45,907 - INFO: Available disk size is '139849 MiB 975 KiB 512'.
2011-02-24 00:25:45,907 - INFO: Snapshot is being committed
2011-02-24 00:25:45,917 - INFO: Launching TAR to make a full backup.
2011-02-24 00:25:45,926 - ERROR: Unable to finish successfully. TAR terminated with errors.
(exit code: -11)
2011-02-24 00:25:45,928 - ERROR: An error occurred during the backup: Unable to finish successfully. TAR terminated with errors.
2011-02-24 00:25:45,937 - INFO: Terminating GIO File Access Manager.
2011-02-24 00:25:45,937 - INFO: Processing of profile failed with error: Unable to finish successfully. TAR terminated with errors.


```

I'd like to follow this up with --- what are people using for an easy, incremental, full system backup in ubuntu? Tried Grsync to but didn't see options to exclude folders.

---

### Post by Wtower on 2011-02-24
I have used sbackup on one desktop without issues. I have never tried to launch it manually though, I simply scheduled a cron job to run as root and it works as should.

---

### Post by NikoC on 2011-02-24
I'm not sure if the package covers your needs, but I'm using [Back in Time]("http://backintime.le-web.org/").

---

### Post by HermanAB on 2011-02-24
Not so fast...

First of all, why backup system files?  There are already copies of Linux all over the place at Canonical, Red Hat, Novell, IBM, Kernel.org, etc.  In general, it is better to only backup your data and re-install the system from scratch when necessary.  Re-installing from scratch is also much faster than restoring from backup.

Secondly, if you want to make a backup of a file, then you must have permission to read the file.  Therefore a backup is usually best done by root, not as a user.

---

### Post by Wtower on 2011-02-24
> **HermanAB said:**
> Not so fast...

First of all, why backup system files?  There are already copies of Linux all over the place at Canonical, Red Hat, Novell, IBM, Kernel.org, etc.  In general, it is better to only backup your data and re-install the system from scratch when necessary.  Re-installing from scratch is also much faster than restoring from backup.

Secondly, if you want to make a backup of a file, then you must have permission to read the file.  Therefore a backup is usually best done by root, not as a user.

Now that you mention I absolutely agree.

---

### Post by beta.tester on 2011-02-24
[B]
Hi

I do not know the backup program you are using, however I use the backup program from with Linux Mint which works great. It has 2 backup options which I find very helpful:

1) You can backup all your /home directory :)

2) You can backup your *software selection*, what I find very handy about this is if even I have to duplicate the system or reinstall it, by using the restore software selection option, it loads all the programs I may have overlooked and installs them and checks dependencies.

To install Backup program ala LinuxMint style :)


Go to the Repositories [http://packages.linuxmint.com/list.php?release=Isadora](http://packages.linuxmint.com/list.php?release=Isadora)

Download: mint-translations (2010.09.01 mint-common 1.0.5 mintbackup 2.0.6) When you have downloaded them install them in this order, it is crucial to install them in this exact order:

1) mint-translations
2) mint-common
3) mintbackup

You do this by highlighting the file and "use Ubuntu software centre (or GEBI installer)" to install them.

When you have done this look in System => admin => and there is your backup tool for ease of use perhaps right click and add to launcher.

Hope this helps, kind regards    john

[/B]

---

### Post by mkowske on 2011-02-24
> **HermanAB said:**
> Not so fast...

First of all, why backup system files?  There are already copies of Linux all over the place at Canonical, Red Hat, Novell, IBM, Kernel.org, etc.  In general, it is better to only backup your data and re-install the system from scratch when necessary.  Re-installing from scratch is also much faster than restoring from backup.

Secondly, if you want to make a backup of a file, then you must have permission to read the file.  Therefore a backup is usually best done by root, not as a user.

I tend to disagree. It may take longer to restore from a backup, but it requires a lot more time to go from a fresh install back to the state my system is currently in and that is USER time as I need to sit at the computer and download and configure all the programs I have installed since base installation. I'd like to avoid that and is why I was backing up more than just personal files.

And I did run the sbackup program as sudo. I also tried first doing 'su -' to root and then running it. Either way, it drops your privileges back to your normal user like shown in the log. That's why I posted about this.

---

### Post by mkowske on 2011-02-24
Back In Time and Mint both look promising -- I'll check those out thanks!

---

### Post by HermanAB on 2011-02-24
Howdy,

If you need to backup the configuration of some programs, such as servers, then just make a tar ball of the /etc directory and keep that.

---

### Post by cscj01 on 2011-02-24
I use luckyBackup to back up all my data to a network drive.  It works great, can be launched as superuser or a regular user, and is simple and straightforward. It uses rsync.

To backup my system files, I use Clonezilla Live to clone the system drive to an external USB drive.

I have sucessfully upgraded hard drives to larger capacity ones with these two programs and have never had a problem.

So, these may be something else you want to investigate.

---

