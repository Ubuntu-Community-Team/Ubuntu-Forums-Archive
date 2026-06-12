---
title: "Trying to write this script but having problems."
date: 2011-01-15
forum: General Help
---

### Post by green351 on 2011-01-15
Hi, I'm running Lucid Lynx and having the following issue:

I found [this]("http://www.labnol.org/software/print-files-on-linux/17841/") wonderful post about how to set up my computer to automatically check a "PrintQueue" folder inside my Dropbox folder, allowing me to be able to print from any device/computer that has access to my Dropbox, to the printer connected to my Ubuntu machine.

I wrote the shell script from the link in gedit, saved it in my home folder as "printingscript", gave myself permission to execute, then tried ./printingscript in the terminal.  Unfortunately I just get an error back saying

```
./printingscript: line 9: syntax error near unexpected token `lpr'
./printingscript: line 9: `lpr -r ${PrintQueue}/${PrintFile};'

```

I don't really know anything about writing code which is why I don't know how to fix the problem.  For reference my shell script looks exactly like the following:

```
#!/bin/bash

export PrintQueue="/root/Dropbox/PrintQueue";

IFS=$'\n'

for PrintFile in $(/bin/ls -1 ${PrintQueue}) do

   lpr -r ${PrintQueue}/${PrintFile};

done

```

As an aside I was going to use gnome-scheduler to have it run the script every minute.  Am I correct to assume that the correct command to use would be ./printingscript?

Ok thanks in advance to anybody who can help.

---

### Post by sisco311 on 2011-01-16
Check out a good Bash guide:
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

The loop you use is one of the most common mistakes BASH programmers make:
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

Try something like:
```
#!/usr/bin/env bash

PrintQueue="/root/Dropbox/PrintQueue"

cd "$PrintQueue"
for file in *; do
  lpr -r "./$file"
done
```

EDIT:
In gnome-schedule (which is a GUI for configuring a users' cron) you have to use the full path to the script (/home/username/script-directory/script-name).

Or simply edit the crontab file from a terminal:
```
crontab -e
```
append it with:
```
* * * * * /home/username/script-directory/script-name
```

EDIT2:
According to **man lpr**, lpr accepts multiple files as an argument. So adding something like:
```
* * * * * /usr/bin/lpr -r /root/Dropbox/PrintQueue/*
```to the crontab file should do the trick.

---

### Post by green351 on 2011-01-16
> **sisco311 said:**
> Check out a good Bash guide:
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

The loop you use is one of the most common mistakes BASH programmers make:
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

Try something like:
```
#!/usr/bin/env bash

PrintQueue="/root/Dropbox/PrintQueue"

cd "$PrintQueue"
for file in *; do
  lpr -r "./$file"
done
```



Thanks so much for the resources.  I'm excited to look into it.  As for the script you wrote, it returns an error of 

```
./printingscript2: line 5: cd: /root/Dropbox/PrintQueue: Permission denied

```

then it tries to print everything in my home folder.  Should I be executing the script using sudo?  Maybe my script should be somewhere else?  It is currently in my "username" folder, and the path to my PrintQueue is /home/username/Dropbox/PrintQueue.

---

### Post by izzyanut on 2011-07-15
I get the exact same problem with permission but instead of deleting the printed file it deletes the script and leave the file in DropBox.

---

### Post by izzyanut on 2011-07-16
Fixed it. change PrintQueue="/root/Dropbox/PrintQueue" to /home/username/Dropbox/PrintQueue and use gnome-schedule to run it every minuet. to do so simply add the command as /home/username/script-location/printscript-filename.sh then when you want to run print just dump into Dropbox. This is what my code looks like (Please not im running multiple instances of Dropbox so please change your Print Queue folder location:

```
#!/usr/bin/env bash

PrintQueue="/home/joe/.dropbox-alt/Print/Dropbox/PrintQueue"

cd "$PrintQueue"
for file in *; do
  lpr -r "./$file"
done
```

---

