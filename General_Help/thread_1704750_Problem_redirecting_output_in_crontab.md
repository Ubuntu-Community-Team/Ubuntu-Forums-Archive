---
title: "Problem redirecting output in crontab"
date: 2011-03-11
forum: General Help
---

### Post by r.osmanov on 2011-03-11
Hi, folks. 

I've the following lines in crontab:
```

MAILTO=me@gmail.com

*/15 * * * * $CS www && /usr/bin/env php /www/s3/cron/s3_shop_indexer.php --index=s3_shop_product_delta --type=product --delta --dry-run && /usr/bin/env indexer -c /www/conf/sphinx.conf s3_shop_product_delta --rotate && /usr/bin/env indexer -c /www/conf/sphinx.conf --merge s3_shop_product s3_shop_product_delta --merge-dst-range deleted 0 0 --rotate 2>&1 >> /www/logs/crontab.shop.log
```It redirects output to both crtontab.shop.log and mailbox.

How do I redirect both ***stderr*** and ***stdout*** to a log file? 

Regards.

---

### Post by r.osmanov on 2011-03-11
anybody?

---

### Post by gmargo on 2011-03-11
You have a lengthy string of commands there.  Only the last command in that string is being redirected (stdout only).  All the previous ones are not.

Regarding redirection, you have:
```

command... 2>&1 >> /www/logs/crontab.shop.log

```but if you want both stdout and stderr redirected to the log file, it should be:
```

command... >> /www/logs/crontab.shop.log 2>&1

```Personally, I would move this to a shell script where it is more easily cared for.

---

### Post by r.osmanov on 2011-03-11
> **gmargo said:**
> You have a lengthy string of commands there.  Only the last command in that string is being redirected (stdout only).  All the previous ones are not.

Regarding redirection, you have:
```

command... 2>&1 >> /www/logs/crontab.shop.log

```but if you want both stdout and stderr redirected to the log file, it should be:
```

command... >> /www/logs/crontab.shop.log 2>&1

```Personally, I would move this to a shell script where it is more easily cared for.
Thank you. Changed the line. But I'm still receiving **stdout** in mailbox.

---

### Post by gmargo on 2011-03-11
> **r.osmanov said:**
> Thank you. Changed the line. But I'm still receiving **stdout** in mailbox.

As I said:
> 
 Only the last command in that string is being redirected. All the previous ones are not.
Put all that stuff in a shell script and limit your crontab entry to:
```

*/15 * * * * /path/to/shell/script.sh >> /www/logs/crontab.shop.log 2>&1

```Now everything will be redirected.  You'll only receive mail if the script is not present or not executable.

---

### Post by r.osmanov on 2011-03-11
Thank you! 
```
*/15 * * * * $CS www && /www/s3/cron/index_shop_delta.sh >> /www/logs/crontab.shop.log 2>&1
```
It works now as expected. So simple. 

However, it is stange. Cron should redirect the whole command output to the log...

---

### Post by rsevero on 2011-05-25
Be aware that cron doesn't redirects anything at all. The redirection is done by the shell cron calls when executing your command.
The way you originally wrote the command means that bash will redirect only the output of the last command. (I'm not sure cron is using bash on your machine).

---

