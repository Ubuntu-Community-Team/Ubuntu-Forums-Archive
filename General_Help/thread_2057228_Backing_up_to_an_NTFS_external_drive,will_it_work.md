---
title: "Backing up to an NTFS external drive,will it work?"
date: 2012-09-13
forum: General Help
---

### Post by cogset on 2012-09-13
Well as the title says,I'm going to do a TAR of my installation on an external hard drive,which happens to be formatted in NTFS:will this work or am I just asking for trouble,and be better off reformatting it to ext4 before proceeding?

---

### Post by GeForce 9500GT on 2012-09-13
I think it will work. Basically, the fileformat is not of any important during backing up. I don't think it matters whether you're using a ext3/ext4 formatted drive or a ntfs formatted drive.

---

### Post by Bucky Ball on 2012-09-13
Run that by me again ... you have Ubuntu installed on disk 1 and you want to make a tar file of the entire install (presumably the / partition) and save it to disk 2 as a backup of your install? Doesn't matter what disk 2 is formatted as. On the other hand, if you intend running the Ubuntu install from disk 2 that will be impossible as it needs to be EXT*.

This is all good but there are other ways of making barebones backups of your install. Tried rsync? It will make an exact replica which you can burn to disk and install on another machine if you wish. There's a few apps about for backing up entire installs. Are you also talking about your data or just the Ubuntu install?

---

### Post by cogset on 2012-09-13
> you have Ubuntu installed on disk 1 and you  want to make a tar file of the entire install (presumably the /  partition) and save it to disk 2 as a backup of your install?Yep,that exactly.

 > Doesn't matter what disk 2 is formatted as. On the other  hand, if you intend running the Ubuntu install from disk 2 that will be  impossible as it needs to be EXT*.I didn't even think  about that,but,now that you've brought this up,it sounds very  interesting indeed:what would be actually needed to do that?

> This is all good but there are other ways of  making barebones backups of your install. Tried rsync? It will make an  exact replica which you can burn to disk and install on another machine  if you wish. There's a few apps about for backing up entire installs.  Are you also talking about your data or just the Ubuntu install?Actually  I went for a simple tar of my / directory because I want to get a feel  of how things work at a basic level,before trying more advanced routes.

---

### Post by Bucky Ball on 2012-09-13
> **cogset said:**
> 
 I didn't even think  about that,but,now that you've brought this up,it sounds very  interesting indeed:what would be actually needed to do that?

Here's a start but there is a lot out there on this. Dig about:

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)
[http://ubuntufriends.wordpress.com/2007/03/31/edit-and-create-your-bootable-iso-image-the-easy-way/](http://ubuntufriends.wordpress.com/2007/03/31/edit-and-create-your-bootable-iso-image-the-easy-way/)

Generally used to customise a kernel then deploy on several machines. You can also make your own flavour of Ubuntu like this and share! Look for 'customise kernel ubuntu' 'create custom image ubuntu' or something like that. 

> **cogset said:**
> Actually  I went for a simple tar of my / directory because I want to get a feel  of how things work at a basic level,before trying more advanced routes.

All good, then. You're rolling. 

Generally, I keep all personal data out of /. I used to create a separate /home partition (which means a /home directory is not created in / by default) but now let the install create the /home directory in /, delete all the directories in there and create symlinks to directories on a data partition so all three installs can use the same /documents, /music, etc. 

Your settings are in /home (directory or separate partition). Hit Control+h to show hidden files and the settings folders for your apps should be there. Some stuff in / is definitely not worth backing up, unless you are intending to create a straight copy/ISO image to reinstall or as backup, but you would want to make an ISO file of your current install for that.

Good luck and enjoy the learning curve. ;)

* You might find this of interest also:

[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

PS: You might like to play around with Unison while you're tinkering. Syncs directories, even across a network. It's in the repositories (Software Centre or Synaptics or 'sudo apt-get install unison').

---

### Post by cogset on 2012-09-15
> I used to create a separate /home partition (which means a /home  directory is not created in / by default) but now let the install create  the /home directory in /, delete all the directories in there and  create symlinks to directories on a data partition so all three installs  can use the same /documents, /music, etc. 

Neat trick,actually I was pondering something like that for the future,as I like to tinker with multi-boot setups.

And thanks for hinting at rsync and unison,BTW.

---

### Post by Bucky Ball on 2012-09-15
> **cogset said:**
> Neat trick ...

Yea, I thought so. Think it was oldfred that put me onto the idea ...

Works great. Before I used to create the /home for each install using the existing /home partition (this can be done by allowing the install to use the existing /home but not format it). I could still access the data from any install but this is much better. At least for me. You need to choose 'Something Else' and partition manually when you get to that part of the install.

You can also use one /swap for all installs. Just don't create a new one and it will use the existing one by default (which is same as /home if you mark to use but not format). ;)

---

### Post by JKyleOKC on 2012-09-15
> **Bucky Ball said:**
> Some stuff in / is definitely not worth backing up, unless you are intending to create a straight copy/ISO image to reinstall or as backup, but you would want to make an ISO file of your current install for that.It gets worse than that if you actually try to back up everything from "/" down, recursively. When you get to "/proc" the operation will go nuts, since this isn't really a directory but is actually a way to look into RAM itself, and it also shows every one of the dozens of processes that are running, as directories. Each of them in turn seems to reference itself, and you have an infinitely deep loop of recursion. You would be lucky to escape with only one corrupted disk file!

Another "directory" that must be excluded from backup is "/dev" which simply lists all detected devices in the system.

For a safe "full-system" backup all that's really necessary are /home and /etc; you can also include /usr since that's where most (but not all) program files and libraries reside. However the safest plan is to use an existing and widely accepted backup program. I was happy with "backuppc" which is in the repositories, but it's overkill if you don't have a network to worry about...

---

