---
title: "Can't use sudo"
date: 2012-04-17
forum: General Help
---

### Post by LeeM on 2012-04-17
Help!
I am running Ubuntu 11.10. Suddenly I can't use sudo. Whenever I issue a sudo command, e.g., 'sudo ls', when I enter my password, it says 'lee is not in the sudoers file. This incident will be reported.
Following several threads here, I have issued the command 'groups' and get 'lee vboxusers'  Nothing about admin

I tried rebooting in recovery mode, and ran 'sudo visudo' to see the sudoers file. But the response I get is 'Read-only file system'

When in recovery mode, I also tried 'useradd -G admin lee' and got "useradd: user 'lee' already exists"
I'm stumped! The only clue I have is that this seemed to start happening after I began using VirtualBox. Could that have overwritten something in my groups?

---

### Post by Azdour on 2012-04-18
Hi,

I believe you need to use the following to add a user to a group (see man usermod):

```
usermod -a -G <group> <username>
```

I'm not quite sure what groups you need to add yourself to in order to use sudo though, maybe someone else will list them.

As you already noted, when you go into recovery mode the system is read-only, see:

[http://ubuntuforums.org/showthread.php?t=1870817](http://ubuntuforums.org/showthread.php?t=1870817)

What is the timestamp of the group file that may tell you when it was changed and does it coincide with the installation date of your VirtualBox?

---

### Post by Lars Noodén on 2012-04-18
That would be [gpasswd](http://manpages.ubuntu.com/manpages/oneiric/en/man1/gpasswd.1.html)

```

gpasswd --add lee sudo

```

---

