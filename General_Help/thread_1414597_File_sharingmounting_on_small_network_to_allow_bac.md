---
title: "File sharing/mounting on small network to allow backing up with rsync"
date: 2010-02-23
forum: General Help
---

### Post by Simon Cropper on 2010-02-23
Hi,

I am new to Ubuntu so forgive me if this is covered elsewhere but after several days I have not been able to find satisfactory answers. I am finding I am going around and around in circles so would appreciate any help -- I have just migrated a home office network last week and have nearly everything working :), except my backups.

**What I have...**

2x Ubuntu Machines

Machine #1 (8GB memory, two main hard disks, Linux Ext4)
Ubuntu Release 9.10 (karmic)
Kernel Linux 2.6.31-19-generic-pae
Gnome 2.28.1

Machine #2 (2GB memory, one hard disk)
Ubuntu Release 9.10 (karmic)
Kernel Linux 2.6.31-19-generic
Gnome 2.28.1

Both are connected to a router used to provide unique IP addresses for each machine and provide access to the Internet.

**What I am trying to do...**

Machine #1 is to be used as main file repository, that is hold the files being worked on.

Machine #1 and #2 need access to core directories on Machine #1 (i.e. company, personal, archives, images).

Machine #2 has some files in the home directory that can be accessed if Machine #1 is not turned on.

I want to create a 'batch file (called backup.sh)' using several rsync -avz --delete [source] [destination] to synchronize/mirror the various directories across this small peer to peer network.

First, I want to copy data in the home directory of Machine #2 to the core file storage directory to create a 'complete' set of files for backup. This means collecting any new documents as well as making a copy of the .evolution folder.

Second, I want to copy this entire file set on Machine #1 to a second hard disk mounted on the same machine, then copy the entire file set back to Machine #2 into a backup directory (I am not really copying all data just using rsync to mirror the directories). This will create 3 copies of the complete core dataset - 2 in Machine #1 on separate hard disks, and another on Machine #2 which is in a separate location.

**Where I am at...**

When on Machine #2 I browse to a directory and right-click on the directory icon to get access to the share folder dialog box. I select 'Sharing Options' and tick 'Share this Folder' and 'Allow others to create and delete files in this folder'. Once this is done I browse the network on Machine #1 and select Machine #2 -- I can see the shared directory. When I try and enter the directory I get a dialog box asking for a password. I fill this in but it just keeps reappearing over and over again after I complete the required information. Note: all computers are on the same workgroup, I have user accounts (same name and password) on both machines, but I still have this problem.

If I go back to the directory sharing option and select 'Guest access (for people without a user account)' I can see and browse the directory on Machine #2 from Machine #1. Personally I want to ensure that only Machine #1 can access Machine #2, not anyone visiting on the network.

So part of the problem stems from not being able to establish shared directories on different machines then mounting them.

Next problem, once mounted how do I reference them? This is a tit-bit of information that most UNIX or Linux users will laugh at but I have not been able to find this information anywhere. In Windows a mounted drive or shared is referenced with a drive letter. What is the equivalent in Linux? How do I say "rsync -avz --delete [/home/simon/Documents/Server_Data/] [Machine#1_SeparateMountcalledCorebackup/Server_Backup]" or "rsync -avz --delete [Machine#2/home/otheruser/Documents/] [/home/simon/Documents/Server_Data/OtherPersonsData]"?

Any assistance will be greatly appreciated.

Bye-and-bye, I have looked at a few GUI front-ends to rsync but they expect everything on the same machine/filesystem/mount and don't allow you to create a list of directories to backup in one shot. I want to automate this system so there is minimal chance of errors occurring, and want to avoid having to type the 20 odd commands over and over.

Simon

---

### Post by louieb on 2010-02-23
For file sharing with Linux to Linux take a look at NFS - its seamless. Accessing files and folders on another machine  would be the same way as accessing a data partition on the same machine. That is you access it through its mount point.  

[HOWTO: NFS Server/Client - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs") 

as for using rsync not the best person to ask here (i do image backups using partimage - am soon to be convering to FSarchiver). But don't see any reason you could not put your rsync commands in a txt file and make a script out of it.

---

### Post by Simon Cropper on 2010-02-23
louieb,

Thanks for that, I'll give it a try. 

Are you able to clear up the syntax for referring to shares or do you just point rsync to the directory once you mounted the share?

Also, what happens if only one computer is on and also wouldn't you need to set up the 'server' on both machines so their could be copying both ways?

Simon

---

### Post by patchwork on 2010-02-23
> I can see the shared directory. When I try and enter the directory I get a dialog box asking for a password. I fill this in but it just keeps reappearing over and over again after I complete the required information. Note: all computers are on the same workgroup, I have user accounts (same name and password) on both machines, but I still have this problem.

If you are using samba, and require user accounts on the server for access add the user name and password to the smbpasswd list:

```
sudo smbpasswd -a <username>
```

As far as referencing the location, after the shared directory is mounted you should be able to access it in the /home/<user>/.gvfs directory

---

### Post by louieb on 2010-02-24
Only if you want both machines to have access files the other - then Yes you will have to install the server on both.  

For example I have a desktop named **whitebox ** and a laptop named **t30box**

I keep backups and other stuff on whitebox - it has 2 NFS shares set up - I have a script that I run on t30box when I need to read or write to whitebox to mount the shares.

```

#!/bin/bash
sudo mount whitebox:/media/stuff /media/wbstuff
sudo mount whitebox:/media/utility /media/wbutility

```

By mounting the whitebox share in /media I get an Icon on  t30box's desktop that opens up the file browser in the share on whitebox. - Copy and paste works.

to copy a file from t30box to whitebox with the cli: 

```
cp /home/lou/test.tx /media/wbstuff
```

Gota go to work - check back later.

---

### Post by Simon Cropper on 2010-02-25
Hi,

1. Patchwork -- I tried smbpasswd and it did not work. Still keeps asking for permission over and over.
2. louieb -- tried setting up the NFS shares but I still encounter problems. I can see the shares and have managed to mount them, but despite being set up as read write, the data is only appears as read only. Plus I still encounter constant 'permission denied errors' when ever I try to copy. When I get some files to move because I use sudo I find that I can't read them with anything else.

File sharing is turning out to be a major issue for me as I have several people that use the same data but log in in different machines (same user name and password) but I am unable to repeatedly read and write files, directories or subdirectories. 

Simon

---

### Post by louieb on 2010-02-26
Good to see you got your shares set up. 

Linux permissions are getting in the way of being able to use them the way you want. 

For example my 2 NFS shares on the server /media/stuff and /media/utility have full read write permissions for everyone.   You use the chmod command to set permissions. 

Only change permissions for the NFS mounts - that is safe. But be warned there are directories in the Linux OS that if you change permissions or ownership - it will break it OS so throughly - your only chance to recover would be a reinstall.

```

sudo chmod  777 /media/stuff
sudo chmod  777 /media/utility

```This will leave the folders owned by root - but will allow full access for all. 

To check - you can use the ls command or in the file browser - right click - Properties>Permissions tab. 

You can also use Nautilus - run as Administrator - right click - Properties>Permissions Tab.


```

[lou@whitebox:~]$ ls -la /media
total 80
...
drwxrwxrwx 24 root root 4096 2009-12-21 04:55 stuff
drwxrwxrwx 12 root root 4096 2009-12-21 04:54 utility
...

```Then on each client do the same thing - change the permissions for the NFS mount directories.

---

### Post by Simon Cropper on 2010-02-26
louieb,

I did note that the permissions were all mixed up. The same thing happened with samba.

The funny thing is, is that it is the UID. One one machine I am UID=1000 while on the other I am UID=1001.

I used CHMOD as you suggested and it appears to work.

The only directories that I have done this to are those data directories contained in /home/ -- I have tried to ensure data is contained in this directory or shared in the /media/ as a mount.

Thanks for your help. 

Simon

---

### Post by louieb on 2010-02-26
Each user is identified by his login name and a numeric id (UID).  

Ideally they should match on each machine. For Linux in general root is UID 0 (zero). In Ubuntu the user added at install time is assigned UID 1000 (other distributions start at 500 - Fedora) - the UID is incremented as each user is added - or optionally you can set it when a user is added.      

Don't know much about where login name and/or UID is used. or how???

---

### Post by Simon Cropper on 2010-02-27
Hi All,

It seems that I/we have managed to get the backup to work.

In the end the NFS solution was the easiest, although if I chowned everything in Samba, like I had to in NFS, I would have managed to get Samba to work also.

Rsync worked OK, although it took 10+ hours to do the initial backup of of a 160GB system. Follow-up mirroring only takes minutes thankfully.  

For others following this post - rsync is best used following a clean boot. I found when running with other programs, especially Firefox, some processes get stuck in a loop (this is a known [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/488849") on karmic koala).

Thanks everyone for your help, especially louieb.

Simon

---

