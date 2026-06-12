---
title: "Samba 4 won't run in Ubuntu 11.10"
date: 2011-11-16
forum: General Help
---

### Post by loren41 on 2011-11-16
I have successfully installed Samba 3.5.11 in Ubuntu 11.10.  When I press the app button, I see no response.  How should I begin researching this problem (log files, etc.)?  Samba had been running successfully with Ubuntu 11.04 but quit after upgrading to Ubuntu 11.10.

---

### Post by naicidrac on 2011-11-20
exact same issue here.  I launch samba and nothing happens.  since I upgraded to 11.10 my MAC and PCs cannot connect to my Ubuntu sever.

---

### Post by redmk2 on 2011-11-20
> **naicidrac said:**
> exact same issue here.  I launch samba and nothing happens.  since I upgraded to 11.10 my MAC and PCs cannot connect to my Ubuntu sever.

What do you mean by: *I launch samba*?  When I boot up any of my machines the samba daemons (*smbd* and *nmbd* )are started.  Are you saying that these 2 processes are not running?

From the Ubuntu host, please post the output of ```
pgrep -l mbd
```

From that same host post the output of ```
smbtree -d3
```

Is it possible that you can't browse to the share, but are still be able to connect? Try to connect from a Windows PC like this from the CMD prompt```
net view <ipaddress of share>
```

---

### Post by redmk2 on 2011-11-20
> **loren41 said:**
> I have successfully installed Samba 3.5.11 in Ubuntu 11.10.  When I press the app button, I see no response.  How should I begin researching this problem (log files, etc.)?  Samba had been running successfully with Ubuntu 11.04 but quit after upgrading to Ubuntu 11.10.

Are you running Samba 3.5 or Samba 4?  What *app button *are you referring to?

---

