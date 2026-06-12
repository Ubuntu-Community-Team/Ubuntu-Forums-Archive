---
title: "sudoed but getting permission denied"
date: 2011-01-30
forum: General Help
---

### Post by Red Kelly on 2011-01-30
I'm trying to "Enables packet forwarding by kernel" by 
```
sudo echo 1 > /proc/sys/net/ipv4/ip_forward
```
but i get 
```
bash: /proc/sys/net/ipv4/ip_forward: Permission denied
```
How do I get permission?

(Reason for forwarding packets is to share internet from eth0 to eth1)

thanks.

---

### Post by Nytram on 2011-01-30
You can start a root shell with the command **su** and then enter the commands.

---

### Post by tredegar on 2011-01-30
Sudo doesn't work when there is redirection (>). You can make it work like this:

```
sudo sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'
```

---

### Post by Red Kelly on 2011-01-30
don't worry found I could change /etc/sysctl.conf and get the same thing after a restart.

thanks anyway. will remember for future.

---

### Post by Elfy on 2011-01-30
> **Nytram said:**
> You can start a root shell with the command **su** and then enter the commands.

Except there'll be no password setup as ubuntu does not have a root password by default.

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Nytram on 2011-01-30
Course, I forgot, been using Arch too long.

---

