---
title: "Why aren't users members of their own groups?"
date: 2011-04-10
forum: General Help
---

### Post by wyth on 2011-04-10
This is just a general question I've had for some time, because it just doesn't make sense to me, and I've never found an explanation.

Whenever you create a user, a group is also created for that user. If a different user -- say an administrator -- needs access to some other user's files, you can become a member of that user's group.

But why aren't users members of their *own* groups by default? And are there any implications or even differences if you go into group settings, find a user's group, and make a user an active member in their own group?

In other words:

[LIST]
[*]Hostname AJAX has two users, Flash and Ming
[*]There is a Flash group for user Flash, and  a Ming group for user Ming
[*]Inside the group settings for Flash are options to make the users Flash or Ming members of the group Flash or the group Ming.
[*]By default, user Flash is not shown as a member of group Flash, nor is user Ming shown as a member of group Ming.
[/LIST]

Huh? Questions:

[LIST]
[*]Why isn't Flash a member of the group Flash, or Ming a member of the group Ming? 
[*]Is it redundant for users to be members of their own groups? In other words, isn't user Flash automatically a member of group Flash? 
[*] If so, why isn't user Flash shown to be an active member of group Flash under the group settings?
[*]I'm assuming the name of user Flash is visible under the group Flash because there may be a second user named Flash (with their own group). But that just re-raises the question: 
[LIST]
[*]Why not just show user Flash -- whose group is also Flash -- as either already ticked on as a member in the group settings, 
[*]Or just not make that user's name visible at all under the group settings if they're a member of their own group by default?[/LIST]
[*]If there are any implications to making users members of their own groups, what are they?
[/LIST]

So: Any insights?

---

### Post by bab1 on 2011-04-11
> **wyth said:**
> This is just a general question I've had for some time, because it just doesn't make sense to me, and I've never found an explanation.

Whenever you create a user, a group is also created for that user. If a different user -- say an administrator -- needs access to some other user's files, you can become a member of that user's group.

But why aren't users members of their *own* groups by default? And are there any implications or even differences if you go into group settings, find a user's group, and make a user an active member in their own group?

In other words:

[LIST]
[*]Hostname AJAX has two users, Flash and Ming
[*]There is a Flash group for user Flash, and  a Ming group for user Ming
[*]Inside the group settings for Flash are options to make the users Flash or Ming members of the group Flash or the group Ming.
[*]By default, user Flash is not shown as a member of group Flash, nor is user Ming shown as a member of group Ming.
[/LIST]

Huh? Questions:

[LIST]
[*]Why isn't Flash a member of the group Flash, or Ming a member of the group Ming? 
[*]Is it redundant for users to be members of their own groups? In other words, isn't user Flash automatically a member of group Flash? 
[*] If so, why isn't user Flash shown to be an active member of group Flash under the group settings?
[*]I'm assuming the name of user Flash is visible under the group Flash because there may be a second user named Flash (with their own group). But that just re-raises the question: 
[LIST]
[*]Why not just show user Flash -- whose group is also Flash -- as either already ticked on as a member in the group settings, 
[*]Or just not make that user's name visible at all under the group settings if they're a member of their own group by default?[/LIST]
[*]If there are any implications to making users members of their own groups, what are they?
[/LIST]

So: Any insights?

The basic answer is that there is no need for a user to belong to a the default group of the same name.  It is a place holder that by default allows file creation permissions of read and write (rw) for both the user and that group (a function of umask of 022).  

In essence this allows only the user to read and write to the file.  It would be redundant add the user to the same name group (i.e. john:john) as it would not add to the users abilities to manipulate the file.

The same notion applies to the directory permissions.  The umask makes the default permissions 755 (rwx r-x r-x).  This means the user (owner can read/write/traverse the directory.  The group and all others can read and traverse the directory.  Adding the user (owner) to the group doesn't help the user in this instance the permissions are less in the group.

In my opinion the self named group is really for use by single host (computer) or a casual user.  In a larger multi-user centrally managed system groups are how you arrange like minded users (i.e sales, management, chemistry, etc.).  In this scenario the owner (user would by default have rw and the members of the group would also have rw permissions.  Since there would be others in the group that would be able to create files and all users would need to have rw permissions: **[B]all**[/B] relevant users would need to be added to the group.

---

### Post by wyth on 2011-04-11
Cool, that helps clear things up. So in short -- say a home network -- it's not necessary for a user to belong or not belong to their own group, but it's not the case that the option is pointless. 

I think I can mark this solved.

---

### Post by bab1 on 2011-04-11
> **wyth said:**
> Cool, that helps clear things up. So in short -- say a home network -- it's not necessary for a user to belong or not belong to their own group, but it's not the case that the option is pointless. 

I think I can mark this solved.

It will help you if you don't think of the group as *the users group *.  No user *has a group*.  The user can be a member of any group, including the group that is named the same as the user.  I would say that in this case the option *is pointless*,  but it is not harmful.

---

