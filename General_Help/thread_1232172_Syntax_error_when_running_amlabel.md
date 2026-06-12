---
title: "Syntax error when running amlabel"
date: 2009-08-05
forum: General Help
---

### Post by webmaster@healthquotes.ca on 2009-08-05
Hi all 

I am trying to use amlabel (a binary of Amanda) to label some more slots that I have created for my "daily" backup configuration. 

Here is the command I am running: "su backup ./amlabel daily daily-21 slot21".

The set is "daily", the label I want to set is "daily-21" and the name of the folder (e.g. slot) is "slot21". Also, the backup user is "backup". 

It results in the following error: "./amlabel: 1: Syntax error: "(" unexpected". 

I am running the command I posted in the "/usr/sbin" folder.

My slots are in "/var/backups/amanda/daily/slots/". I've tried fully qualifying the path to the slots folder, with the same result.

Thanks in advance for any help.

p.s. I have posted this question in the BackupCentral forum and am not getting much help.

---

