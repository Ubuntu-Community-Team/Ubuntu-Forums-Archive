---
title: "Group rights"
date: 2006-04-01
forum: General Help
---

### Post by draenor on 2006-04-01
I'm having some issues setting system for groups on my computer. I'm looking to close up upon how to setup a server with plenty of users, and a step in the right direction is to configure groups properly. 

I have user1 @ Group Members (The only user at group Members)
I need to edit /dev folder for my group so I can't access it. Since it's a root folder I need to be able to access sudo. 

I need to restrict /dev from user1. I've added sudo to user1 using visudo, to avoid getting into the admin group. 

```
su user1
sudo chmod g-rwx /dev
ls -al | grep dev 
```

Rights have been edited, however changing back to my default user, the same rights have been changed there as well ..
So I check if if we share some group, I find that we dont: 
```

sudo cat /etc/group  | grep user1  # All is well, user1 is a member of Members only
sudo cat /etc/group- | grep user1  # same

```

So why is there that chmod g+r file changes rights for both user1 and user2, neither sharing groups ?


A little bit off topic, but I came to think of it while typing. How come creating a separate partition for memory (is it pagefile in linux too ?) gives greater performance that having it on the same partition (Given it's the same harddrive) ?.


*[COLOR="Red"]EDIT:[/COLOR]* 
Perhaps it's because /dev belongs to root? Setting chmod g-rwx still gives me the right to list contents of the directory, does that mean 'all' or 'user' has higher access than 'group' or is it simply because 'group' is root ? I'm a little confused :P

---

