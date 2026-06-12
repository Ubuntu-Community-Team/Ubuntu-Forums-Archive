---
title: "How to delete saved files on log out"
date: 2010-04-11
forum: General Help
---

### Post by Andy Wilkins on 2010-04-11
I'm setting up a single stand-alone computer in my classroom to be used by my students at the school where I teach. I've installed Ubuntu, as it smashes Windoze out of the court every time. 

I want the students to be able to log on to the computer using just one account: 'Student'. This computer will be attached to a printer so they can type up and print oOfice documents,web pages, etc. However, once they log out, I want any files they might have saved (such as a word processed document) to be removed/deleted from the account so that when another pupil logs on to the 'Student' account they start with a clean slate. I suppose you could call it a sort-of Kiosk account.

How can I get Ubuntu to clear any saved documents on log-out?

Cheers in advance!

---

### Post by WinterRain on 2010-04-11
I believe **Pessulus** is what you will need. From synaptic package manager: "pessulus enables the system administrator to set mandatory settings in
GConf, which apply to all users, restricting what they can do, which may
be of particular usefulness for kiosks (internet cafes, for example).

Examples of what can be locked down are the panels (no changes in the panel
configuration are allowed, locking their position and their contents), some
of their functions individually (disabling screen locking and log out), the
web browser (disabling specific protocols, arbitrary URLs, forcing the user
to be in fullscreen mode), among many others."

Hope this helps.

---

### Post by nixclusive on 2010-04-11
I achieved a similar setup using pam_mount. Its a PAM module that allows you to mount a filesystem before logging in and automatically unmounts it after you log out. Setting a user's filesystem as tmpfs ensures that no files are saved once the user logs out.

Install pam_mount
```
sudo apt-get install libpam-mount
```

edit the file **/etc/security/pam_mount.conf.xml** and add:
```
<volume user="**student**" fstype="tmpfs" path="none" mountpoint="/home/**student**" options="size=256M,noatime,nosuid,nodev,noexec,uid=%(USER),mode=0700" />
``` after the line ```
<!-- Volume definitions -->
```

this may not be the best solution though as files are still left in /tmp (cleared on reboot) and the system doesn't take it very kindly if the user on a tmpfs home directory attempts to run the command 'ecryptfs-setup-private'.

---

### Post by Andy Wilkins on 2010-04-11
Thanks nixclusive.

Worked a charm!

---

### Post by nixclusive on 2010-04-12
This does not prevent them from writing a [_crontab_](https://help.ubuntu.com/community/CronHowto) and abuse the command scheduler. You might want to create a cron.deny file and list your guest user in there to prevent this.

```
sudo echo '**student**' >> /etc/cron.deny
```

---

### Post by Andy Wilkins on 2010-04-13
Cheers Nix

---

