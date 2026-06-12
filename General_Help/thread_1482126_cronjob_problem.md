---
title: "cronjob problem"
date: 2010-05-13
forum: General Help
---

### Post by vereker on 2010-05-13
Hi guys

I have been trying to run my cronjob with a .sh file but it doesnt not seem to be working. I have tried the following code

* * * * * /home/jamie/Documents/my.sh
* * * * * sleep 30; /home/jamie/Documents/my.sh


# /0.2 * * * *   /home/jamie/Documents/my.sh

Trying to get the cronjob to run every thirty seconds but nothing is happening, i have edited it using crontab -e, nano cronjob, nothing seems to work.

Please help!!

Thank you very much

---

### Post by mister_p_1998 on 2010-05-13
Whats in the contents of my.sh?
does it run manually ok?
Steve

---

### Post by vereker on 2010-05-13
Hi there

Well basically I am running the HCI tool scan and outputting the MAC addresses to a MySQL database and want to keep it running so that the MAC addresses and constantly being added to the database i.e. keep running the my.sh file, the contents of which are:

hcitool scan | awk '{if($1 != "Scanning"){print $1 " " $2}}' > result.txt
./php.sh

Thanks again

---

### Post by gmargo on 2010-05-13
Using cron to create a loop seems backwards to me.  Why don't you put the loop inside the shell script?

---

### Post by vereker on 2010-05-13
Okay, how would you set it for every minute in a shell script?

Thanks

---

### Post by MichealH on 2010-05-13
Explained here... :D

[http://ubuntuforums.org/showthread.php?t=586478](http://ubuntuforums.org/showthread.php?t=586478)

---

### Post by vereker on 2010-05-13
have tried that approach but still no luck?
any other ideas?

thank you

---

