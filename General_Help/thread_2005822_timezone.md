---
title: "timezone"
date: 2012-06-18
forum: General Help
---

### Post by winzip on 2012-06-18
Hi 

I want to check what  timezone has been set in Ubuntu server. 

How do I find it ? whats the command ?

---

### Post by codemaniac on 2012-06-18
date command lets you know in what timezone you are in .

```
man date
``` 

Also see **/etc/timezone **

Changing the Time Zone :

Open up a terminal , 
```
sudo dpkg-reconfigure tzdata
```

Follow the directions in the terminal.

---

