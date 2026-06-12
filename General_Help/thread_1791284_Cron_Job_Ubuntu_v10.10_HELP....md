---
title: "Cron Job Ubuntu v10.10 HELP..."
date: 2011-06-26
forum: General Help
---

### Post by Debian1 on 2011-06-26
Hello,

I can't figure out why this #bin/bash command when called via CRON does not copy all folders/files as if I would run the same executable file from the given directory.

Example: CD Folders > run ./BudgetBak ---Executable runs successfully and copies all folders/files

However, when scheduling the CRONTAB to to the path of where the BudgetBak executable is stored, the CRON job runs successfully, but the folders/files are not included.

I've tried this under both ROOT and as well as scheduling the job under a tool called "Schedule Tasks". I receive the same result with no folders/files included.

Below is an example of my simple #!bin/bash script

#!/bin/bash
#BackupScript
# Backup up the Budget Directory to the BackupFolder

# TAR & Gzip each Directory
tar -czvf /home/UserAccount/Documents/Budget.tar.gz Budget
 
#Move tar.gz file to a specefic Directory
mv  /home/UserAccount/Documents/Budget.tar.gz /home/nate/BackupFolder

# Output a file with Date & Time of Backup
echo "Moved all Folders- Completed Successful on $(date)" >> /home/UserAccount/BackupC$

#Output information to .txt file
echo "TAR Completed Successfully on $(date)" >> /home/UserAccount/BackupCompleted.txt
#Space between each run
echo "###############################################################" >> /home$

Sample of my CRONTAB configuration:

#Backup Budget Folder
#*/01 * * * *  /home/UserAccount/Documents/BudgetBak

Your input is much appreciated!

---

### Post by furtypajohn on 2011-06-29
I think the main issue with your script is when it generates the tar.gz file. You typically run the script from the location where the script is being run, but cron does not do that. Cron is looking for "Budget" but it cannot find it and thus the script fails.

Since you already know the directory where Budget exists, and it doesn't change, just hard code the path in the script like so:

```
tar -czvf /home/UserAccount/Documents/Budget.tar.gz /path/to/Budget
```Now cron shoud not have a problem finding the Budget folder.

---

### Post by datenhalde on 2011-06-29
I agree, the relative path to Budget won't work for cron. 

crond usually sends any errors by email, if possible. Have you set up a mail system on that machine? 
Another possibility is to log any error messages of the commands included in your script to a file:
```
tar -czvf /home/UserAccount/Documents/Budget.tar.gz /path/Budget 2>> /home/user/backup.err.log 
```

---

### Post by yotam on 2011-06-29
Are you sure your script starts with PWD=${HOME}
where your **Budget** is located?

---

