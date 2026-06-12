---
title: "USB memory stick won't load without a restart"
date: 2011-05-10
forum: General Help
---

### Post by Robbyx on 2011-05-10
What can I do to correct the failure of the mount command to load the mem stick. 

In nautilus it reports that I do not have the permissions necessary to view the contents of "Kingston"

In user settings there is only one user: Robin. The user privileges are showing as all ticked except for send and receive faxes, and use tape drives.

In the group for Robin there is only one member: Robin. Group id is 1000. There are a lot of groups available on the system. They al show Robin as unticked as a group member.

To what groups should I make  Robin be a member, without compromising security?

Using Ubuntu 11.04

---

### Post by TheNerdAL on 2011-05-10
This might help: 

> **northern lights said:**
> _Never_ run graphical apps with 'sudo'. Use 'gksu' in gnome/xfce and 'kdesu' in KDE.

If you want to open directories as root, please use ```
gksu nautilus /path/to/directory
```


As for the actual problem, opening 'work2' as superuser should not be necessary. It's not like that's systemfiles. Run ```
chown -R USER /media/work2
```to give you permission. USER obviously needs to be replaced by your username and you might also want to check whether it's really 'work2' in /media.

---

### Post by Robbyx on 2011-05-10
What do you think about the lack of groups attached to my username?

Re your comment about. There is no entry as work2. the mem stick is showing as KINGSTON (in caps).

So I assume this is what I should apply:
chown -R robin /media/KINGSTON

But will it remain if I remove the stick and put it back in again?

Are you sure it wouldn't be better to somehow add me to another group which does have the permission to open mem sticks?

---

### Post by TheNerdAL on 2011-05-10
> **Robbyx said:**
> What do you think about the lack of groups attached to my username?

Re your comment about. There is no entry as work2. the mem stick is showing as KINGSTON (in caps).

So I assume this is what I should apply:
chown -R robin /media/KINGSTON

But will it remain if I remove the stick and put it back in again?

Are you sure it wouldn't be better to somehow add me to another group which does have the permission to open mem sticks?

You don't need work2. And yeah, you should apply that and idk if it will remain. Try it and see if it does. And you are the only user in the computer, right? So, you should be the Administrator.

---

