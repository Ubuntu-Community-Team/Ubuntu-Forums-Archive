---
title: "output redirect with crontab"
date: 2010-09-16
forum: General Help
---

### Post by Ebener on 2010-09-16
My Problem: The output redirection auf a script works if the script is  called in the terminal but not when its called via crontab.

My Situation: I have 2 scripts:
~/backup1
```
echo backup a to c
rsync -a -v --progress --delete --exclude=.Trash-1000 /path/a/ /path/c/backup/
echo backup b to c
rsync -a -v --progress --delete --exclude=.Trash-1000 /path/b/ /path/c/backup/
```~/backup2
```
if [ -d "/path/c/backup" ]
then
    TODAY=`date +%Y-%m-%d`
    echo "backup run $TODAY">/home/user/Desktop/backup-$TODAY
    echo "started `date`">>/home/user/Desktop/backup-$TODAY
    /home/user/backup1 &>> /home/user/Desktop/backup-$TODAY
    echo "finished `date`">>/home/user/Desktop/backup-$TODAY
fi
```If I run backup2 via terminal the content of /home/user/Desktop/backup-2010-09-16 is
```
backup run 2010-09-16
started Di 16. Sep 10:01:01 CEST 2010
backup a to c
rsync: opendir "/some/path" failed: Permission denied (13)
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]
backup b to c
finished Do 16. Sep 10:19:01 CEST 2010
```but if backup2 is called by crontab the contents of the file are
```
backup run 2010-09-16
started Di 16. Sep 10:21:01 CEST 2010
finished Do 16. Sep 10:21:01 CEST 2010
```

---

### Post by Ebener on 2010-09-21
Solved it by changing
```
/home/user/backup1 &>> /home/user/Desktop/backup-$TODAY
```to
```
/home/user/backup1 >> /home/user/Desktop/backup-$TODAY 2>&1
```

---

