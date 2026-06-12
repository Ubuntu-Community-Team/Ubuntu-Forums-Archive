---
title: "Bash scripting problem with vervobe cp"
date: 2009-10-29
forum: General Help
---

### Post by - Lo - on 2009-10-29
Hello everybody!

I have a problem with the following script which I would use with cronjob:

 ```
#!/bin/bash

echo ### Daily backup cronjob ###
date
cp -v -r dly_backup/* nas/my_nas/
echo #############################
```In cronjob I insert the following command:

```
./dly.sh >> backup_log 2>&1
```All works fine apart from the redirection...in case of error the error messages are written in the backup_log file, but the cp messages (which run with the -v option) are not redirected...

Can someone help me? :)

Thanks a lot!

- Lo -

---

### Post by alphaniner on 2009-10-29
Instead of ```
./dly.sh >> backup_log 2>&1
```

try

```
./dly.sh 2>&1 >> backup_log
```

Edit: Doh!  That doesn't redirect the errors to the file :/

Edit2: This should work:

Script:
```
#!/bin/bash

echo ### Daily backup cronjob ###
date
cp -v -r dly_backup/* nas/my_nas/ **2>&1**
echo #############################
```

Crontab command:
```
./dly.sh >> backup_log
```

---

### Post by - Lo - on 2009-10-29
Hey alphaniner,

first of all thanks a lot for the reply, but it does not work....in the backup file I found only the "date" output, but not the copied files....

This is really strange because this happen only for that specific folder...I have created a dummy folder with dummy files and a dummy log file and all works as expected...

Can this problem be related to the fact that the /backup root folder is managed with samba? I don't think so but I cannot find any logical explanation for this behavior...

---

### Post by alphaniner on 2009-10-29
That is weird.  I don't think the samba issue should matter either.  The only potential issue I can see is your use of relative paths.

---

### Post by - Lo - on 2009-10-29
in my cronjob I have used absolute paths, but I cannot post them because contains sensitive data...

---

### Post by alphaniner on 2009-10-29
I'm fresh out of ideas.  Can you edit the title of the thread?  Maybe 'cron output redirection problem' would be more appropriate, could get more views.

---

### Post by - Lo - on 2009-10-29
But I get this problem even if I launch the command manually from the command line...aaaaaagrh....

---

### Post by - Lo - on 2009-11-02
Ok, I have solved the mistery....it seems that the output is written to the log file whenever the command completes....I don't know why...

Are there someone who knows why this happen?

Thanks a lot

- Lo -

---

