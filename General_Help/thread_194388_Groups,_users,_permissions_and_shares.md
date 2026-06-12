---
title: "Groups, users, permissions and shares"
date: 2006-06-11
forum: General Help
---

### Post by danmonkey on 2006-06-11
I'm setting up a system (edubuntu) for my sister and her family and what I'd like to do is the following:
- All users to be in the same group
- No user to have access to administration tasks
- A shared folder which anyone in the group can have read/write access (and for any folders/items created within it to automatically have read/write access at group level).

I've done the first one.  I'm not sure about the second one - would this prohibit automatic updates?
I'm not sure how to set up a shared folder for a group.  I've attempted to do this, but if someone in the group creates a new file/folder in it, it only has owner write privilages.  Is there a way to make anything created in a shared group folder read/writeable for the whole group?  Also - where's the best place to create this folder?

Any help much appreciated!

---

### Post by Rui Pais on 2006-06-11
hi, 
at least one user must have administrative powers, maybe setting an account for yourself with a good password, or setting an account for root (thats what most distro do but ubuntu scheme with sudo is at imho far better). 
Just make shure that only you (or root) can excute administrative tasks.
Thats easy to do with sudo users-admin, for each user check:
 Properties -> User privileges -> Executing system administration tasks.

Now about upgrades. To do upgrades its necessary admistrative poweres (upgrade changes parts of the system). But you can give access to only apps specific. For security matters give access to synaptic is not good idea. An user thatcan access synaptic can add experimental repositories, install deb download from net with god knows what. But update-manager is nice cause it allows users to keep system up-to-date, without so many power. Just do:
sudo visudo
and add the line:
> %users ALL=NOPASSWD: /usr/bin/update-manager
assuming that users are the group that you set to all your users.

To a shared folder, do (or has root)
```
sudo mkdir /home/all
```
(or what other name like /home/My Computer)
then 
```
sudo  chmod a+rwx /home/all
```

Now, as far as i know, if someone creates a folder but make it not visible by others, the folder belongs to he/her... he/her have that right :) 
If the owner didn't not set any special permition, since they belong to the same group, they could see and read all from each other.

hth

---

