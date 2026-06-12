---
title: "No-ip client start on system boot"
date: 2006-05-22
forum: General Help
---

### Post by flabbas on 2006-05-22
Im trying to get the Noip2 client to start at system boot, unfortunately it needs to be run as root.

I used:

```
echo '/usr/local/bin/noip2' >> /etc/rc.local
```

To add an entry into the rc.local, but the client still does not load on boot.

Am I doing something wrong?

---

### Post by PBK on 2006-05-22
I have no-ip installed on my system. I have a file named "no-ip" in my /etc/init.d/ directory. Do you have this file?

---

### Post by Mr Green on 2006-05-23
sudo apt-get install no-ip
sudo no-ip -C
sudo /etc/init.d/no-ip start

Will start no-ip and make sure it starts after reboot.

---

