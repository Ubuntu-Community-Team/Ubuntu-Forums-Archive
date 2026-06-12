---
title: "cron jobs  not working"
date: 2012-04-23
forum: General Help
---

### Post by winzip on 2012-04-23
crontab
------------
# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
**[COLOR=Red]05 14 * * * /home/user/backup.sh[/COLOR]**  <-----**[COLOR=Blue]this is my job . this is not invoked.[/COLOR]**

what is the issue ?

---

### Post by matt_symes on 2012-04-23
Hi

Can you post the script ?

What command did you use to set the cron entry ? Why are you not using your crontab ?

Does the script have full paths and access to all environmental variables it may need ?

Is the script executable ?

Kind regards

---

### Post by winzip on 2012-04-23
> **matt_symes said:**
> Hi

Can you post the script ?


It may not be of any use....its quite lengthy....its just a couple of  cp  and mysqldump ..

> 
What command did you use to set the cron entry ?
**sudo  vi  crontab**

> 
Why are you not using your crontab ?

because I can not  save. I  get readonly.  I can save only if I use sudo 


> 
Does the script have full paths and access to all environmental variables it may need ?
Yes

> 
Is the script executable ?
yes

---

### Post by kjohri on 2012-04-23
> 17 * * * * root cd / && run-parts --report /etc/cron.hourly
25 6 * * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6 * * 7 root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6 1 * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
05 14 * * * /home/user/backup.sh <-----this is my job . this is not invoked.


In the last line containing backup.sh, userid is missing.

[Using cron]("http://www.softprayog.in/tutorials/using-cron")

---

### Post by matt_symes on 2012-04-23
Hi

Personally i would use your crontab as there will be no problems with users.

Open a terminal and type

```
crontab -e
```Pick nano as the editor if given the choice as it's the easiest. Add this line.

```
05 14 * * * /home/user/backup.sh
```Have you run the script without using cron to verify it works ? 

If it does work then that would point to the script missing an environmental variable or not having a full path somewhere.

Please post the script even if it is large.

Kind regards

---

### Post by winzip on 2012-04-23
> **kjohri said:**
> In the last line containing backup.sh, userid is missing.

[Using cron]("http://www.softprayog.in/tutorials/using-cron")

yes. I have noticed that.  which userid to put here ?

I dont login with root. I login with userid  as 'user'.

so should I put  'user'  or 'root'   ?

---

### Post by matt_symes on 2012-04-23
Hi

> **winzip said:**
> yes. I have noticed that.  which userid to put here ?

I dont login with root.
I login with userid  as 'user'.

so should I put  'user'  or 'root'   ?

You can use either. 

I would still use your own crontab though.

Kind regards

---

### Post by winzip on 2012-04-23
> **matt_symes said:**
> Hi





I would still use your own crontab though.

Kind regards
Ok. I will give this a try. Where this file will be generated if i use crontab -e and nano ?
I am using default crontab found under /etc.
What advantage i will get here if i follow this approach?

---

### Post by matt_symes on 2012-04-23
Hi

> **winzip said:**
> Ok. I will give this a try. Where this file will be generated if i use crontab -e and nano ?
I am using default crontab found under /etc.

They are kept in ```
/var/spool/cron/crontabs/
```There is a file for each user in there. Only root can read the directory so to view it you will need elevated privileges.

```
sudo ls /var/spool/cron/crontabs/
```This is to stop you messing with other users crontab files and is part of Linux's security.

> What advantage i will get here if i follow this approach?* It will be run under your users profile. 
* It will not clutter up roots crontab. 
* It's what your users crontab is for.
* It allows you to have different cron jobs than other users on your system.

Kind regards

---

### Post by winzip on 2012-04-23
> **matt_symes said:**
> 

```
sudo ls /var/spool/cron/crontabs/
```



this prints nothing. no listing found.

What do I do now ?

---

### Post by matt_symes on 2012-04-23
Hi

To edit your crontab open a terminal and type

```
crontab -e
```To list any entires in your crontab type

```
crontab -l
```Your crontab gets created when you first edit and save it.

```
matthew@matthew-Aspire-7540:~$ sudo ls /var/spool/cron/crontabs/
matthew
matthew@matthew-Aspire-7540:~$
```

Kind regards

---

### Post by winzip on 2012-04-23
> **matt_symes said:**
> Hi

To edit your crontab open a terminal and type

```
crontab -e
```To list any entires in your crontab type[/CODE]


It asks for editor.  I am not comfortable with nano ....is it not possible to use  vi editor to edit  my own crontab ?

---

### Post by matt_symes on 2012-04-23
Hi

> **winzip said:**
> It asks for editor.  I am not comfortable with nano ....is it not possible to use  vi editor to edit  my own crontab ?

You should be able to select vim (vi improved). I use that myself.

Kind regards

---

### Post by winzip on 2012-04-23
> **matt_symes said:**
> Hi



You should be able to select vim (vi improved). I use that myself.

Kind regards

There is no vim ....  but   it offers  vim.tiny ..vim.big  etc 

Does vim work here ?

---

### Post by matt_symes on 2012-04-23
Hi

> **winzip said:**
> There is no vim  but vim.tiny ..vim.big  etc it offers.

Does vim work here ?

Is that not close enough (vim.big) ? 

You can set up your own alternative link to point to another editor if you do not like the choices it offers.

Kind regards

---

### Post by winzip on 2012-04-23
> **matt_symes said:**
> 

You can set up your own alternative link to point to another editor if you do not like the choices it offers.



how ? when I type  **crontab -e** it opens in nano by default  now....looks like  nano been linked already when I tried first time.... however   I  want to open this   in vim .  how do I  link   **crontab -e **to open in vi or vim  ?

I feel uncomfortable with nano ....I  feel comfortable with vi / vim though.  How do I change editor ?

---

### Post by matt_symes on 2012-04-23
Hi
```

EDITOR=/usr/bin/vim crontab -e
```

This will run crontab with vim (or any other editior you choose). It's a one shot command and will revert back to nano after use.

If you want to make it permanent then you need to update the links. Check out the manual for update-alternatives.

```
man update-alternatives
```

The symlink is editor if i remember correctly.

Kind regards

---

### Post by winzip on 2012-04-23
> **matt_symes said:**
> Hi
```

EDITOR=/usr/bin/vim crontab -e
```This will run crontab with vim (or any other editior you choose). It's a one shot command and will revert back to nano after use.

If you want to make it permanent then you need to update the links. Check out the manual for update-alternatives.

```
man update-alternatives
```The symlink is editor if i remember correctly.

Kind regards

Ok.thanks.

I'll do this  though..

EDITOR=/usr/bin/vi crontab -e

---

### Post by winzip on 2012-04-23
I tried  EDITOR=/usr/bin/vi crontab -e  and I got this...

please see the attachment

---

### Post by matt_symes on 2012-04-23
Hi

That is no problem. It creates a temporary file while you are editing it.

Kind regards

---

### Post by winzip on 2012-04-24
Thanks. I  have tested crontab ..but its not working  the same way as it work from a terminal.



When running the cron job  I  dont get the zip  output.  Whats wrong ?

my script has this line ..
.................................
zip -9 -r /home/user/DB_BACKUP/$(date +%e-%B-%Y).zip /home/user/DB_BACKUP/$(date +%e-%B-%Y)


I  get this output 

drwxr-xr-x 3 root root 4096 2012-04-24 17:10 24-April-2012
[COLOR=Blue]-rw------- 1 root root 5348 2012-04-24 17:10 ziFfoFcr[/COLOR]


But when I run script  using terminal  

$./backup.sh  <-----  this works fine . I get zip file.


Whats wrong with cron jobs ?

---

### Post by matt_symes on 2012-04-24
Hi

Please post the full contents of your script. The script is a bash script ? You are using bashisms.

**EDIT: **Maybe this will help you.

This is my test back up folder containing one a directory called 24-April-2012. The directory contains a file called test.

```
matthew@matthew-Aspire-7540:~$ ls test_backup/
24-April-2012
matthew@matthew-Aspire-7540:~$ ls test_backup/24-April-2012/
test
matthew@matthew-Aspire-7540:~$ 
```The contents of the file test is hello.

```
matthew@matthew-Aspire-7540:~$ cat test_backup/24-April-2012/test 
hello
matthew@matthew-Aspire-7540:~$
```This is my backup script

```
matthew@matthew-Aspire-7540:~$ cat backup.sh 
#!/bin/bash

/usr/bin/zip -9 -r /home/matthew/test_backup/$(/bin/date +%e-%B-%Y).zip /home/matthew/test_backup/$(/bin/date +%e-%B-%Y)
matthew@matthew-Aspire-7540:~$
```This is my crontab entry to run the backup script. Set your as required.

```
matthew@matthew-Aspire-7540:~$ crontab -l
59 * * * * /home/matthew/backup.sh
matthew@matthew-Aspire-7540:~$
```This is cron running according to syslog.

```
matthew@matthew-Aspire-7540:~$ tail -n5 -f /var/log/syslog
Apr 24 20:55:17 matthew-Aspire-7540 crontab[6490]: (matthew) BEGIN EDIT (matthew)
Apr 24 20:55:37 matthew-Aspire-7540 crontab[6490]: (matthew) REPLACE (matthew)
Apr 24 20:55:37 matthew-Aspire-7540 crontab[6490]: (matthew) END EDIT (matthew)
Apr 24 20:55:42 matthew-Aspire-7540 crontab[6510]: (matthew) LIST (matthew)
Apr 24 20:56:01 matthew-Aspire-7540 cron[1331]: (matthew) RELOAD (crontabs/matthew)
Apr 24 20:59:01 matthew-Aspire-7540 CRON[6529]: (matthew) CMD (/home/matthew/backup.sh)
Apr 24 20:59:01 matthew-Aspire-7540 postfix/sendmail[6534]: fatal: open /etc/postfix/main.cf: No such file or directory
Apr 24 20:59:01 matthew-Aspire-7540 CRON[6528]: (matthew) MAIL (mailed 1 byte of output; but got status 0x004b, #012)
^C
matthew@matthew-Aspire-7540:~$
```The folder test_backup now contains the zip file with the correct date as part of the file name.

```
matthew@matthew-Aspire-7540:~$ ls test_backup/
24-April-2012  24-April-2012.zip
matthew@matthew-Aspire-7540:~$
```And here is the contents of the zip file. It includes the file test.

```
matthew@matthew-Aspire-7540:~$ unzip -l test_backup/24-April-2012.zip                                                                                                      
Archive:  test_backup/24-April-2012.zip
  Length      Date    Time    Name
---------  ---------- -----   ----
        0  2012-04-24 20:37   home/matthew/test_backup/24-April-2012/
        6  2012-04-24 20:37   home/matthew/test_backup/24-April-2012/test
---------                     -------
        6                     2 files
matthew@matthew-Aspire-7540:~$
```And finally here is the contents of the zipped file. It prints the contents of test, that contained the word hello, to stdout.

```
matthew@matthew-Aspire-7540:~$ unzip -p test_backup/24-April-2012.zip 
hello
matthew@matthew-Aspire-7540:~$
```Kind regards

---

### Post by winzip on 2012-04-25
I see you are using /usr/bin/zip i.e full path ? How do i find the full path of zip in my system ?

Is it locate zip ?  Or whereis zip ? Or something else ?

---

### Post by ahso4271 on 2012-04-25
which zip

---

### Post by winzip on 2012-04-25
Please find the current script attached.   I  have masked credentials used in this script though. Hope that should not be a problem.


Here is the output

Result:
------------

output  under DB_BACKUP

drwxr-xr-x 3 user user 4096 2012-04-25 12:30 25-April-2012
-rw------- 1 user user 5348 2012-04-25 12:30 ziYh51PV

Please tell why this does not work via  cron job ?

this works fine from terminal.

---

### Post by matt_symes on 2012-04-25
Hi

Not sure why. Here is a revised version of your script. 

It calculates the date once, stores its value in curr_date and reuses its value. It uses mkdir with the p switch to create the parent directories.

I added some comments as to what i thought you were trying to do.

```

#!/bin/bash

# Get the date
curr_date=$(date +%e-%B-%Y)

# Dump date as test. REMOVE WHEN VERIFIED DATE IS CORRECT.
echo ${curr_date} > ~/curr_date_test 
echo "/home/user/DB_BACKUP/${curr_date}.zip" >> ~/curr_date_test

# Make the backup folders 
mkdir -p /home/user/DB_BACKUP/${curr_date}/Alfresco 

# Get dump of test database 
mysqldump -P 3306 -h 192.168.2.85 -u root -proot test_db > /home/user/DB_BACKUP/${curr_date}/test_db.sql 

# Copy revelent data 
cp -r /home/user/alfresco/alf_data/backup-lucene-indexes /home/user/DB_BACKUP/${curr_date}/Alfresco/ 

# Dump main database 
mysqldump  -P 3306 -h 192.168.2.85 -u alfrescouser -palfrescouser alfresco >/home/user/DB_BACKUP/${curr_date}/alfresco.sql 
 
# Copy extra files. 
cp -r /home/user/alfresco/alf_data/contentstore* /home/user/DB_BACKUP/${curr_date}/Alfresco/ 
 
# Zip up files 
/usr/bin/zip -9 -r /home/user/DB_BACKUP/${curr_date}.zip /home/user/DB_BACKUP/${curr_date} 

# Clean up. 
rm -rf /home/user/DB_BACKUP/${curr_date}
```

This will check the date is being created correctly.

```
cat ~/curr_date_test
```

Try it and see how it works on your system.

Kind regards

---

### Post by winzip on 2012-04-25
> **matt_symes said:**
> Hi

Not sure why. Here is a revised version of your script. 

It calculates the date once, stores its value in curr_date and reuses its value. It uses mkdir with the p switch to create the parent directories.

I added some comments as to what i thought you were trying to do.

```

#!/bin/bash

# Get the date
curr_date=$(date +%e-%B-%Y)

# Dump date as test. REMOVE WHEN VERIFIED DATE IS CORRECT.
echo ${curr_date} > ~/curr_date_test 
echo "/home/user/DB_BACKUP/${curr_date}.zip" >> ~/curr_date_test

# Make the backup folders 
mkdir -p /home/user/DB_BACKUP/${curr_date}/Alfresco 

# Get dump of test database 
mysqldump -P 3306 -h 192.168.2.85 -u root -proot test_db > /home/user/DB_BACKUP/${curr_date}/test_db.sql 

# Copy revelent data 
cp -r /home/user/alfresco/alf_data/backup-lucene-indexes /home/user/DB_BACKUP/${curr_date}/Alfresco/ 

# Dump main database 
mysqldump  -P 3306 -h 192.168.2.85 -u alfrescouser -palfrescouser alfresco >/home/user/DB_BACKUP/${curr_date}/alfresco.sql 
 
# Copy extra files. 
cp -r /home/user/alfresco/alf_data/contentstore* /home/user/DB_BACKUP/${curr_date}/Alfresco/ 
 
# Zip up files 
/usr/bin/zip -9 -r /home/user/DB_BACKUP/${curr_date}.zip /home/user/DB_BACKUP/${curr_date} 

# Clean up. 
rm -rf /home/user/DB_BACKUP/${curr_date}
```This will check the date is being created correctly.

```
cat ~/curr_date_test
```Try it and see how it works on your system.

Kind regards

what   does  [COLOR=Red]**~**[/COLOR]   means  in  "[COLOR=Red]**~**[/COLOR]/curr_date_test"  ?   

I'll  give it a try . But I dont understand what does "[COLOR=Red]**~**[/COLOR]"  doing here ?

---

### Post by matt_symes on 2012-04-25
Hi

```
~/
```

 is a typing shortcut to your home directory so you don't have to type

```
/home/user/.....
```

Kind regards

---

### Post by winzip on 2012-04-25
Looks like  curr_date  is not evaluated.

see this  small testing result..

#!/bin/bash

# Get the date
curr_date=$(date +%e-%B-%Y)

#First Create the folder that will contain the backup

mkdir  -p /home/user/DB_BACKUP/$(curr_date)
echo 1. made directory /home/user/DB_BACKUP/$(curr_date) >backup.log



Log file:
---------
$ cat backup.log

1. made directory /home/user/DB_BACKUP/



Did you notice that  the $(curr_date)  is not evaluated here ?

I also checked DB_BACKUP folder..... its empty.

whats the reason ?  how do you fix it ?

---

### Post by matt_symes on 2012-04-25
Hi

Please read my posts properly.

It's not.... 

```

mkdir  -p /home/user/DB_BACKUP/$[COLOR=Orange]**(**[/COLOR]curr_date[COLOR=Orange]**)**[/COLOR]
echo 1. made directory /home/user/DB_BACKUP/$[COLOR=Orange]**(**[/COLOR]curr_date[COLOR=Orange]**)**[/COLOR] 
```but

```
mkdir  -p /home/user/DB_BACKUP/$[COLOR=Red]**{**[/COLOR]curr_date**[COLOR=Red]}[/COLOR]**
echo 1. made directory /home/user/DB_BACKUP/$[COLOR=Red]**{**[/COLOR]curr_date[COLOR=Red]**}**[/COLOR] 
```to access the value stored in curr_date.

curr_date=$(date +%e-%B-%Y) stores the date in curr_date by running the date command in a subshell and putting the return value in curr_date. 

You don't use a sub shell $(..)  to access the value stored in curr_date though. You use ${..}.

What else did you modify in the script ?

Kind regards

---

### Post by winzip on 2012-04-26
Thanks for the correction. 

However, I  have narrowed down the problem area.  Here is a small test which replicates the  zip issue.  Please check this small script and look at its output.  no zip is created .




backup.sh
------------

#!/bin/bash
# Get the date
curr_date=$(date +%e-%B-%Y)
#Make a folder that stores the alfresco backup

mkdir -p /home/user/DB_BACKUP/${curr_date}/Alfresco


#Backup contentstore

cp -r /home/user/alfresco/alf_data/contentstore /home/user/DB_BACKUP/${curr_date}/Alfresco/



#zip the entire Backup folder of this run

/usr/bin/zip -9 -r /home/user/DB_BACKUP/${curr_date}.zip /home/user/DB_BACKUP/${curr_date}




Result:
------------

user@mmc:~/DB_BACKUP$ ls -l
total 20
drwxr-xr-x 3 user user  4096 2012-04-26 12:16 26-April-2012
-rw------- 1 user user 15336 2012-04-26 12:16 zij4hdZu



Do you see the problem  ?  how do I fix now ?

---

### Post by matt_symes on 2012-04-26
Hi

I can see the problem Winzip but it is not something i can replicate on any of my machines and, therefore, is extremely hard to debug from here.

Have you tried the script in a test only environment like i did ? 

Using dummy files and not the contents of the sqldump files ?

That is what i would do next to see if the problem is somehow related to one of the commands you are running in the script.

Does the zip file get generated correctly if you hard code the zip file name in the script  and not use the date ?

```
#zip the entire Backup folder of this run

/usr/bin/zip -9 -r /home/user/DB_BACKUP/**test.zip** /home/user/DB_BACKUP/${curr_date}
```You need to run tests to narrow down the problem.

Kind regards

---

### Post by winzip on 2012-04-26
> **matt_symes said:**
> Hi

  
Using dummy files and not the contents of the sqldump files ?



There is no sqldump in the test script I posted.  Its just a file copy command.


> 
Does the zip file get generated correctly if you hard code the zip file name in the script  and not use the date ?

```
#zip the entire Backup folder of this run

/usr/bin/zip -9 -r /home/user/DB_BACKUP/**test.zip** /home/user/DB_BACKUP/${curr_date}
```You need to run tests to narrow down the problem.
Ok. I tested this also ...see the revised   backup.sh script and its output


```
#!/bin/bash
# Get the date
curr_date=$(date +%e-%B-%Y)
#Make a folder that stores the alfresco backup
echo 4. creating directory /home/user/DB_BACKUP/${curr_date}/Alfresco for storing alfresco backups >>backup.log
mkdir -p /home/user/DB_BACKUP/${curr_date}/Alfresco
echo 5. made directory /home/user/DB_BACKUP/${curr_date}/Alfresco >> backup.log

#Backup contentstore
echo 10. backing up contentstore of  /home/user/alfresco/alf_data/contentstore to /home/user/DB_BACKUP/${curr_date}/Alfresco/ >>backup.log
cp -r /home/user/alfresco/alf_data/contentstore /home/user/DB_BACKUP/${curr_date}/Alfresco/
echo 11. backup of contentstore complete >>backup.log



#zip the entire Backup folder of this run
echo 13. zipping up the folder /home/user/DB_BACKUP/${curr_date} to /home/user/DB_BACKUP/${curr_date}.zip >>backup.log
/usr/bin/zip -9 -r /home/user/DB_BACKUP/**test.zip** /home/user/DB_BACKUP/${curr_date}
echo 14. zip done >> backup.log




user@mmc:~/DB_BACKUP$ ls -l
total 20
drwxr-xr-x 3 user user  4096 2012-04-26 17:08 26-April-2012
-rw------- 1 user user 15336 2012-04-26 17:08 ziS3U111

```

Do you find the root cause  ?

by the way ,  cp  and zip ....is there any known issue ?

---

### Post by matt_symes on 2012-04-26
Hi

> Do you find the root cause  ?

I'm a bit stumped by this one. I cannot understand why it's not working from cron.

Can we check you crontab entry to make sure nothing is wrong there.

```
crontab -l
```

> by the way ,  cp  and zip ....is there any known issue ?

Not that i'm aware off :confused:

Kind regards

---

