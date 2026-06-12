---
title: "Ubuntu 11.10 unable to login"
date: 2012-03-20
forum: General Help
---

### Post by jgomezh4 on 2012-03-20
Hello!

I´ve been using Ubuntu 11.10 for a couple of months without any problem. However i´m now unable to log in. It happened after i installed Sophos Antivirus. The system got awfully slow after the installation so i tried to shut my laptop down. The system then refused to shut down (nothing happened) so i performed a hard reset. Then, at the login screen after i enter my password a black screen is showed like half a second and the login screen comes everytime back again. This happens also with the guest account and using both Unity and Gnome desktops.

I already deleted the .Xauthority file in the user home folder and nothing happened. I also renamed the home folder (mv /home Backup) and created a new one with proper owner seetings and that didn´t solve the problem either. I already deinstalled Sophos which didn´t help.  Since i have little experience with ubuntu i don´t know what to try next. I´m able to login using ctrl+alt+f1 so my password is working....

 Any help would be really appreciated.

---

### Post by Paddy Landau on 2012-03-21
I see no one else has responded, so I'll help to what extent I can (not much, though).

Why do you need antivirus -- are you forwarding files to Windows users?

If I had your situation, the first thing I'd do would be to try to clean out the installations. You say you have deinstalled Sophos; I presume you did that from the Recovery console? Also from the Recovery console (with networking), try these in order:
```
sudo apt-get --fix-broken install
sudo dpkg --configure --pending
sudo apt-get update
sudo apt-get dist-upgrade
```In all fairness, this probably won't help, but it's worth a try.

As a last resort, use a Live CD to back up your entire home folder and then reinstall Ubuntu.

Sorry I'm not much help.

---

### Post by jgomezh4 on 2012-03-23
well, that is the output to the lines you suggested:

```

sudo apt-get --fix-broken install
W: Not using locking for read only file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.

sudo dpkg --configure --pending
dpkg: error: unable to acces dpkg status area: Read-only file system
```maybe that helps anybody finding the problem...

and the question about the antivirus: yes, i am constantly receiving and forwarding files to and from windows users.

Thanks for the help anyway. Ill probably end up reinstalling Ubuntu.

---

### Post by Paddy Landau on 2012-03-23
Interesting. Sophos has managed to convert your file system into read-only:

> **jgomezh4 said:**
> [FONT=Lucida Console]... read only file ...
... Read-only file system[/FONT]

This is not something I have come across before. I will help as far as I can (which is not much -- I hope someone else with better knowledge will chime in), otherwise reinstalling Ubuntu would solve that problem.

Please post the contents of your file /etc/fstab and we'll see if there is anything there to help.

---

