---
title: "rsync over wireless at logout"
date: 2009-08-13
forum: General Help
---

### Post by diederick76 on 2009-08-13
Hi,

I have a bash script that does a backup of my user's home directory using rsync over a network, when I power down my computer. The script is called backup and lives in /etc/init.d. With

```
sudo update-rc.d backup start 03 0 6 .
```

I made sure it was executed when the computer powers down.

After this appeared to work nicely on my desktop box, I wanted to perform the same trick on my laptop. My laptop however uses a wireless connection, which appears to shut down when the user logs out, presumably because wireless connections are controlled by network-manager, which is run by the user (is that right?).

So I moved the backup script to ~/bin/, and created a file called .xsession with these contents:

```

gnome-session
~/bin/backup

```

I put this in my user's home dir. It appeared to work, but only when I choose "Log off", not when I power down the laptop directly from the gnome panel. Exactly the same happens when I create a ~/.bash_logoff which calls the backup script.

Can someone tell me why this is, how I can find out what exactly happens during logging off and in what order, and, more specifically, how I can make a script run during logoff, but before network-manager shuts down?

Thanks for any help.

---

### Post by P4man on 2009-08-13
put it in the shutdown script. This link may help:
[http://ubuntuforums.org/showthread.php?t=436346](http://ubuntuforums.org/showthread.php?t=436346)

---

