---
title: "Network manager &quot;enable networking&quot; checkbox got disabled after updation ubuntu 10.10"
date: 2011-04-01
forum: General Help
---

### Post by bhupinderjitbawa on 2011-04-01
I m using ubuntu 10.10 , after updation the network manger is unable to establish a gprs conneciton with the mobile...and dosnot showing anything under network manager.When i right click on the network manager icon its **Enable networking** checkbox is disabled and i m unable to tick it...how to resolve it..i m not able to google it..
how to enable "Enable networking" checkbox,i m unable to click on it.?its faded gray..

---

### Post by PlankEyeWilly on 2011-04-01
I also have the same issue.  Since my networking seems to be working properly I never really noticed the issue until today, when I was trying to set up and test ICS. 

 I am not sure if this is related:

```
tommy@nc6230:~$ ps -edf | grep nm-app
tommy     1699  1568  0 16:32 ?        00:00:00 nm-applet --sm-disable
tommy     1980  1767  0 16:36 pts/0    00:00:00 grep --color=auto nm-app
```

What is the --sm-disable switch at the end of my running nm-applet process?

---

