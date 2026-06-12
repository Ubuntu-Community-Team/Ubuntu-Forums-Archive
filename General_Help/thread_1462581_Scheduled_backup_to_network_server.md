---
title: "Scheduled backup to network server"
date: 2010-04-25
forum: General Help
---

### Post by humphreybc on 2010-04-25
Hi,

I have a server in my house that I store a lot of stuff on. I have it bookmarked in Nautilus, and when I hit the bookmark for the first time in a session, it mounts the server as "sftp for benjamin on 192.168.1.2"

I can drag and drop files across using ssh in Nautilus, it works really well.

But I want to have automatic backups. I tried "Back in Time" but it doesn't seem to give me the option of choosing my server in the list of "backup to" folders.

I don't want to mess around with cronjobs and stuff, I just want something that will simply backup my things every few days. I also don't want it creating an entirely new copy of all my unchanged stuff each time, but rather just modifying the things I change.

Thanks!

---

### Post by blueridgedog on 2010-04-25
I suggest rsync and a crontab entry (though that is not what you want).

This guide looks good:

[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

I would use the -av option and the --delete option.

---

