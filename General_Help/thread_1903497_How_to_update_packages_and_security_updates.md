---
title: "How to update packages and security updates?"
date: 2012-01-02
forum: General Help
---

### Post by houmank on 2012-01-02
Hi,

I did an SSH into my Ubuntu Server today and it says 

37 packages can be updated.
31 updates are security updates.

How can I do an update?

I tried this without any success:

```
sudo apt-get update
```

Many Thanks,
Houman

---

### Post by Frogs Hair on 2012-01-02
The command you ran will check for updates . To apply them run the following and you will be asked if you want to proceed  .```
sudo apt-get upgrade 
```

---

### Post by lisati on 2012-01-02
The "update" option is only part of the picture. The following will apply updates:
```

sudo apt-get update && sudo apt-get upgrade

```
More information on apt-get can be found here: [https://help.ubuntu.com/11.10/serverguide/C/apt-get.html](https://help.ubuntu.com/11.10/serverguide/C/apt-get.html)

---

### Post by houmank on 2012-01-02
Oh right. Thank you very much.

Everything seems to have gone smooth.

I only got one message that worried me:


```
Setting up unattended-upgrades (0.55ubuntu6) ...
update-rc.d: warning: unattended-upgrades start runlevel arguments (none) do not match LSB Default-Start values (0 6)
update-rc.d: warning: unattended-upgrades stop runlevel arguments (0 6) do not match LSB Default-Stop values (none)

```

Do I have to be worried?

Thanks,

---

