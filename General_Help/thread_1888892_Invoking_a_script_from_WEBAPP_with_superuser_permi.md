---
title: "Invoking a script from WEBAPP with superuser permissions"
date: 2011-11-30
forum: General Help
---

### Post by Sérgio André on 2011-11-30
Hi :)

I am trying to run a script from a webapp on tomcat6. The problem is that I need superuser permissions for tomcat6 user to run the script.

I have not changed my sudoers file, I just created a new one at /etc/sudoers.d/ that looks like this:

[INDENT]Defaults    env_keep += "JAVA_HOME"

# Host alias specification

# User alias specification

# Cmnd alias specification
Cmnd_Alias TOMCAT_ALLOWED = /opt/domotics/databasebackup.sh, /usr/bin/innobackupex

# User privilege specification
tomcat6 ALL=(ALL) NOPASSWD: TOMCAT_ALLOWED[/INDENT]

The problem is that I keep getting this error:
[INDENT]"sudo no tty present and no askpass program specified"[/INDENT]

I know why I am getting this error, I just do not know how to solve it :S

I have already used "Defaults visiblepw" but this option only makes my webapp act like an endless loop (prompts for a password and I do not want that behavior).

Am I missing something? (information in [http://ubuntuforums.org/archive/index.php/t-639803.html](http://ubuntuforums.org/archive/index.php/t-639803.html) is not solving my problem either)

PS: Release
[INDENT]DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"[/INDENT]

If you need more information, just let me know :)

Thanks in advance,
Sérgio

---

### Post by gordintoronto on 2011-11-30
"The problem is that I need superuser permissions for tomcat6 user to run the script."

Why? It doesn't seem reasonable.

---

### Post by Sérgio André on 2011-11-30
I want my webapp to be able to run the innobackupex command. This command requires sudo to run successfully. That is why I am trying to give the user tomcat6 the chance to run it without sudo password. This process must be "transparent" to the webapp user.

EDIT: Now that I read my first post and yours, I explained it wrongly. I do not want tomcat6 to be superuser or run as superuser. I just want tomcat6 to be allowed run those commands.

---

### Post by gordintoronto on 2011-11-30
If the command requires sudo, your databases are in the wrong location.  

Also note what the suppliers of innobackupex say: "We are currently not satisfied with the architecture, code quality and maintainability, or functionality of innobackupex, and we expect to replace it with something else in the future."

---

### Post by Sérgio André on 2011-12-02
Thank you for the reply.

To be honest, my databases are not in the wrong location, the innobackupex requires access to the mysql database (would be fine if it was only dependent of my databases to run). I would have to change mysql permissions or allow innobackupex to run with sudo. Honestly I prefer the second choice.

About innobackupex, I have to agree, they have a lot of things to improve (my database user needs full grants to mysql database, needs sudo to backup any user database, etc.) and I am expecting that, but at the moment I really have to use it :)

Anyway, I was able to make tomcat6 capable of running innobackupex :)

Thanks for the all the help and advices :)

---

### Post by brainthegrinch on 2012-10-17
[Sérgio André]("http://ubuntuforums.org/member.php?u=1503492") how did you fix it..  I have the same problem has you

---

### Post by SlugSlug on 2012-10-17
you would edit sudoers with

sudo visudoers

and enter 



```
tomcat (or whatever username) ALL=NOPASSWD: /path/to/script
```

at bottom of file

---

### Post by brainthegrinch on 2012-10-17
I know this part, my problem is about the tty problem explain in the beginning of the thread
sudo no tty present and no askpass program specified

---

