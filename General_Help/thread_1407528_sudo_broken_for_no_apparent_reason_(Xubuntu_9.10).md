---
title: "sudo broken for no apparent reason (Xubuntu 9.10)"
date: 2010-02-15
forum: General Help
---

### Post by BeardlessForeigner on 2010-02-15
I found a simlar problem several times in the search results with no real resolution. When I try to use sudo I get the following:
```

user@ubuntu:~$: sudo vim
sudo: can't open /etc/sudoers: Permission denied
```

Trying to run gksu just hangs for a bit then exits. The permissions of /etc/sudoers are fine: 
```

user@ubuntu:~$: ls -l /etc/sudoers 
-r--r----- 1 root root 557 2010-02-15 /etc/sudoers
```

Using visudo logged in as root (through a recovery login) I confirmed that /etc/sudoers still has the default contents. The user is in the admin group. What's more, if I am logged in as root and try to run sudo I get the same result.

This is a new install. All that happened between sudo working and sudo not working is that I ran 'sudo thunar' in order to change the group and permissions of a folder '/mnt/backup'. After I did this, I started getting the problem.

One thread asked about a '/var/run/sudo' file, which does not exist on my system. I have not messed with this however since it does not seem like something a user would normally create/edit.

Edit: I also tried reinstalling sudo with 'apt-get install --reinstall sudo' while logged in as root , but nothing changed.

Thanks in advance for any help or ideas.

---

### Post by rnerwein on 2010-02-15
hi

whats about the permissions of /usr/bin/sudo ?
should be: [COLOR=Red]-rwsr-xr-x 1 root root[/COLOR] 143656 2009-06-22 18:15 /usr/bin/sudo

if they are not correct sudo can't open /etc/sudoers

oh forget it - i just saw you have already reinstalled sudo - sorry
ciao

---

### Post by BeardlessForeigner on 2010-02-15
I also checked the permissions of /usr/bin/sudo before I reinstalled and they were correct, I just forgot to mention it. Thanks for trying ;)

---

### Post by BeardlessForeigner on 2010-02-16
Ok, I seem to have got it sorted out. I found a post on another forum where someone else fixed it by running "chmod 0755 /". This did the trick for me. I was a bit skeptical since "ls -l /" seemed to show ok permissions, and I only changed permissions before on "/mnt/backup", but sudo works now. 

So in short, someone else with this problem could try refixing the permissions on /. Hopefully that didn't mess anything else up, but the system seems ok for now.

---

