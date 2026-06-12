---
title: "croning a root job"
date: 2011-07-05
forum: General Help
---

### Post by kaykav on 2011-07-05
HI
     I'm sought of in a dillema. I want to use crontab to run updates and upgrades everyday, so I thought to use crontab.As follows: 
   00 08 * * * sudo apt-get update && sudo apt-get upgrade && date>> ~/whenups
   (If the cron job is ran a date-stamp is put into a file called whenups.)
 The only problem is ,to run a sudo command I have to enter my password. Which takes away the 'automatic' idea of cron. So the cron job will not run,without my password being entered at 8am every day. How do I get around this problem?   Thanks

---

### Post by SeijiSensei on 2011-07-05
> **kaykav said:**
> HI
     I'm sought of in a dillema. I want to use crontab to run updates and upgrades everyday, so I thought to use crontab.As follows: 
   00 08 * * * sudo apt-get update && sudo apt-get upgrade && date>> ~/whenups
   (If the cron job is ran a date-stamp is put into a file called whenups.)
 The only problem is ,to run a sudo command I have to enter my password. Which takes away the 'automatic' idea of cron. So the cron job will not run,without my password being entered at 8am every day. How do I get around this problem?   Thanks

Use "sudo crontab -e" to edit root's crontab (with vi by default; for a different editor first run the command "export EDITOR=nano" or whatever your favorite text editor might be).

The other option is to edit /etc/crontab and create an entry like this:

```
00 08 * * *  root apt-get update && sudo apt-get upgrade && date>> ~/whenups
```

which will run the commands as the root user.

---

### Post by seawolf167 on 2011-07-05
You should make a BASH script with the commands you want to run then point the crontab to that script while running it as root, else in your command posted the script is trying to run as the user "sudo" the command apt-get...

Take a look at the crontab link in my signature for more information on proper formatting for the scripts.

Since you are trying to automatically install updates, [this link ]("https://help.ubuntu.com/community/AutomaticSecurityUpdates")will be more helpful for you. It shows you how to configure to automatically apply security updates.

---

### Post by holiday on 2011-07-05
You need to log into root and put the crontable in root's space.

---

### Post by wojox on 2011-07-05
Create the cron job as root. ;)

EDIT: You guys are quick

---

### Post by kaykav on 2011-07-05
Well ..thank you all for your replies.I'll try it all...

---

### Post by kaykav on 2011-07-05
One more thing....  When an 'upgrade' is in progress there comes a point where the process 'ask' if I want to continue. Once again 
I have to interact (y) to continue , but I can't do that automatically. So the upgrade will not happen. The update will,but not the upgrade.....  I think!......thanks again

---

### Post by Habitual on 2011-07-05
```
apt-get -y 
```

---

### Post by kaykav on 2011-07-06
apt-get -y
That's a good command.Didn't know it existed...thanks

---

