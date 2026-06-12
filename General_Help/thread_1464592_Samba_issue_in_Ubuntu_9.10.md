---
title: "Samba issue in Ubuntu 9.10"
date: 2010-04-28
forum: General Help
---

### Post by chngck on 2010-04-28
I have configure few folders access by 3 users, In common folder only users that create that document can do changes. The rest of the users can only read the file but can not do changes.

Ownership of the folder is admin, group is sambashare which already have the access create and delete files. All the 3 users already in sambashare main group, and they only can edit the file that they copy or create to the common folder .........

Can anyone have any idea what i have done wrong?

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
[Permissions issue...]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by chngck on 2010-04-28
> **Sin@Sin-Sacrifice said:**
> [Permissions issue...]("https://help.ubuntu.com/community/SettingUpSamba")


You mean.......

**Setting permissions**

 To set permissions of newly created documents / files edit /etc/samba/smb.conf and in the [global] section add : 

create mask = 0644
directory mask = 0755I think I do not see those line in smb.conf ........ hmmm, I try it tomorrow morning. Thanks for you help :)

---

### Post by Morbius1 on 2010-04-28
I'm not 100% sure that I understood your post but you haven't done anything wrong. It's working just like it should.

It sounds like you created a Folder on the server,  /share for example, and it has the following permissions:

owner=admin
group=sambashare
mode=0770

Any remote user that adds a file will have the permissions set as 
owner=remote_user_x
mode=0755

Only remote_user_x will be able to edit that file and all other will only be able to read.

If you want all users to be able to read and write to the file then have it "inherit" the permissions set at /share itself:

Add the following lines to the share definition in smb.conf:

```
inherit permissions = yes
force group= sambashare
```When the remote user adds a file:
owner=remote_user_x
mode= 0770

[COLOR=Blue]EDIT: Of course this assumes that all remote users are member of the sambashare group.
EDIT2: Need to add a force group = sambashare - sorry about that. Need to remember to think it through, then post [/COLOR]:oops:

---

### Post by Morbius1 on 2010-04-28
Actually there is another way to do this. 

You could add the following line to the share definition:
```
force user = admin
```When remote_user_x gains access by samba he will be converted to "admin" as far as that share is concerned. Then it doesn't matter who tries to write to a given file as long as they have properly authenticated themselves to samba.

---

### Post by chngck on 2010-04-29
Thanks, issue solve by adding in 
 
[Global]
........
inherit permissions = yes
force group = sambashare
 
:P:P:P:P

---

