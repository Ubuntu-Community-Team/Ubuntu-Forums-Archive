---
title: "cronjob noobie"
date: 2009-06-27
forum: General Help
---

### Post by dswz on 2009-06-27
Hi all!

I've been using ubuntu server edition for quite some time now, everything is nicely documentated and there usualy are enough related posts to find answers.. however this one is getting me mad.. :mad: I must say that i don't know that much about linux.. so hopefully the answer is simple for u guys!

So here's the story.. I created this shell script:

```
#!/bin/sh
echo Backup Started `date` >> /var/log/backups
cd /

if [ -d /home/backups/`date +%w`/ ] ; then
   rm /home/backups/`date +%w`/backup.tar.gz
   echo Overwriting Day `date +%w` >> /var/log/backups
else
   mkdir /home/backups/`date +%w`/
fi

mkdir /home/backups/tmp
mysqldump -u root -pXXXXX DBXXX | gzip > /home/backups/tmp/mysqldump.sql.dump.gz
cp -Rf /var/www /home/backups/tmp
cp -Rf /home/groupoffice /home/backups/tmp
tar czvf /home/backups/`date +%w`/backup.tar.gz /home/backups/tmp
rm -Rf /home/backups/tmp

echo Backup Completed `date` >> /var/log/backups

```and this cronjob (as root):

```

# m h  dom mon dow   command
01 05 * * * cd /home/username/ && ./backup.sh

```then I found something that tells me to add this into the cronjob:

```

HOME=/home/username
PATH=/home/username/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr

```so total is now:

```

HOME=/home/username
PATH=/home/username/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
# m h  dom mon dow   command
01 05 * * * cd /home/username/ && ./backup.sh

```but it refuses to run.. I checked my own log /var/log/backups
and the cronlog but nothing relevant is there.
When I run the command directly as root: 

```

cd /home/username/ && ./backup.sh

```everything works fine...

What Am I missing here? I cant find the answer...!!

Thanks in advance!:P

---

### Post by JKyleOKC on 2009-06-27
Those two lines starting HOME and PATH should be in your script, not in the cronjob itself. They would go after the first line of the script file, just before the "echo" line. The purpose is to set up these two environment variables temporarily so that it works as you expect. And instead of "username" in the two, you should have your own user name so that the cron job acts as if it were you, rather than "root"...

---

### Post by dswz on 2009-06-27
Ok i'll try to put the two lines in the shell script!

The username thing I understand.. just removed them for privacy reasons.
 
The root thing I don't understand.. I would like to write something in the "/home/backups" directory.. but I get an access denied error if I am using my own username (obviously).
How can I write into the /home/backups directory if I am running the cronjob as "username", is there another way instead of using the root cronjob? Should I chown the /home/backups to username:username? 

Thanks for your help!!!!

update: cron is working perfectly now ... as root! Is running the cron as "username" a better idea?

---

### Post by JKyleOKC on 2009-06-27
If it's working as you want it to, then no more changes are needed. Cron jobs run as root and so can read or write most anywhere even without explicit permissions. If you want your username to have access to /home/backup and everything inside, you can modify the permissions on that directory to allow everyone read and write permissions, or can use "chown" to change ownership of the directory and via its -R option, also change ownership of everything it contains.

edit: I see I didn't fully answer your question. While the cron job's environment variables are changing the home directory and the path, for the duration of the job, the job itself is still running as root and thus has the ability to write to /home/backup...

---

