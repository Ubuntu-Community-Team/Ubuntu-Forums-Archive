---
title: "Host error"
date: 2012-03-14
forum: General Help
---

### Post by OldManRiver on 2012-03-14
All,

Have not personally changed anything on my U-Box (10.04 LTS), but now when I call for "sudo su" or "sudo -i" the system takes about 10 minutes to come back to prompt for password and giving this error:

```
sudo: unable to resolve host localhost.localdomain
```

Been installing some frameworks recently and went to the "/etc/hosts" file to see what is up.  The only things I saw were a bunch of adds for IPV6, which is turned off on my machine, so commented these out.

Reboot shows no change.  What do I need to do to correct this annoyance?

Thanks!

OMR

---

### Post by lisanels47 on 2012-03-14
check your hostname and make sure it's in the /etc/hosts file.  
#hostname
I think it's stored at /etc/hostname as well.  Here's mine for reference:

lisa@hsic-55:~$ cat /etc/hostname
hsic-55

lisa@hsic-55:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	hsic-55

---

### Post by OldManRiver on 2012-03-20
lisanels47,

Ah found the /etc/hostname file is now missing in action.

Thanks!

OMR

---

