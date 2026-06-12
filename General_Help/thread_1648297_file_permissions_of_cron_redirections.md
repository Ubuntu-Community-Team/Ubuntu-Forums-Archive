---
title: "file permissions of cron redirections"
date: 2010-12-18
forum: General Help
---

### Post by Hawkoon on 2010-12-18
I have a system with couple of local user accounts. I setup /etc/profile with umask 027 so that I can use groups to control if users can access files they don't own. It works great but now I find that cron saves stdout and stderr redirections with an effective umask of 022 (everybody has read rights).

My user cron tab looks like this:
```
SHELL=/bin/sh
# m h  dom mon dow   command
30 23  * * * /mnt/scripts/backup/eee_snapshots.bash >> /home/hawkoon/cron.msg 2>>/home/hawkoon/cron.err
```I don't want that everyone gets read permissions on these files but I am not sure how to configure this. Anyone got some ideas how to do this or why my umask setting in /etc/profile is overridden here?

I also see that redirections from rc.local too inherit read permissions for everyone. They are owned by root. Either the root umask needs to be configured some other place than /etc/profile or this refers to the same problem I am having with cron.

Thanks,
Hawkoon

---

### Post by efflandt on 2010-12-18
Assume NO environment for cron and you will not be disappointed.  In other words in crontab or script run from crontab you should use full paths and/or set any environment you need.  See **man 5 crontab** about the environment.

---

### Post by Hawkoon on 2010-12-19
Thanks efflandt for pointing this out.

A global umask definition in crontab (similar to SHELL=...) doesn't seem to work, but when I precede the crontab command with a umask statement I get the desired result.

```
52 14  * * * umask 027; /mnt/scripts/backup/eee_snapshots.bash >> /home/hawkoon/cron.msg 2>>/home/hawkoon/cron.err
```I am doing the same in rc.local now and it works there too.

---

### Post by tredegar on 2010-12-19
The alternative to messing with cron's umask, is to set the permissions on your home directory differently (ie "properly" IMHO)

```
chmod 750 /home/username
```
Now, nobody but yourself, or someone belonging to your group can read any file inside your **/home/username**

**root** can of course read anything, any time.

---

### Post by Hawkoon on 2010-12-19
> **tredegar said:**
> The alternative to messing with cron's umask, is to set the permissions on your home directory differently (ie "properly" IMHO)

```
chmod 750 /home/username
```Now, nobody but yourself, or someone belonging to your group can read any file inside your **/home/username**

**root** can of course read anything, any time.

Good point. But what if you move your files (by mistake or otherwise) to some shared partition? Permissions enforced through a parent directory will be lost. This is why I have taken the approach to handle permissions by the files themselves.

Then again, your approach is a lot simpler yet very effective, without needing to  insert umask statements in all sorts of places. Hmm, I will have to  rethink my setup with regards to the shared partition scenario.

---

