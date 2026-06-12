---
title: "rsync as root in ubuntu"
date: 2011-07-04
forum: General Help
---

### Post by chah on 2011-07-04
Hi, I want to backup accounts using rsync and cron. I need to do this as root to be able to access all the files in other peoples accounts. I'm not sure what is the way that this kind of command is intended to be executed in ubuntu. Should I create a password for root on the remote machine and do rsync -av root@192.168.1.4:/home . to copy it to my current machine?

---

### Post by papibe on 2011-07-04
You can create a crontab for root using sudo. Take a look at this tutorial: [Cron Howto]("https://help.ubuntu.com/community/CronHowto").

---

### Post by chah on 2011-07-05
Hi Thanks for the reply. I do already sort of know how to use cron. My question is more pertaining to the rsync portion. I want to backup home directories from server A to server B using rsync. Do I login to server B and type:

$ rsync -av root@serverA:/home .

meaning I need to enable ssh or rsync services on serverA. Or is the standard way to rsync using a the ubuntu account and then sudo to root there before copying files? But to sudo, I need to type in a password, which means I need an interactive shell?

I'm not sure of the process. Right now, root does not seem to have a password on my machine, and I don't know if it is allowed to ssh to a remote machine using the root account in ubuntu.

---

### Post by SeijiSensei on 2011-07-06
rsync uses SSH by default to set up its sessions.  You can use SSH shared-key authentication to avoid the need to set up passwords.  See this: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by aeiah on 2011-07-06
are you wanting to backup the home directories (as you say) or do you want to mirror them on server B? if you just want to back them up, you dont need to ssh into server B as root. just ssh in using whatever username has write access to your backup directory. something like this in server A's root crontab would be fine
```

sudo crontab -e
```

```

0 * * * * rsync -a /home/ backupuser@serverB:~/backup_directory/home/

```


its good practice not to enable root logins on ssh (since root is a known username with, well, root privilages). setup a keypair, make sure server B is connectable via ssh and dump your home dirs.

---

### Post by chah on 2011-07-07
Hi aeiah,

Would what you are suggesting preserve the ownerships of each file? Or would each file be owned by backupuser in your example crontab entry?

---

