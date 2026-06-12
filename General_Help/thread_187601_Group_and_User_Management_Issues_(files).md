---
title: "Group and User Management Issues (files)"
date: 2006-06-03
forum: General Help
---

### Post by Raghnall on 2006-06-03
“Help, I need somebody,
Help, not just anybody,
Help, you know I need someone, help.”

Ok, I’m getting desperate. I have searched the forums on both Ubuntu and Kubuntu and haven't found anyone with a similar problem.

I'm configuring a web server with each user having their own htdocs root. I also need the htdocs root to be writeable by apache2 (www-data). I first try to set the ACL on the htdocs folder to owner: user and group: www-data both with read and write access. works... ok, but I need the sub folders to inherit the parent folder permissions. So I try to set the set-GID and set-UID bits, I can set the set-UID bit but the set-GID bit doesn't seam to want to stick.

so I try to do some group management. (I had earlier tried to add my users to the www-data group but came across a thread that said I shouldn't do that). So I decide to make my own group that www-data and the users are both in and setting the GID on the htdocs folder to that, this is where my problem begins. when i try to change the GID to that of the new group (www-group) it tells me that i do not have permissions to do so (same as when i tried with users in www-data). my users are in the new group, I made sure through GUI interfaces ((k)ubuntu) and also made sure through cmd. I have tried creating the group through cmd and through GUI, adding the users through cmd and GUI, and adding the users manually through editing /etc/group and if needed be /etc/gshadow(-). 

Still no luck.

Also when I try to add a user to my new group with "adduser myuser www-group" it tells me that I am already in the group, but when I run "groups" it doesn’t show www-group as one of the groups I am in. I know I must be missing something.

I have also thought of adding www-data to my users group, but decided against it because I only want apache to have write access to htdocs.

I'm sure if I can get the group management issue fixed the set-GID bit will fall into place. again I have tried this on both kubuntu (my actual server) and ubuntu (my intranet fileserver and my laptop).
Now off to bed.

---

