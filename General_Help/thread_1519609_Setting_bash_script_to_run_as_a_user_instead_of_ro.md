---
title: "Setting bash script to run as a user instead of root at boot up"
date: 2010-06-28
forum: General Help
---

### Post by cryptodan on 2010-06-28
I want to create a script that will allow me to run my HLDS Server as user hlds so it isn't running as root on boot up. This will be placed in the rc.local command via path to the script which will be /home/hlds/half-life

So what do I need to put in the script to set the script to run as user HLDS?

---

### Post by Bachstelze on 2010-06-28
```
su -c "command" user
```

Or see if your programs can be run as another user with an argument on the command line.

---

