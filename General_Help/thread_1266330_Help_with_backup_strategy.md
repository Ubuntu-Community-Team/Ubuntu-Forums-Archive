---
title: "Help with backup strategy"
date: 2009-09-14
forum: General Help
---

### Post by anirvana on 2009-09-14
Hello all,

I am writing to get some advice regarding a good backup strategy for my application (code and data) which I will deploy on a remote server.

The situation: I will have access to a VPS/actual server somewhere. It will have some popular flavor of linux on it, probably Ubuntu 9.04. I will have admin rights.

The problem: How should I set up a backup strategy?

The guys who will give me access to the server may not be able to go in and add hard disks as and when I need them and so they have offered to provide more disk space up front than I would need. They will install the linux system, I will not have access to it during the OS installation process.

I think my application will never use more than 2 TB of disk space. The guys at the server farm can install a server with 4 1 TB disks for me. What could be the best way to mirror the 2 1 TB disks onto the other 2 1 TB disks after the OS has been installed.

Also if there is a standard recovery mechanism to bring back the system based on mirrored disk(s), I would really appreciate a pointer.

I have used Google to search and there's tons of articles, petabyte systems and what not. I am not sure how to go about it and hence this post.

Thanks in advance.

---

### Post by ccline19 on 2009-09-14
The first thing I would ask is if the system is considered critical? If it is then I would consider using rsync to replicate the data from one computer to another. The issue I have always had with raid systems is if the system experiences a hardware failure such as the motherboard, then the raid is essentially useless until you bring the system back up. Off loading your data even too an external 1tb hard drive would make your recovery faster. I tend to keep an older compter system and install linux on it in the event the main system goes down. Grab the external HD and plug it in and restore database.

Something also to consider is if the type of data you are planning to back up? Samba servers hold data much different than the linux file system. Some backup software has problems supporting different types.

I'm sure you have found there are plenty of solutins our there. If you have money to throw at the project I would go with external HD's and rsync.

I wanted to add that rsync can be used over the Internet in case you want to house the backup system in another building.

---

### Post by anirvana on 2009-09-14
@ccline19

Thanks for the reply. :-)

The external HD solution did cross my mind but the server admins have let me know that they would prefer an internal HDD based backup solution for my app.

I could ask for an NFS/Samba server/.. but I want to maintain a backup on the internal HDs. I realize that motherboard failure is critical, but its just that I'm more concerned about the data Vs 24x7x365 failover.

Thanks

---

### Post by ccline19 on 2009-09-15
Then I would consider looking for a backup solution that can compress the data while backing it up to another hard drive. I will look around and see what I can find. I know there are a few out there but not sure how good they are since it will be more of a snapshot of the data at the time of the backup.

---

