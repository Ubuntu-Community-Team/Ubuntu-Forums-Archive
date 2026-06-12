---
title: "Cronjob results filling up / directory"
date: 2011-02-22
forum: General Help
---

### Post by weldonj on 2011-02-22
Some of my cronjobs are filling up files in my / directory.

How do I make this stop?

One of my cron jobs uses wget:
wget -q [http://www.mysite.com/bexcb0.php](http://www.mysite.com/bexcb0.php)

The bexcb0.php file writes a file and then echos a result if it is sucsesfull. These echo results are being put into bexcb0.php files in my /root folder  and are piling up. 

My / folder is filling up with files bexcb0.php  etc
bexcb0.php    bexcb0.php.1  bexcb0.php.2 bexcb0.php.3 bexcb0.php.4 bexcb0.php.5 etc

How do I make this stop?

If I just remove the echo will they stop writing to the / folder?

---

### Post by Cheesehead on 2011-02-24
Try wget's -O flag (output file), and direct the output to /dev/null or stdout (-)
```
wget -O /dev/null http://www.mysite.com/bexcb0.php
```

Or, it you really want to determine success, you need to capture the output to a variable and test it.
```
output=$(wget -O - http://www.mysite.com/bexcb0.php)
# Do your if-then logic to see if the variable contains what it should, and do something about it.
```

---

