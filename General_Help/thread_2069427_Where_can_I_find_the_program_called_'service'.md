---
title: "Where can I find the program called 'service'?"
date: 2012-10-10
forum: General Help
---

### Post by hanzj on 2012-10-10
[http://www.opendns.com/support/article/101](http://www.opendns.com/support/article/101) tells me that I need to run 

```
sudo /sbin/service ddclient start
```
So I try that command but get
> sudo: /sbin/service: command not found

I tried
```
 sudo apt-get install service
```
but I'm told
> E: Unable to locate package service

What must I do? Where can I get this file/program/package called "service"?

Thank you.

---

### Post by lisati on 2012-10-10
What happens when you try:....?
```
sudo service ddclient start
```

---

### Post by wojox on 2012-10-10
Try:
```
sudo service ddclient start
```
or
```
sudo /etc/init.d/ddclient start
```

---

### Post by hanzj on 2012-10-10
lisati,


```
sudo service ddclient start

``` > * To run ddclient as a daemon, please set run_daemon to 'true' in /etc/default/ddclient 
   ...done.

I guess that worked! Thanks, lisati!

---

### Post by hanzj on 2012-10-10
Thanks, wojox!

---

### Post by mikewhatever on 2012-10-10
...and service is actually in /usr/sbin/, in other words, /usr/sbin/service.

---

