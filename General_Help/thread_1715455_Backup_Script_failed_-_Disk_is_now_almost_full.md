---
title: "Backup Script failed - Disk is now almost full"
date: 2011-03-27
forum: General Help
---

### Post by NuMPTy_87 on 2011-03-27
Bit of an emergency it seems...

I was testing out a new cron job (very simple rsync), and for whatever reason when executed at midnight, the files were not written to the correct drive (executing the script manually does this).

'watching' df -k, I could see '/' fill up extremely quickly. I now have about 10GB~ free space on the 74GB raptor - down from 60GB.

I've gone through trying to find the offending files, however I can't seem to find them anywhere.

Any variety of 'du' that I know of isn't turning up anything.

Any suggestions?

Thanks!

---

### Post by NuMPTy_87 on 2011-03-27
bump :)

---

### Post by NuMPTy_87 on 2011-03-27
I suppose I should include the script that was running.
@daily /path/to/script

IE it went at midnight as it should.
Script itself:

```
sudo rsync -rltDvu --modify-window=1 --progress --delete --delete-excluded --exclude-from=/home/<name>/Documents/bash/bigbackupexclude.txt /home/<name>/ /media/"My Book"/rsync

```

It works perfectly when run manually, and it also worked perfectly when I tested it with cron before.

Not sure what happened, but I *need* to find out where these files are.

Thanks!

---

### Post by NuMPTy_87 on 2011-03-27
So, after running ```
du -ah | sort -rn | head

```
which unfortunately didn't work as expected, I noticed a strange thing:

```
1020K	./media/My Book/rsync/Documents/Cisco/CCNP/CCNP_SWITCH_642-813_Quick_Refe/CCNP SWITCH 642-813 Quick Reference.pdf
1020K	./media/My Book_/rsync/Documents/Cisco/CCNP/CCNP_SWITCH_642-813_Quick_Refe/CCNP SWITCH 642-813 Quick Reference.pdf
```

It seems that "My Book" was actually mounted to '/media/"My Book_", and that the script went and dumped my entire backup to /media/"My Book" as it should.

The mount point for the external hard drive keeps changing. I suppose I'll have to specify a UUID instead of a name...

Cheers,

---

### Post by NuMPTy_87 on 2011-03-27
And to add onto that... it seems the best method for this would be

[http://askubuntu.com/questions/4210/seagate-freeagent-external-hard-drive-keeps-auto-mounting-repeatedly]("http://askubuntu.com/questions/4210/seagate-freeagent-external-hard-drive-keeps-auto-mounting-repeatedly")

Hopefully it will help someone else :)

---

