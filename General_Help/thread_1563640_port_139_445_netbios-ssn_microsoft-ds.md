---
title: "port 139 445 netbios-ssn microsoft-ds"
date: 2010-08-29
forum: General Help
---

### Post by hellz99 on 2010-08-29
I have these two ports open for some reason.  netstat says they're attached to 'smbd', but when I look at packages installed and search for smbd the only thing that comes up is samba4 which is NOT installed.

I'm guessing some other package installed this as a dependency.  Is there anyway to find out what it was and remove it?

---

### Post by redmk2 on 2010-08-29
r> **hellz99 said:**
> I have these two ports open for some reason.  netstat says they're attached to 'smbd', but when I look at packages installed and search for smbd the only thing that comes up is samba4 which is NOT installed.

I'm guessing some other package installed this as a dependency.  Is there anyway to find out what it was and remove it?

Those are ports for Samba and *smbd *is the daemon that should be running.  Maybe you installed Samba 3.  

Let's see if Samba is really running on your host.  From the terminal post the output of ```
**ps -ef | grep mbd**
```

---

### Post by hellz99 on 2010-08-29
Right.  
```

root      1083     1  0 Aug26 ?        00:00:00 smbd -F
root      1176  1083  0 Aug26 ?        00:00:00 smbd -F
root      2035     1  0 Aug26 ?        00:00:01 nmbd -D

```

I dont see that samba3 is installed either.

---

### Post by Monotoko on 2010-08-29
First thing I would do is ensure your computer drops any connections on those ports if it is not used:

```
iptables -A INPUT -p tcp --dport 139 -j DROP
iptables -A INPUT -p tcp --dport 445 -j DROP
```

Now we can figure out what's causing it, check if you have samba installed, and if it is, remove it: 
```
dpkg -s samba|grep installed
```

If its installed:
```
sudo apt-get remove samba
```

---

### Post by hellz99 on 2010-08-29
yes that did it. now removed.
I have a feeling that installing wireshark is what installed samba because upon uninstalling samba there was also wireshark listed in the other stuff getting uninstalled.

---

