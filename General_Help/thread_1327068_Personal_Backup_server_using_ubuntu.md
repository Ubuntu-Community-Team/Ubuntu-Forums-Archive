---
title: "Personal Backup server using ubuntu"
date: 2009-11-15
forum: General Help
---

### Post by sundar22in on 2009-11-15
Hello,

I see a necessity to have an automated bacup solution for the following reasons:

* Growing collection of personal pictures. 
     * From camera, mobile, wecam etc.
     * When I go out with friends, each share pictures taken in thier camera via USB, Picasa etc.
* Growing collection of softwares and tools.
* Personal documents.

So I would like to backup and archive all my growing data in a home backup server. I am planning to have a redundant copy of backup data in 500 GB hard drive, so that I dont have to depend on one backup source. I do not want to go for a paid/free third party solution like Drop box for two reasons... one: I cannot be always online. Two: I am concerned about privacy.

Backup data should be compressed (To save space) and i dont need history of data. I only need the latest data (So I dont have to use version control). 


How do you manage and archive your personal data? Could you please share how do you backup ? and your personal experience? I understand that there is no silver bullet here which solves all the backup need I/we have. 

It will be of great help for everyone if you share how do you backup. Thanks in advance. :)

---

### Post by jasonsjunk on 2009-11-15
Install Sbackup it is in the repositories.  You can set a simple schedule when the backups are to occur and tell it where to place the backup files.  I basically backup my three computers to each other.  Computer 1 backs up its data to computer 2 and computer 2 ->3 etc....   This is easily accomplished using NFS shares.  

Sbackup compresses the backups and it will perform full and incremental backups according to how you set it up.  For a home network it works very well and it easy to configure via the gui.

---

### Post by nexes128 on 2009-11-15
You may also want to look at TimeVault ([https://wiki.ubuntu.com/TimeVault]("https://wiki.ubuntu.com/TimeVault")) as it allows for file versioning of files among other things, its still in alpha but is getting ready to go into beta.

---

