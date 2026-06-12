---
title: "script for back to back backups"
date: 2009-07-30
forum: General Help
---

### Post by ub007 on 2009-07-30
Hi All,

I'm trying to write a script that would do a backup job n number of times.Effectively it should do 1 backup,it that succeeds,do a second backup job of the same files and so on.Will it be as simple as something like..

> while [ 1=1 ]
tar xvf backup.tar *.jpg 


or do i have to write any checks as in $? == 0 to see if each job was successful.

David

---

### Post by DaithiF on 2009-07-30
Hi,

while [ 1 ]
do
  tar xvf backup.tar *.jpg || break
done

will do what you want, a non-zero result from tar will cause the loop to exit.

but i'm not sure it makes much sense to do this -- what do you want to happen to the backup.tar file each time ?  its just going to get overwritten this way.  also, do you really want it to run continuously?  you may want to investigate cron instead to run a job at regular intervals, so that your script can just concentrate on doing the backing up part, and can delegate the mechanics of *when* to run to something better suited to the job.

---

