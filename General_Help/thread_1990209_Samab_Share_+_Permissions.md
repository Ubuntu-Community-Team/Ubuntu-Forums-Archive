---
title: "Samab Share + Permissions"
date: 2012-05-29
forum: General Help
---

### Post by chrislynch8 on 2012-05-29
Hi,

First of all not sure if this is the correct location to post this question but here goes.

I have a samba shared central. In central I have 5-6 folders that users access. I want to setup permissions on one of that will only allow the following. A User can view all files in the folder, a User can write to the folder but the User cannot delete anything in the folder.

Is this possible on a Linux Machine?

Rgds
Chris

---

### Post by Morbius1 on 2012-05-30
> I want to setup permissions on one of that will only allow the  following. A User can view all files in the folder, [COLOR=Blue]a User can write to  the folder[/COLOR] but the User cannot delete anything in the folder.Define "write" please.

If by "write" you mean that a remote user can add to the share then you could try something like this example:

[1] Create a directory as root:
```
sudo mkdir /mnt/Test
```[2] I'm going to create a guest accessible share in this example so I need to change permissions. I will also add the "sticky bit" to the folder restricting the deletion of any of it's contents to the owner of the file :
```
sudo chmod 1777 /mnt/Test
```[3] Now I will create a share that will force all added files / folders to inherit the ownership of the parent directory ( which is root in this case ):
> [Test]
path = /mnt/Test
read only = no
guest ok = yes
[COLOR=Blue]inherit owner = yes[/COLOR]
create mask = 600
directory mask = 700
directory security mask = 700Somewhat convoluted perhaps but it's the best I've got at the moment.

Note: I've assumed by "write" you mean the ability to add to the share not the ability to "edit" the contents of the share.

***[COLOR=Blue]EDIT[/COLOR]**: Step [3] was silly, I think I went too far - the remote user can't even read the contents of a file. Try this instead:*
> [Test]
path = /mnt/Test
read only = no
guest ok = yes
[COLOR=Blue]inherit owner = yes[/COLOR]
create mask = 644
#create mask = 666 <- Another option in case by "write" you also mean edit the file.


---

### Post by chrislynch8 on 2012-05-30
Hi Morbius1,

I completely forgot about the sticky bit, that will solve my issue. 

Rgds
Chris

---

### Post by chrislynch8 on 2012-05-31
OK - so one final problem,

I have the samba share now setup correctly. When A user on the Local Network puts file into it they cannot delete the file, which is great.

I have 25 server connected to this main one via a VPN, the shared folder is shared with the other servers via NFS and then on the remote server samba is used to share the NFS folder to local users. 

I users from the remote offices put files into the shared folder the inherit owner = yes is not applied and the file takes the owner of the person that has put the file into the share.

I have the inherit owner set up on the remote samba server also. Is this possible or will I have to set up a script that will always apply the correct owner to the shred folder?

Rgds
Chris

---

