---
title: "Problems with applying superuser priviledges permanently"
date: 2006-06-23
forum: General Help
---

### Post by daller on 2006-06-23
Hi There,

I have a problem with applying superuser priviledges to my user (elav)

This is my sudoers-file (edited with "sudo visudo")

```

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults	!lecture,tty_tickets,!fqdn

# User privilege specification
root	ALL=(ALL) ALL
elav	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

Running apt-get update (well, basically everything!) returns a permission error:

 ```

E: Could not open lockfile /var/lib/apt/lists/lock - open (13 Permission denied)

```

The reason I want superuser priviledges, is that I have sispm installed (sourceforge.net/projects/sispm) and a frontend for it...

...And it has to do it automatically... The app opens automatically on KDE startup

---

### Post by lkagan on 2006-06-23
It's working just as it should.  The fact that you can type 

```
sudo visudo
```

Let's you know it's doing what it's supposed to.  All sudo will let you do is run a program as the root user after entering your password as you did to edit the sudoers file.    

If you type:

```
groups
```

At the command line you'll see that you belong to the admin group. This line:

```
%admin ALL=(ALL) ALL
```

says that anyone in the admin group can run commands as root by using sudo.  So go ahead and get rid of the line you added, it's redundant.

If you want to actually run programs as root without entering the password, you will have to become root.  Based on the number of posts I see you've made to these forums, I'll assume you already know how to do that.  Another option is a hack that I've seen but don't much care for.  Change the uid and gid in /etc/password to 0 which is the same as root.

Larry

---

### Post by daller on 2006-06-23
Yes, but the whole idea with editing the sudoers file, is to gain superuser access without typing my password!

the command "sispm" has to run without sudo!

...I have gotten this to work on many computers, but it doesn't work on this one!

I have turned off the machine that has the error - But I'll try again tomorrow!

----

On this pc, it work with the following line in the sudoers file:

```
elav   ALL= /usr/bin/sispm
```

...but it doesn't work on the other machine!

---

### Post by aysiu on 2006-06-23
You'd want something like this added to your /etc/sudoers file: ```
daller ALL = NOPASSWD: /usr/bin/sispm
```

---

### Post by mlind on 2006-06-23
[QUOTE=daller]Yes, but the whole idea with editing the sudoers file, is to gain superuser access without typing my password!
[/QUOTE]

sudo is used to execute command as another user. /etc/sudoers just
defines rules for sudo usage. if you wan't to execute scripts/applications that require
root privileges, use NOPASSWD option that's described on sudoers manual.

```

man sudoers

```

---

### Post by daller on 2006-06-23
Is there an alternate way, to make a single file (maybe from several users!) run with root priviledges?

EDIT: Well, that just got answered... :D - You are so damn fast on this forum :)

...And I'll try it on the other machine tomorrow!

And I'll be able to execute it without a leading "sudo" ???

---

### Post by aysiu on 2006-06-23
No, you'd still have to execute it with the *sudo* prefix, but you wouldn't be prompted for your password in order to execute the command.

---

