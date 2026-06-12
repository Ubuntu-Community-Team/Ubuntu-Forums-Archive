---
title: "Restart script for Davmail"
date: 2012-09-24
forum: General Help
---

### Post by sullivanjc on 2012-09-24
I am using Davmail on Ubuntu 12.04.  The problem is my company's outlook web access is timing out the connection after two hours and I have to close and restart Davmail or I am unable to retrieve mail.  Since I am not always at my PC when this happens, I would like to set up a script that automatically closes and restarts Davmail hourly.   Any way to do this?

---

### Post by raja.genupula on 2012-09-24
Crontab can be used to schedule a job that runs on certain internal .
write a script as
 ```
pkill davmail
davmail 
done

```Then open your terminal and type this ```
crontab -e
``` there at last write below line . 

then write like this 
```
0 */1 * * * /path/to/yourscript.sh
```I am sure that gonna help you .[U]

[SIZE=3]One more solution[/SIZE][/U]

write script like this
```
pkill davmail
davmail
sleep 3600
done
```

save that script as somename for example dav.sh
for the first time ```
chmod +x dav.sh
```
Then now in your terminal 
```
nohup ./dav.sh &
```

---

