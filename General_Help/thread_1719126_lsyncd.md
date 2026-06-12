---
title: "lsyncd"
date: 2011-04-01
forum: General Help
---

### Post by lukejanicke on 2011-04-01
I can't make **lsyncd** work between [COLOR="navy"]/home[/COLOR] and [COLOR="navy"]/var/www[/COLOR].

I'm using [COLOR="red"]Ubuntu 10.10[/COLOR] and [COLOR="Red"]lsyncd 2.0.4[/COLOR].

I tested **lsyncd** with two folders in my Documents directory and it worked fully (even with two daemons to give two-way sync).

I want to sync
[COLOR="Navy"]/home/lukejanicke/Websites/Development/follow[/COLOR]
to
[COLOR="navy"]/var/www/follow[/COLOR]

The Terminal command to start the daemon is:
```
lsyncd -rsync /home/lukejanicke/Websites/Development/follow/ /var/www/follow/
```

When I run this command, the folders are sync'd **once** but any changes made thereafter are not sync'd.

Can anyone help?

---

### Post by supermasita on 2011-04-03
Hi!

This is how i would use LSYNCD

* Create a file "lsyncd.conf" (or any name u like) with the following:

```
settings = {
   logfile    = "/var/tmp/lsyncd.log",
   statusFile = "/var/tmp/lsyncd.status",
   nodaemon   = true,
}

sync{default.rsync, source="/home/lukejanicke/Websites/Development/follow/", target="/var/www/follow", rsyncOps="-ltusv", delay=1}
```

(The setting array defines where to write log and status, and it also says not to use LSYNCD as DAEMON, but if u intend to sync al the time, it may be better to set to TRUE).

(The sync array, defines source and target, also RSYNC options and delay before syncing in seconds).

* Then u just run lsyncd with:
```
lsyncd lsyncd.config
```

Hope this helps! :)

---

### Post by lukejanicke on 2011-04-04
Thanks! That works perfectly.

I think it was the ```
rsyncOps="-ltusv", delay=1
``` bit that made the difference. I don't understand those options. I better read the manual again.

---

### Post by axkibe on 2011-04-04
Is your case a two-way operation or a one-way?

If its a two-way "-u" from the rsyncOps makes a difference, but alone is not yet a clear solution. Use a --temp-dir=DIR with two different dirs for both daemons.

If its one-way, nothing in the config file should make a difference to the command line. Except it sets the delay from 15 seconds down to 1 second. Maybe you looked a little to early in the target directory?

If its one way, and after a minute the files are still not in the target, please log it with providing "-log all" and paste the log file.

---

### Post by supermasita on 2011-04-04
In my example, i use it to sync to a frontend that may have cached data that i dont want to overwrite (if its new), so "-u" is only useful in a two way or any other special situations :) u r right.
> **axkibe said:**
> 
If its a two-way "-u" from the rsyncOps makes a difference


---

### Post by dean.p on 2011-06-05
I too had a little trouble getting lsyncd to work butin the end, it's great! I sync one-way between a local server and remote PC using a 5 second delay (lsyncd --delay 5).

However, my problem now is that lsyncd does not automatically start if the server reboots. I need lsyncd to start automatically also using the --delay 5 option.

I've had trouble finding any info on this other that some Japanese sites (I cant read japanese) using chkconfig, although didn't work as I think chkconfig is depreciated anyway.

I'm sing Ubuntu server 10.10, any help would be appreciated.... I'm not a linux guru but get by with the basics ;)

---

### Post by malleeblue on 2012-09-09
Seems this thread should be marked as solved?

Anyways, just wanted to say that I too have gotten this combination of lsyncd and rsync to do instant backups of my data to another computer and it's working really well. I look forward to some genius brining it all together into a gui and touting it as a real, local/LAN Dropbox-like solution. Really glad to have found lsyncd.

---

