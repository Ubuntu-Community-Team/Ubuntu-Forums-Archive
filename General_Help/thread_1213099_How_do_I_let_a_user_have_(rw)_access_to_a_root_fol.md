---
title: "How do I let a user have (r/w) access to a root folder?"
date: 2009-07-14
forum: General Help
---

### Post by Nazaroo on 2009-07-14
I copied a folder from 2nd HDisk to root account, so that I could then let other users access the common files. (I have to remove the 2nd drive afterward.)

According to the file browser, it is in 'root/Desktop/Public'.

When I log in as another user, it doesn't show up, or else I don't know how to find it.

What is the missing step or key bit of knowledge I need to read/write to this folder (full of html and .jpg files) from the account of another ordinary user?

Second supplementary question:

I have a folder on the Desktop of root:  Can I make that accessible (r/w) to another user?

common file sharing folder would save a lot of headaches here.


thanks 
Nazaroo

---

### Post by michy99 on 2009-07-14
/root is not a good place to put these files. It would be better to set up a new folder in / and set the permissions so others can access it. For example, if you want to call it data:```
sudo mkdir /data
sudo chmod 777 /data
```

---

### Post by mikewhatever on 2009-07-14
Do you realize you've made it that complicated by enabling root account? Anyway, look at man chmod for solutions.

---

### Post by CatKiller on 2009-07-14
> **Nazaroo said:**
> common file sharing folder would save a lot of headaches here.

Exactly, and root's Home folder isn't it. Put it somewhere else. /home/data might be a reasonable place, since that's just one click on the up button from any user's Home folder, but anywhere can work. You could also put symlinks in each user's Home folder to wherever you've put this folder, or bookmark that location for each user so that it shows up on the Places menu.

---

### Post by Nazaroo on 2009-07-14
> **michy99 said:**
> /root is not a good place to put these files. It would be better to set up a new folder in / and set the permissions so others can access it. For example, if you want to call it data:```
sudo mkdir /data
sudo chmod 777 /data
```


okay lets say I create a /data folder in folder holding the users (/home ?):

Does that make it automatically visible to all users afterward?  Will that become the "Public" folder for users of the computer?, and if so, why isn't there a default folder like that named "Shared" or "Public" or "ALL USERS" prebuilt into an install?  Seems like a no-brainer...

confused,
Nazaroo

---

### Post by michy99 on 2009-07-14
Maybe it will make things clearer if you explain what you want to put in this folder. 

Who can access a folder is controlled by the permissions set on the folder. In the example above, chmod 777 /data will give everybody read, write, and execute permissions for the folder.

Another possibility is to create a separate partition for data and make it accessible by all users.

---

### Post by michy99 on 2009-07-14
Something else I just thought about. Linux (and all unix derivatives) is set up to be a multi-user system from the beginning. That means that there has to be control over what each user can access to protect each users data.

---

### Post by Nazaroo on 2009-07-14
> **michy99 said:**
> Something else I just thought about. Linux (and all unix derivatives) is set up to be a multi-user system from the beginning. That means that there has to be control over what each user can access to protect each users data.

Let me explain:

(1) In this case the data is meant to be accessible and editable by all parties (whoever is volunteering to keep a website updated).

(2) Only one user at a time can use the computer, so there can be no conflict re: open files being edited by two people at once.

(3) Most of the users will be either extra users (duplicate accounts) or users just set up for this purpose (editing the material in this folder).

So 'security' issues are not paramount here, but rather ease of access and keeping code in sync with internet copy of files.

The material will all be 'open copyright', i.e., either we own the copyright or it is covered under the GNU agreements.

thanks 
Nazaroo

---

### Post by Nazaroo on 2009-07-14
> **michy99 said:**
> Maybe it will make things clearer if you explain what you want to put in this folder. 

Who can access a folder is controlled by the permissions set on the folder. In the example above, chmod 777 /data will give everybody read, write, and execute permissions for the folder.

Another possibility is to create a separate partition for data and make it accessible by all users.


In any case, this system doesn't sound very secure, since what one would want is individual settings on a folder for each user, if security is the issue.  If "777" gives everyone access, then how do you give just "some" access?  Maybe I missed something but...

---

### Post by bodhi.zazen on 2009-07-14
> **Nazaroo said:**
> In any case, this system doesn't sound very secure, since what one would want is individual settings on a folder for each user, if security is the issue.  If "777" gives everyone access, then how do you give just "some" access?  Maybe I missed something but...

Use acl

---

### Post by michy99 on 2009-07-14
There are three sets of permissions on each file or folder, One set for the owner, one for the group, and one for others. It sounds like you want to set up a group and have those users who should have access to be members of the group.

This page may be of some help:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by Nazaroo on 2009-07-17
> **michy99 said:**
> There are three sets of permissions on each file or folder, One set for the owner, one for the group, and one for others. It sounds like you want to set up a group and have those users who should have access to be members of the group.

This page may be of some help:

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Thanks for the link.  I will read the manual...:)

---

