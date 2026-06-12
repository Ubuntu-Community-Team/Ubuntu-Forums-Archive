---
title: "Prey service autostart"
date: 2010-07-06
forum: General Help
---

### Post by rozbarwinek on 2010-07-06
Hi

I have installed Prey tracking program and filled API in configurator window.
Now, how can I check that Prey is running after reboot?
I haven't found anything in cron...

---

### Post by stlsaint on 2010-07-06
Not sure how prey works after install but if it has a app running you can see th process but install the package htop and using it to view processes!

---

### Post by cariboo on 2010-07-06
I quick way to check if a process is running is to open a terminal and type:

```
ps ax | grep prey
```

---

### Post by rozbarwinek on 2010-07-07
This is the result:

```
emil@emil:~$ ps ax | grep prey
1723 pts/1    S+     0:00 grep --color=auto prey
```

So the service is running and my laptop is secure? :)

---

### Post by quinnten83 on 2010-07-07
I guess the service is running, but I'm guessing it needs to be configured.
Maybe have a look at their website for details.
[http://preyproject.com/](http://preyproject.com/)

---

### Post by rozbarwinek on 2010-07-07
I have already configured it :D 
Thanks for help ^^

---

