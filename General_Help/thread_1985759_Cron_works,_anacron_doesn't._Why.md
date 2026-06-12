---
title: "Cron works, anacron doesn't. Why?"
date: 2012-05-23
forum: General Help
---

### Post by quixote on 2012-05-23
I'm backing up some directories on my laptop, running Lucid, to a networked server. The script runs rsync on an ssh connection. On cron everything works. The crontab line looks like this:
```
10 09 * * * SSH_AUTH_SOCK="$(find /tmp/keyring*/ -perm 0755 -type s -user quixote -group quixote -name '*ssh' | head -n 1)" /home/quixote/teaching-daily-sh 1>log-rsync.txt 2>log-rsync-erss.txt
``` The script, teaching-daily-sh has the rsync line to back up the relevant directories.

I'm trying to use anacron instead because the laptop is often off when cron needs it, so backups are unreliable. This is the anacrontab line:```

1      30     q.daily  SSH_AUTH_SOCK="$(find /tmp/keyring*/ -perm 0755 -type s -user quixote -group quixote -name '*ssh' | head -n 1)"  nice run-parts --report  /home/quixote/.anacron/quixote.daily 1>log-rsync.txt 2>log-rsync-erss.txt

``` The "quixote.daily" directory contains only the same teaching-daily-sh script that also runs under cron.

Judging by the error output files, the only difference is that SSH_AUTH_SOCK is successful in authenticating the cron job, but anacron just doesn't get it. I keep getting "Host verification failed." Since the exact same thing works outside of anacron, it's not a problem with my ssh setup.

On another computer, I have the exact same setup, except it's LinuxMint Debian, and the scripts anacron runs that need ssh authentication run fine.

Is there something odd about anacron on Lucid? Can anybody figure out what I'm doing wrong?  This is driving me nuts!

---

### Post by quixote on 2012-05-26
Nobody has any ideas? Say it ain't so! :(

---

