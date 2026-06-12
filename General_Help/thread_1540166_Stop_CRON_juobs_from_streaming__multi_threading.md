---
title: "Stop CRON juobs from streaming / multi threading"
date: 2010-07-27
forum: General Help
---

### Post by caiseya on 2010-07-27
running Ubuntu 8.04.2  and Ubuntu 8.04.1
 
hi,
 
I have a number of batch jobs that run other commands or batch jobs.
 
1. When I run them from the command line, they execute each job/command in serial
2. When they are run via CRON over night, its runs every command at the same time...!  not much fun for resource !
 
This sounds really simple switch somewhere but Iver search and search and cannot find the solution.
 
example batchjob = backup-client-all-local.pl
 
backup-client-all-local.pl contains:
/home/andy/cao/backup-client-local.pl  0
/home/andy/cao/backup-client-local.pl  1
/home/andy/cao/backup-client-local.pl  2
/home/andy/cao/backup-client-local.pl  3
/home/andy/cao/backup-client-local.pl  4
/home/andy/cao/backup-client-local.pl  5
/home/andy/cao/backup-client-local.pl  6
/home/andy/cao/backup-client-local.pl  7
/home/andy/cao/backup-client-local.pl  8
/home/andy/cao/backup-client-local.pl  9
etc
etc
 
any help would be great !
 
Andy

---

