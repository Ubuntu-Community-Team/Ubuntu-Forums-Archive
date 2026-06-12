---
title: "rsync bash script different in cron?"
date: 2010-02-19
forum: General Help
---

### Post by aaronp on 2010-02-19
Hi all,

I've got a bash script that uses rsync via SSH to back up data from a remote webserver.
This script works fine when I run it myself but when it runs as a cron  job I get the following error:

```
2010/02/20 08:15:01 [6786] Unexpected remote arg: user@www.server.com:~/www
2010/02/20 08:15:01 [6786] rsync error: syntax or usage error (code 1) at main.c(1219) [sender=3.0.6]
```

(note I changed my SSH username and server name in the above code, it is correct in the script)

Do I need to change the script or the cron line at all?
Here's the cron line below, and it's in my cron (i.e. not root's)

```
00 4 * * 6 /media/store/webbackup/rsyncbackup.sh

```

thanks

---

### Post by rnerwein on 2010-02-19
hi
i don't know if this can be the reason.
i think you are using the "bash" on the command line when you run your script.
the same is the environment setting - you have to set it inside your script.
cron is using the default system shell "/bin/sh". that means that if you have a bash specific command syntax in your script you have to have the "#!/bin/bash" at the first line in your script. 

ciao

---

### Post by aaronp on 2010-02-19
Thanks for the response, but I've already got the bash line at the top of the script. thanks

---

### Post by falconindy on 2010-02-19
You'll need to post the script.

---

### Post by gmargo on 2010-02-19
> **aaronp said:**
> rsync via SSH

And how is SSH getting it's validation?  Are you relying on a running **ssh-agent** process?  That won't work from cron.

---

### Post by aaronp on 2010-02-19
> **falconindy said:**
> You'll need to post the script.

Ok thanks, here is the relevant section. I can post the entire thing if required.

```

folder=`/bin/date +%Y%m%d`
dirpath="/media/store/backup/backups/"
logpath="/media/store/backup/logs/"

#retrieve most recent directory name from file
oldname=`cat /media/store/backup/backups/latest`

#set paths and filenames to be used in script
newfolder=$dirpath$folder
oldfolder=$dirpath$oldname
reportfile=$logpath"log"$folder".txt"
dbfolder="/media/store/backup/sql"

cp -al $oldfolder $newfolder
echo $folder > $dirpath"latest"

rsync -r --delete --log-file $reportfile -u --exclude *.mp3 --exclude *.avi --rsh="ssh -p2222" user@www.server.com:~/www $newfolder
rsync -r --delete -u --rsh "ssh -p2222" user@www.server.com:~/sql $dbfolder

```

---

### Post by falconindy on 2010-02-19
Not immediately obvious which rsync invocation the error is in. Can you pin that down by commenting out the lines one at a time and running it via cron?

---

### Post by Slim Odds on 2010-02-19
Actually, it is.

~ will expand to something completely different depending on the environment (which will be different between cron and your user account).

---

### Post by aaronp on 2010-02-19
I think the error is clearly pointing to the first rsync invocation, because it refers to ~/www and not ~/sql

But ~ expands to the user account on the server, not on my machine. 
Shouldn't this be referring to the home directory of the user on the server? (i.e. the script should not interpret this as meaning my local user home directory, and it doesn't when I invoke the script manually) 

Is cron evaluating the ~ before sending it to rsync?
I doubt it because then rsync would return a full pathname in the error and not ~?

---

### Post by falconindy on 2010-02-19
Mmm, that could very well be it. You can get the home directory of the login user by omitting the ~/. In other words, try:
```
rsync -r --delete --log-file $reportfile -u --exclude *.mp3 --exclude *.avi --rsh="ssh -p2222" user@www.server.com:www $newfolder
```

---

### Post by aaronp on 2010-02-19
> **falconindy said:**
> Mmm, that could very well be it. You can get the home directory of the login user by omitting the ~/. In other words, try:
```
rsync -r --delete --log-file $reportfile -u --exclude *.mp3 --exclude *.avi --rsh="ssh -p2222" user@www.server.com:www $newfolder
```

Thanks, that worked with manual invocation again, but still the same issue when run from cron:

```
2010/02/20 14:09:01 [8032] Unexpected remote arg: user@www.server.com:www
2010/02/20 14:09:01 [8032] rsync error: syntax or usage error (code 1) at main.c(1219) [sender=3.0.6]
```

---

### Post by jobix on 2010-02-19
Do any of the files that you're trying to sync have whitespaces in their names? Can you try your script and run it with just a couple of files with no whitespaces or special characters in their name?

---

### Post by gmargo on 2010-02-20
You have omitted necessary single quotes around your exclude patterns.  But I doubt that is the cause of your problem.

```

rsync -r --delete --log-file $reportfile -u --exclude **'*.mp3'** --exclude **'*.avi'** --rsh="ssh -p2222" user@www.server.com:www $newfolder

```

---

### Post by aaronp on 2010-02-20
> **gmargo said:**
> You have omitted necessary single quotes around your exclude patterns.  But I doubt that is the cause of your problem.

```

rsync -r --delete --log-file $reportfile -u --exclude **'*.mp3'** --exclude **'*.avi'** --rsh="ssh -p2222" user@www.server.com:www $newfolder

```

Excellent! thanks gmargo (and everyone else who suggested solutions)
That worked. 

Any ideas on why that is required when the script runs via cron but not when manually invoked?

Aaron

---

### Post by gmargo on 2010-02-20
Without quotes, the shell is doing the pattern expansion.  So it depends on what directory you are in, and if there are matching files there.  With quotes, rsync gets the pattern and not the expanded file list that the shell would generate.

---

### Post by jobix on 2010-02-20
> **gmargo said:**
> Without quotes, the shell is doing the pattern expansion.  So it depends on what directory you are in, and if there are matching files there.  With quotes, rsync gets the pattern and not the expanded file list that the shell would generate.

Good catch. Same reason why I asked him about white spaces in the filenames. To escape them you may need the "\" characters or they might get misinterpreted.

---

