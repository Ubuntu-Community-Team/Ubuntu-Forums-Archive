---
title: "Cron tab problem"
date: 2011-03-02
forum: General Help
---

### Post by formula on 2011-03-02
Hi 

When I try to run a cron tab it doesn't work and when I look in the log file this is what I get:
[http://iqdesk.co.uk/Screenshot.png](http://iqdesk.co.uk/Screenshot.png)

---

### Post by anglican on 2011-03-02
> **formula said:**
> Hi 

When I try to run a cron tab it doesn't work and when I look in the log file this is what I get:
[http://iqdesk.co.uk/Screenshot.png](http://iqdesk.co.uk/Screenshot.png)Make sure you use the full pathname to any and every command in your crontab. cron has a greatly reduced environment compared to the normal user environment. In particular, your PATH is very limited.

H

---

### Post by seawolf167 on 2011-03-02
What is the crontab entry that you are trying to run?

---

### Post by formula on 2011-03-02
lynx [http://my_domain/phpscript.php](http://my_domain/phpscript.php)

I am not sure I understand the path. Where I can set it?

---

### Post by SeijiSensei on 2011-03-02
Are you trying to run a PHP script on a regular basis?  It's much easier to run that on the server with the php binary like this:

```
/usr/bin/php5 /path/to/script.php 
```

Just install [php5-cli](http://packages.ubuntu.com/lucid/php5-cli) on the server.

---

