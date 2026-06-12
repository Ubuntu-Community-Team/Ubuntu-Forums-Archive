---
title: "How to restart process once a day"
date: 2009-09-07
forum: General Help
---

### Post by kristapsb on 2009-09-07
Hello,

I have a little .sh script, which runs on bootup:

```
#!/bin/bash

cd /root/agony/

screen -d -m ./hlds_run -binary ./hlds_i686 -game cstrike +map de_dust +port 27015 -insecure -master +maxplayers 21 +exec server.cfg +exec amxx.cfg

cd /root/dr/

screen -d -m ./hlds_run -binary ./hlds_i686 -game cstrike +map deathrun_4life +port 27017 -master -insecure +maxplayers 21 +exec server.cfg +exec amxx.cfg

```As you can see, this script runs two processes. I am wondering is there anyway to quit un re-start these processes once a day?

OS - Ubuntu Server

Thanks!

---

### Post by fishy6969 on 2009-09-07
Have a go with cron. Have a look at the wiki here

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

Regards

---

### Post by kristapsb on 2009-09-07
Thanks, but can anyone help me with this script?

---

### Post by fishy6969 on 2009-09-07
Remove all the 'screen' stuff ie -

```
#!/bin/bash

cd /root/agony/
./hlds_run -binary ./hlds_i686 -game cstrike +map de_dust +port 27015 -insecure -master +maxplayers 21 +exec server.cfg +exec amxx.cfg

cd /root/dr/
./hlds_run -binary ./hlds_i686 -game cstrike +map deathrun_4life +port 27017 -master -insecure +maxplayers 21 +exec server.cfg +exec amxx.cfg
```

Make sure the script is executable (chmod +x *scriptname*) then run crontab -e and add the script eg

```
01 04 * * * /usr/bin/somedirectory/somecommand
```

---

