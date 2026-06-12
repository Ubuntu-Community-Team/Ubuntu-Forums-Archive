---
title: "problem with cron when runing ssh client"
date: 2011-08-05
forum: General Help
---

### Post by irakla7777777 on 2011-08-05
i wrote script for ssh reverse connection :

spawn ssh  -R 2210:localhost:22 [email]user@XX.XX.XX.XX[/email]
 
  expect "password:"
    
   send "MYPASSWORD\n" 
    
      interact

when i run this from terminal , command executed succesfuly.

but when i run this from cron , it does not work. 

my crontab looks like this :

*/1 *   * * *   root       /home/user/Desktop/script.sh

---

### Post by Kira_Belka on 2011-08-05
*/1 * * * * root /home/user/Desktop/sh script.sh

---

### Post by btindie on 2011-08-05
Make sure the script has got the eXecutable bit set (chmod +x script.sh)

Also, is that cron job scheduled under your own user account? If so then you shouldn't specify the user for it to run as, you can't have it run as root. Instead, change the cron entry to

```
*/1 *   * * * /home/user/Desktop/script.sh
```It's only the master crontab (/etc/crontab) and in /etc/cron.d that you need to specify the username. See "man 5 crontab"

---

### Post by irakla7777777 on 2011-08-05
content of this script is :

```

#!/usr/bin/expect
spawn ssh -R 2210:localhost:22 user@XX.XX.XX.XX

expect "password:"

send "MYPASSWORD\n" 

interact



```

cron does not run it as background process. 

i have tested it with wireshark , and ssh protocol runs in every minut. and it disconnect immediately  ... so no permission problem ...

HOW TO GET IT WORK ?

---

