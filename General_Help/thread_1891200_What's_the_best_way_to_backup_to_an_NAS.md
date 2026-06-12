---
title: "What's the best way to backup to an NAS?"
date: 2011-12-05
forum: General Help
---

### Post by diablo75 on 2011-12-05
I have been hired to put together a system of 5 computers (1 server, 4 work stations) for a clinic that is switching over to a new electronic health records system.  The company they will be purchasing their software/services from is called Office Practicum.  My job is to setup the hardware and backend with support from Office Practicum during the software setup phase.  They suggest Windows Server 2008 or Linux to be the OS for the server and I've opted for Ubuntu Linux with their blessing.  The workstation computers will be running Windows 7.

The server is going to be a Lenovo TS-430 with two hard drives running in RAID 1.  Outside of that will be a RAID enabled NAS.  The roll of the server, so far as I know, is to primarily act as a storage location for database information which will be accessed by the clients and I have a feeling that the reason they suggest Linux for their servers (but not their clients) is because there is probably no actual proprietary software of their own that will be running on the server, and instead its sole roll in this is to act strictly as a file server.  Simple enough.

There will be a NAS that I'd like to have housing another duplicate of the data that will be stored on the server and optionally backup images of the hard drives from all the work stations so if one of those die we have an additional fallback option.

What's the best way to automate a backup routine where the Ubuntu system automatically backs up the DBs being saved to it from the other workstation computers.  Is there a way to have a form of instant sync that takes place when files are added/changed, perhaps with versioning and auto pruning old versions away safely (like what Dropbox does but locally)?

---

### Post by Drenriza on 2011-12-05
Client backup.
Cant you write a Windows script to use telnet or scp to copy a folder containing the files that should be backed up and place it in a folder on the NAS. After it has been through zip or something.

Backup server.
Again write a simple bash script to create a folder and place the correct files / info in the folder, get it through tar and then scp / telnet / ssh / rsync it over to the NAS server in the correct folder.

You can also easily extract info from a database with simple one liner commands and place the information in a txt file.

The bash script could be placed in cron and their must be some way to automatically call the script on Windows as well.

---

### Post by diablo75 on 2011-12-05
For the Windows clients I was hoping to find a commercial backup program that would backup the entire drive as an image file, perhaps once a week or something, simply to make the reloading process take less time if a drive were to suddenly fail.  I'd rather the reload take a matter of minutes instead of hours spent reinstalling the OS+updates and software plus settings.

But for the server, yeah a script could probably work.  But I'd like something a little more sophisticated, easier to implement and perhaps perform backups in real time instead of on a schedule... but hey, I have to admit I'm a little new at this.

---

### Post by Mark Phelps on 2011-12-05
Since the client PCs are running Win7, and you already said you want the server to act as a database server,  how do you know that a Linux server will even do what you need? 

Win7 has problems reading and writing to Linux filesystems -- why complicate that further with forcing a Linux filesystem onto the only server they will access? And, if you're going to format the server drives as NTFS, then what is the point of using Linux as a server OS?

As to database server, are you going to access it via ODBC from the Win7 PCs? Do you even know of an ODBC client that will run under Win7 but be able to access Linux filesystems?

Seems to me that if the company is willing to pony up the cost of Windows Server 2008, you should consider that first, not a Linux solution.

---

### Post by jtokarchuk on 2011-12-05
We actually roll this exact solution out at work. I work as a computer technician.

We use a program called BackupAssist. It has native support for rsync backups. With rsync, once the entire backup is "seeded" (in place on the server) it will only take increments. It will take changes only. 

You can configure the scheduling of such backups too, from everyday to weekly or however you like. 

[http://www.backupassist.com/index.html](http://www.backupassist.com/index.html)

Check it out. I think this is the solution to go for. You can use free solutions like Deltacopy but the reporting on something like that is weak at best. Where Backupassist can be configured to email you reports every morning (I know Deltacopy can too, but they aren't as robust)

---

### Post by diablo75 on 2011-12-05
> **Mark Phelps said:**
> Since the client PCs are running Win7, and you already said you want the server to act as a database server,  how do you know that a Linux server will even do what you need?

The software developers mentioned in the OP told me they support Linux and also said there is no technical drawback to using Linux as the server OS vs. using Windows Server.  So if there's anybodies word I'm going to follow about this, it's theirs.
> 
Win7 has problems reading and writing to Linux filesystems -- why complicate that further with forcing a Linux filesystem onto the only server they will access? And, if you're going to format the server drives as NTFS, then what is the point of using Linux as a server OS?

As to database server, are you going to access it via ODBC from the Win7 PCs? Do you even know of an ODBC client that will run under Win7 but be able to access Linux filesystems?

Seems to me that if the company is willing to pony up the cost of Windows Server 2008, you should consider that first, not a Linux solution.
You've never heard of SSH, FTP or SAMBA?  Databases aren't some mysterious thing.  At the end of the day, they're just files.  And moving files over a network isn't some kind of new, experimental thing.  It's what computer networking has always been about.

---

### Post by Drenriza on 2011-12-07
> **diablo75 said:**
> For the Windows clients I was hoping to find a commercial backup program that would backup the entire drive as an image file, perhaps once a week or something, simply to make the reloading process take less time if a drive were to suddenly fail.  I'd rather the reload take a matter of minutes instead of hours spent reinstalling the OS+updates and software plus settings.

Install a client once and install all the necessary programs and update all drivers.
Then take a image of the client. If one fails then just reload the image since it can be used for all the clients. And then take the backup file and restore it.

> We use a program called BackupAssist. It has native support for rsync backups. With rsync, once the entire backup is "seeded" (in place on the server) it will only take increments. It will take changes only.
Hopefully it takes the "changes" and save to a new file and not overwriting the already existing one. What if you make a fuckup then :p? Then you screw up your backup as well.

Take a backup so you have a 
Daily backup and a weekly backup. Then you can always rollback a week if needed.

---

### Post by diablo75 on 2011-12-13
> **Mark Phelps said:**
> 
As to database server, are you going to access it via ODBC from the Win7 PCs? Do you even know of an ODBC client that will run under Win7 but be able to access Linux filesystems?

[http://www.firebirdsql.org/](http://www.firebirdsql.org/)

---

