---
title: "Configuring LogRotate for non /var/log logs."
date: 2012-08-03
forum: General Help
---

### Post by teward on 2012-08-03
I'm not entirely certain how to do this but...
 
I've got a cron script running hourly that runs a script that logs the current date and time, and also the output of `free -m` to /root/memlog
 
Is there a way to set up logrotate to rotate that log daily such that it moves /root/memlog to /root/memlog.date? If so, what do I need to do to configure that? (I'm not too familiar with logrotate)
 
 
---
 
After digging around in the manpage, would this run it daily without compression, and only keep a week's worth of files?
 
```
/root/memlog {
  daily
  missingok
  rotate 7
  create 640 root root
  nosharedscripts
}

```

---

### Post by kjohri on 2012-08-14
Try,

```
 /root/memlog {
        daily
        missingok
        rotate 7
        dateext
        create 640 root root
 }
```

[http://www.softprayog.in/tutorials/managing-log-files-with-logrotate]("http://www.softprayog.in/tutorials/managing-log-files-with-logrotate")

---

