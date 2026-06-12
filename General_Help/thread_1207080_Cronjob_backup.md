---
title: "Cronjob backup"
date: 2009-07-07
forum: General Help
---

### Post by shang1 on 2009-07-07
Hello all,
I am trying to make a shell script which will backup my important Documents every half hour using cron.

Ideally, I want the script to backup the directory, with the name, date and time. I would also like it to only keep the latest 5 backups, (so as to save space/cluster). Namely, when there is >5 backups in the directory the oldest back up will be removed.

This is what I have so far (which is erroneous):
```

#!/bin/bash
today=$(date '+%d_%m_%y')
tar czf /home/riley/Documents/backup_"$today".tar.gz /var/doc_backup/  

```

If anyone can help me I would greatly appreciate it.
Thanks.

---

### Post by maheshasolkar on 2009-07-07
Following command will remove all '.gz' files from /backup/storage/dir that are older than 200 minutes. Which should be little more than 5 backups if you run a backup every half hour: 
```

  % find /backup/storage/dir -name "*.gz" -cmin +200 | xargs rm -f
```

You should test that command carefully before you incorporate it into your cron script.

Hope this helps.

---

### Post by shang1 on 2009-07-07
great, thanks. I came up with this.

```
#!/bin/bash
find /var/doc_backup/ -name "*.tar.gz" -cmin +149 | xargs rm -f
time=$(date)
tar czf /var/doc_backup/"$time".tar.gz /home/riley/Documents/Code  

```

however, the find/rm section does not work - any ideas?

---

### Post by maheshasolkar on 2009-07-08
If you run the following command in the terminal, what does it return?

```
  % find /var/doc_backup/ -name "*.tar.gz" -cmin +149
```

---

### Post by shang1 on 2009-07-08
```
riley@riley-laptop:~$ find /var/doc_backup/ -name "*.tar.gz" -cmin +149
/var/doc_backup/Wed Jul  8 13:10:50 EST 2009.tar.gz
/var/doc_backup/Wed Jul  8 13:10:02 EST 2009.tar.gz
/var/doc_backup/Wed Jul  8 13:06:59 EST 2009.tar.gz
/var/doc_backup/Wed Jul  8 13:10:13 EST 2009.tar.gz
/var/doc_backup/backup-Wed Jul  8 13:06:41 EST 2009.tar.gz

```

So it finds the correct files, but the | xargs rm -f 'part' does not work, any idea why this could be?

---

### Post by maheshasolkar on 2009-07-08
May be because the file names have spaces in them? Can you try this:

```
  find /var/doc_backup/ -name "*.tar.gz" -cmin +149 | sed -e s/' '/'\\ '/g | xargs rm -f

```

---

### Post by shang1 on 2009-07-08
great - it works perfectly. Thanks for the assistance.

---

