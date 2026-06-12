---
title: "crontab activation?"
date: 2010-11-17
forum: General Help
---

### Post by Bradj47 on 2010-11-17
I wrote my first cronjob today using **crontab -e**. But it seems it didn't work. Is there some activation process I have to go through once I write the file? Here's what I have in the crontab: 

```
# m h  dom mon dow   command

0 * * * *       <command>
0 * * * *       <command>

```

---

### Post by ksteuber on 2010-11-17
Try seeing if cron in running.
You can use ```
ps aux
``` to view running processes, or I would use something like ```
ps aux | grep cron | grep -v grep
``` This will search the running processes for anything with the word 'cron' in it without listing the process you just ran to grep for cron. If there is no output, cron is not running.

---

### Post by matt_symes on 2010-11-17
Hi

Make sure your file is executable (if it is not already)

Use chmod +x <filename>

Also use the full path to the file. And remember cron does not have your environmental variables

> once I write the fileActually, what are you trying to do? I might have misread your post.

Kind regards

---

### Post by Bradj47 on 2010-11-17
> **matt_symes said:**
> Hi

Make sure your file is executable (if it is not already)

Use chmod +x <filename>

Also use the full path to the file. And remember cron does not have your environmental variables

Actually, what are you trying to do? I might have misread your post.

Kind regards

Well both hidden commands there are ssh commands. I hid them to protect my server information. Are ssh-keygens considered environmental variables? That might be the problem I'm having.

---

### Post by asmoore82 on 2010-11-17
crontab jobs are executed with a very basic shell.
Typically, this means each crontab entry needs to call a full fledged
BASH shell script to do the heavy lifting.

Also, crontab jobs are executed in their own "clean" Environment.
They have no immediate relationship with your Desktop session and
are unable to access your encrypted private SSH keys.

You can simply not lock your SSH keys with a password when you create them.
This does not reduce the security of using the SSH keys across the network,
It simply means that your local $HOME/.ssh/id_rsa file contains your un-encrypted
private key and should therefore be protected as if it were your password.

To grant cronjobs a relationship with your Desktop session,
they can simply snoop the relative Environment data from /proc ...
```
cat /proc/$(pgrep -n -u "$USER" gnome-session)/environ
```

---

