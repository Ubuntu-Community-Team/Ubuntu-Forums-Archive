---
title: "root help"
date: 2010-01-18
forum: General Help
---

### Post by Armyguy on 2010-01-18
I recently decided to give linux a try on my personal machine. I work on a unix machine from time to time at work but am pretty much a novice with what I am doing on this laptop. I am running Ubuntu 9.10, I was trying to change the root password on my laptop but ran into the following:

charles@charles-laptop:~$ whoami
charles

charles@charles-laptop:~$ sudo password root
sudo: password: command not found

charles@charles-laptop:~$ which sudo
/usr/bin/sudo


Any ideas, or am I doing this wrong?

---

### Post by rmjokers on 2010-01-18
Ubuntu doesnt use the root account by default. It exists on the system, but it doesnt have a password, and doesnt allow logins. You can do everything root would do using sudo. However, if you really want to enable the root account, you can. Just type "sudo passwd root" and set the password.

See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more details.

---

### Post by snowpine on 2010-01-18
Yes you are doing it wrong. :) There is no need to enable the root account in Ubuntu; we use 'sudo' instead. Check it out:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by sisco311 on 2010-01-18
The root account password is disabled, by default, for a reason.

Ubuntu's default security model uses sudo for temporary privilege escalation on particular tasks for particular users with a password authentication.

Please read the community documentation: [uhelp]community/RootSudo[/uhelp]

Once you understand how sudo works you will understand why don't you need a password for the root account. ;)

EDIT: d'oh, i'm slow! :)

---

### Post by Leppie on 2010-01-18
there's other ways to get to the root shell if that is what you're trying to do.

---

### Post by oldfred on 2010-01-18
The forum even has rules on root vs sudo which I happened acroos one day:

Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by Xog on 2010-01-18
the other day I was trying to use sudo to edit blacklist.conf and it was giving me permission denied.

i typed in
```
sudo -i
```
then proceeded to gedit blacklist.conf and it worked.

---

### Post by Leppie on 2010-01-18
> **oldfred said:**
> The forum even has rules on root vs sudo which I happened acroos one day:

Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)
the thing is that there's no rule against starting a root shell.

---

