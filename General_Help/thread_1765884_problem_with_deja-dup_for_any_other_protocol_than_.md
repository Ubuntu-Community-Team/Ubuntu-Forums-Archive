---
title: "problem with deja-dup for any other protocol than FILE"
date: 2011-05-23
forum: General Help
---

### Post by lmirguet on 2011-05-23
Hi,

I have a problem with deja-dup: it refuses to use any other protocol than FILE.
For example, if I select the FTP protocol, and that I check the stdout, I can read:

[FONT=Courier New]** (deja-dup:4333): DEBUG: DuplicityInstance.vala:203: Running the following duplicity (4383) command: duplicity 'collection-status' '--exclude=/root/deja-dup/ftp:/admin@192.168.0.4:21/Public/backups/planetjoshua' '--include=/var/spool/cron' '--exclude=/home/laurent/.VirtualBox' '--include=/home' '--exclude=/root/.gvfs' '--exclude=/root/.cache/deja-dup' '--exclude=/root/.cache' '--include=/root' '--include=/opt' '--include=/etc' '--exclude=/sys' '--exclude=/proc' '--exclude=/tmp' '--exclude=**' '--gio' '--no-encryption' 'file:///root/deja-dup/ftp:/admin@192.168.0.4:21/Public/backups/planetjoshua' '--verbosity=9' '--archive-dir=/root/.cache/deja-dup' '--log-file=/tmp/deja-dup-8H10VV'
[/FONT]
So apparently it prefixes the backup location with [FONT=Courier New]file:///root/deja-dup[/FONT] (which is the current directory).

I tried to look into this issue without any success. Does someone have an idea ?

Thanks
Laurent

---

