---
title: "moduser Causes Groups Not To Be Recognized"
date: 2006-05-31
forum: General Help
---

### Post by dsantin on 2006-05-31
I saw some similar threads about this, but I didn't see any recovery strategies for my particular problem and I really hope someone can help.  Here goes:

I was remotely administering my machine and created a group svn (I was installing subversion).  I then used "sudo usermod -Gsvn dsantin", which promptly removed me from every other group.  Once I got physical access, I rebooted into the recovery console and found the previous group file /etc/group-, which I assume was created right before my little usermod experiment.  I diffed group and group- and saw only that I'd been deleted from most of the groups, so I moved /etc/group somewhere else and moved /etc/group- to /etc/group.  This, I assumed, would reinstate my group membership.

I can sudo again, so that tells me I was partially successful.  However, every time I run the "groups" command, I get the following output;

id: cannot find name for group ID 1000
1000 id: cannot find name for group ID 4
4 id: cannot find name for group ID 20
20 id: cannot find name for group ID 24
...
etc.

Additionally, doing an "ls -l ~" shows the gid of all those files as 1000, instead of the usual group name "dsantin".  It looks like my groups have lost association with their gids, I'm assuming because of usermod.  Is there a way to recover without reinstalling?  I'm really hoping there is.  If anyone can help, I'd really appreciate it.

EDIT: It would also be helpful if I got the name of the command right.  Man, I'm dumb today.

---

### Post by tonyr on 2006-05-31
Did you reboot after replacing /etc/group?

**moduser** is one of the low level utilities that does exactly what you
saw: replaces the current group membership with the specified group
membership.  The man page is not quite clear on this, but the correct syntax
for what you wanted to do appears to be
```

sudo usermod -g <primary-group> -G <list-of-all-other-groups> username

```

The preferred method for adding an existing user to an existing group, without
wiping out the previous membership definition, is
```

sudo adduser user group

```

I'm attaching my **/etc/group** file (from my Dapper installation) for comparison.

EDIT: Actually, all it may require to regain your correct 'groups' response is to
logout/login.

---

### Post by dsantin on 2006-05-31
First, thanks for your response.  I'm tearing my hair out here.

[QUOTE=tonyr]
Did you reboot after replacing /etc/group?
[/QUOTE]

Yes.  It hasn't made a difference.  Executing "groups" still says that id cannot find name for group ID #### (insert gid here).

I compared my group file to yours.  I can't see any significant differences, other than my name appears before some of the system-defined users like "hal" and "cupsys".  This is what makes me think the problem lies elsewhere.  I've attached my group file in case you see something I don't.

---

### Post by tonyr on 2006-05-31
Something to check:  on my system, the permissions on **/etc/group-** are
**-rw------**.  The permissions on /etc/group are **-rw-r--r--**, with
owner/group == root/root.

---

### Post by dsantin on 2006-05-31
I figured out the problem.  /etc/group wasn't readable by anyone other than root.

Thanks for your help, Tony.

EDIT: That was weird.  :)

---

