---
title: "Crontab permissions"
date: 2012-08-01
forum: General Help
---

### Post by meshman on 2012-08-01
I'm confused about permissions and crontab.  I have a shell script that backs up the entire OS to a .tgz file. (tar)  When I run this as root, I get a 500M+ backup file.  So I add this same command to crontab.
 
Command in the script file:
 
tar cvpzf /backup.tgz  --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

In crontab:
 
01 3    * * *   root    bash /home/myuser/backup.sh

I'm logged in as root when I edit this and all seems ok but after crontab runs the script all my backup file contains is the contents of the /etc directory (77mb).
 
What user is this actually running as?  No one is logged into the system when this executes so who (what user) is executing it?  If it's root, why won't it run the same way it does when I actually am logged in?
 
Thanks!
(Ubuntu 10.04)

---

### Post by ajgreeny on 2012-08-01
> **meshman said:**
> I'm confused about permissions and crontab.  I have a shell script that backs up the entire OS to a .tgz file. (tar)  When I run this as root, I get a 500M+ backup file.  So I add this same command to crontab.
 
Command in the script file:
 
tar cvpzf /backup.tgz  --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

In crontab:
 
01 3    * * *   root    bash /home/myuser/backup.sh

[COLOR=Red]I'm logged in as root when I edit this and all seems ok but after crontab runs the script all my backup file contains is the contents of the /etc directory (77mb).
[/COLOR]  
What user is this actually running as?  No one is logged into the system when this executes so who (what user) is executing it?  If it's root, why won't it run the same way it does when I actually am logged in?
 
Thanks!
(Ubuntu 10.04)
Are you really logged in as root when you make that edit of crontab, or do you actually do it with a **"sudo crontab -e"** command?

To run something through cron as root when there is no root user by default in ubuntu is not possible as far as I'm aware.  Cron is usually run as a normal user, not root, and I am not sure you need to do this as root anyway. Wait for more replies before you do anything rash, as I could be wrong about this.

---

### Post by meshman on 2012-08-14
> **ajgreeny said:**
> Are you really logged in as root when you make that edit of crontab, or do you actually do it with a **"sudo crontab -e"** command?
 
Yes. I think. I can't log in as root, I have to login as me and do 'sudo su'.
 
But I'm confused about the whole thing. Up until now I've been using /etc/crontab. If I do crontab -e, I get en empty file. In other words, this isn't /etc/crontab I'm editing (it's apparently /tmp/crontab.pqwHLM/crontab. ??) So I added the same line to whatever crontab -e is editing. Nothing at all happens at the scheduled time. (All editing in all cases is done as su)
 
What file am I supposed to be editing? I'm confused.
 
Thanks for the reply.

---

### Post by Dave_L on 2012-08-14
To add the command to root's crontab:

```
sudo crontab -e
```

Add the line

```
1 3 * * * bash /home/myuser/backup.sh >/home/myuser/backup.log 2>&1
```

(The log file is optional, but may be helpful if the script doesn't run correctly.)

Don't include the user "root" in the crontab entry.

To view the crontab afterwards:

```
sudo crontab -l
```

The actual crontab for root is in the file /var/spool/cron/crontabs/root, but it's preferable to use the crontab command to edit it, rather than edit it manually.

---

