---
title: "Cannot start samba"
date: 2011-01-29
forum: General Help
---

### Post by tgckpg on 2011-01-29
```
owner@Owner-desktop:/$ start smbd
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.119" (uid=1000 pid=7042 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

owner@Owner-desktop:/$ ls /var/log/samba
ls: cannot access /var/log/samba: No such file or directory


```

---

### Post by amsterdamharu on 2011-01-29
Try sudo, 
```
sudo start smbd
sudo start nmbd
```


The default in Ubuntu is that it starts when your system starts:
In the /etc/init/smbd.conf there is a line beginning with "start on ", if you want to start samba and nmbd manually you should change this to:
```
start on start-smbd
```

To do so you can use nano:
```
sudo nano /etc/init/smbd.conf
```
after changing it press control + x then y and enter.

---

