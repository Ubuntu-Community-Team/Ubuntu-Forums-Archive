---
title: "Backup files to .zip?"
date: 2011-02-24
forum: General Help
---

### Post by aflyingturtle on 2011-02-24
I'm looking for an application that will (at periodic intervals) take a backup of a folder and place it in another folder as a .zip. Kind of like the program backup manager,  except instead of having the folder as a plain file, have it backup to a .zip. Also, I would like it to put the files in the folder _Directly_ as the .zip, not with the full filesystem to get to the backup.

---

### Post by seawolf167 on 2011-02-24
The easiest way might be to set a command to run in crontab

say the command

```
tar -cjf file.tar.bz1 files-to-zip
```then edit crontab

```
sudo gedit /etc/crontab
```and add a line like this to run each day at 6am some.command as root

```
00 6 * * * root some.command
```see the link to crontab in my sig for more information on how to format crontab entries.

---

### Post by EPM34 on 2011-02-24
I think I understand what you want but I would suggest looking at a third party App that is designed for data back-up.  We have started using SugarSync and love it.  Besides being a great backup tool it is a repository that can be accessed by others.

---

### Post by kody on 2011-04-26
> **EPM34 said:**
> I think I understand what you want but I would suggest looking at a third party App that is designed for data back-up.  We have started using SugarSync and love it.  Besides being a great backup tool it is a repository that can be accessed by others.

Did you have any issues getting SugarSync up and running? I've installed it via wine and have configured Wine so that "My Documents" refers to a \srv location. I can find and add directories to back up, and the files show as backing up, but then when I click to manage sync folders or view the files online, they don't show up! It's like I've got a file rights issue going on or something. 

Any insight?

---

