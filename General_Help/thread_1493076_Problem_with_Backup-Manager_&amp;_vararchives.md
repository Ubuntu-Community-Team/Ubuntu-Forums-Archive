---
title: "Problem with Backup-Manager &amp; var/archives"
date: 2010-05-25
forum: General Help
---

### Post by drknot on 2010-05-25
Hello, new to these forums so please be gentle.

94GB partiotion constantly filling up due to backup-manager archiving  both /etc and /home into the var/archives folder (nothing to do with  apt!!) 

I've edited /etc/backup-manager.conf to archive /etc and /home/documents

/home currently ~35GB so even .tar.gz ends up around 18GB and 3+  versions - fills disc++

using shift-delete on /var/archives to bypass Trash and make space.

I think this is a workaround but would prefer to be able to properly  schedule backups and also for them to automatically land on my .gvfs  connected external network drive

No cron for user/root at present.
I have configured fstab on other systems in the past.

Running on amd64 10.04 with i855 graphics on an Acer 5520. I've already  searched the net/forums for this particualr issue and whilst raised in  some forms mostly blind ends to apt

suggestions/help appreciated.
I don't seem to have this issue on another laptop with 10.04 i686 but it  has a smaller home directory and 250GB h/d

in another life I would have /var on it's own partition and kept this to  only a few GB - and backup-manager would be failing silently to fill my  HD.

---

### Post by jerome1232 on 2010-05-25
I say an rsync script, get a one liner working then you can add error checking to it, and incremental backup capabilities and etc...


The one-liner would be something like
```
rsync -avz /etc /home /home/yourusername/.gvfs/networksharehere --exclude .gvfs
```

The only possible problem I can foresee is when your user is logged out does .gvfs exist? does it have the share mounted there still? I don't know, you can build the script to check for it though.

---

### Post by drknot on 2010-05-25
Thanks, that had crossed my mind as an option and looks workable.
I suspect I will need to permanently mount my drives through fstab rather than on demand via gvfs as I don't know how to check if a remote drive is present first!

It would be nice if there was a GUI or even gconf-editor way to enable/disable backup-manager. The conf file is fairly well commented so I hope what I've done will work.
Tips on b-m.conf greatly appreciated.

If it doesn't work I may end up sending to dev/null or uninstalling

---

