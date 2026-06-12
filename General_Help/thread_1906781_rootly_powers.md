---
title: "rootly powers"
date: 2012-01-09
forum: General Help
---

### Post by conradin on 2012-01-09
Hai All, 
I want to set up a bunch of users. Three users having the power to add or remove programs, but not change things like the kernel, and to administer control for users in their sub directories. I do not want these users to be able to control the overall system operation however. Just their environment, and any sub users (limit users) they may wish to create. 

How Might I go about this.?

I am using Ubuntu 10.10, and wish to do this via the command line.

---

### Post by 1clue on 2012-01-09
You Might Like to Take a Look at Sudo and Sudoers.

---

### Post by 1clue on 2012-01-09
You might also like to make a backup of sudoers before you go messing with it.  And maybe define a root password just in case, either that or have a system rescue CD handy to boot from.

Don't just start at the bottom of the manual page either, go into it carefully.  Your user's ability to install software and do anything special is granted by sudoers.

---

### Post by conradin on 2012-01-09
So where in /etc/sudoers file, and %sudo ALL=(ALL) ALL 
I would like sudo ALL=(SOME) ALL
or something like that? I get changing the root password, but not how to restrict the admin privileges via the sudoers file.

---

### Post by CharlesA on 2012-01-09
> **1clue said:**
> You might also like to make a backup of sudoers before you go messing with it.  And maybe define a root password just in case, either that or have a system rescue CD handy to boot from.

Don't just start at the bottom of the manual page either, go into it carefully.  Your user's ability to install software and do anything special is granted by sudoers.
+1.

Take a look at the page here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by topsites on 2012-01-09
To my understanding the way to approach this would be to chmod the entire appropriate directory trees intended for the users to whom you wish to assign certain levels of access, leaving the rest of the drive off limits.
At least I am pretty sure chmod can be used recursively.

Although it doesn't quite answer the question, I thought I'd point that out.
And there may exist other methods...
[https://help.ubuntu.com/11.04/serverguide/C/user-management.html](https://help.ubuntu.com/11.04/serverguide/C/user-management.html)

---

### Post by 1clue on 2012-01-09
Hmm, go get some of whatever makes you relax a bit.  It gets a bit fuzzy here.  I'm not going to explain it all because I can't.  I can do it but not explain it, and if you do it on your system you need to know what happened, this is core security for you so you don't really want to take some stranger's word for it if you know what I mean.

First thing, if you grant too much authority then you'd just as well publish your IP address and root password on the forum here.  You're very right to limit the grants.

Second thing, always require a password.  Sudoers allows no password, but that's ridiculous.

Now, look in /etc/group.  There's an 'admin' group in there, and your system's first user (the one you created when you installed Ubuntu) is in there, and probably nobody else.  Those guys can 'sudo' and be root.  The easiest thing you can do to gain authority is to add some user to 'admin' and they will be able to be root, but only after they log out and log back in, if they were logged in when you made the change.

Now for the setup you're talking about, you need to set up lists in sudoers.
[LIST=1]
[*]You have a list of what I like to call roles, such as your user admin role.  This is the membership of people who can do any category of things.  They call this User_List.
[*]You have a list of commands for some role.
[*]You have a runas_<something>, which is the user or group the commands should be run as when somebody sudo's it.
[*]You have a host list, which is the list of hosts from which the command can originate.
[/LIST]

For example, you could cause **sudo adduser bob** to be run as root, or as the admin group, or as some other user who has authority if you messed with command permissions directly.

By the way, that was NOT an idea.  Don't mess with file permissions of system commands.  It's a surefire way to reinstall your system after days of frustration.  Ask me how I know.

---

### Post by 1clue on 2012-01-09
> **topsites said:**
> To my understanding the way to approach this would be to chmod the entire appropriate directory trees intended for the users to whom you wish to assign certain levels of access, leaving the rest of the drive off limits.
At least I am pretty sure chmod can be used recursively.

Although it doesn't quite answer the question, I thought I'd point that out.
And there may exist other methods...
[https://help.ubuntu.com/11.04/serverguide/C/user-management.html](https://help.ubuntu.com/11.04/serverguide/C/user-management.html)

I hate to be rude, but NO!

Don't chmod anything relating to system-installed commands.  You can do this with data directories, but using chmod or chgrp without knowing exactly what you're doing is going to lead to a really unhappy experience.  You can do it with a directory of scripts which you wrote, but don't try it with system stuff.

Linux permissions have evolved over years and have been carefully designed by people who know what's going on.  You can use several mechanisms to allow or deny permissions.

The most frequently used is sudoers.  There is also 'hardened' linux with access control lists.  I can't help you there, I've never had a real reason to mess with it, and no time to do it just on a lark.

---

