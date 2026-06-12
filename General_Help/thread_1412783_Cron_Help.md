---
title: "Cron Help"
date: 2010-02-21
forum: General Help
---

### Post by skeeterxb on 2010-02-21
New to Ubuntu and Cron, hoping someone can help on a new challenge. 
 
I made a simple file and coverted it to a script with the chmod command. The script will backup from one folder to another, pretty simple script. I wanted to start using cron to get it do it on a schedule. I created a cron job as a txt file and then ran crontab mycron.txt (file consists of 30 10 * * * /home/myname/bin/backup), it directs it to run the backup script i created. Seems the job isnt running for some reason and i dont know why, any idea's? Is there some step i am missing in getting cron to do the job?
 
Thanks in advance.

---

### Post by amac777 on 2010-02-21
It might be helpful if you post both the script and the output of: 

```
crontab -l
```

With that information somebody should be able to see what the problem is.

---

### Post by cjhabs on 2010-02-21
To get changes to cron to kick in automatically, use "crontab -e" to edit the cron file. This will use the default editor as defined by the EDITOR environmental variable. I have "export EDITOR=gedit" defined in my .bashrc to call gedit - not sure what you'll get otherwise.

---

### Post by skeeterxb on 2010-02-21
Here is some more information from 
 
crontab -l
 
It says 30 17 * * * root /home/rob/bin/backupfiles
 
Hope this helps, let me know if you need anything else from my end.  
 
Thanks
Rob

---

### Post by amac777 on 2010-02-21
Were you logged in as root or using sudo privledges when you ran 'crontab -l'? If not, I don't think your user rob's crontab can run scripts as the root user. So you may need to edit the crontab again and remove the word 'root'.

---

### Post by skeeterxb on 2010-02-21
Thanks for the advice. 
 
I was logged in as myself as rob, so do you think i should create the cron file again as sudo and that should do it?
 
something like 
 
sudo crontab mycron.txt
 
This should bring the script to cron and allow it run as sudo correct?

---

### Post by skeeterxb on 2010-02-21
You were right my friend, it worked after running it as sudo.

---

### Post by bawig1 on 2010-02-22
Hi,

I am also having problems with cron. I am trying to get a program to start at midnight. I am logged in my usual account  The output of my crontab file is;

```

# m h  dom mon dow   command
  0 0  *   *   *     /usr/bin/transmission

```


I have tried a  couple of different times with 'm' and 'h' but transmission doesn't run. Am I using cron in the correct manner? To get a program to run at a certain time?

Thanks,

Brett

---

### Post by bawig1 on 2010-02-22
I found the following entry in syslog;

```

Feb 23 09:26:01 district9 CRON[4916]: (brett) CMD (/usr/bin/transmission)

```Does this mean that transmission is running? because the gui is not showing. Have I got the wrong idea about cron?

---

