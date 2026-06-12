---
title: "Samba share security setup owner versus other"
date: 2010-02-13
forum: General Help
---

### Post by Slates on 2010-02-13
Ive set up samba on Ubuntu 9.10. I have a windows USB hard drive that I have connected to my Ubuntu server. Ubuntu recognises it and its listed under /media. The owner is listed as the logged on user slates under ls -l, as is the case for all the files therein.

I have edited smb.conf, changed the workgroup to the windows one Im using and added entries for my share to disalow guest access. 

When I browse to the shared folder from windows (XP or 2000) I see the share. Im prompted for my password. I enter slates and my Ubuntu password and access is granted.

However I would like to grant access under a non-admin user. So I created a user call Samba. 

But when I try to access the share under this user, it fails with "the network name cannot be found". I have the username and password correct (and I did a password reset to be sure)

So I edit smb.conf and add valid users = slates, samba and restart samba.

No change.

So I try the GUI samba server configuration. I check Slates and samba for access.

No change.

I click allow access to everyone instead.

Now Im told (in windows) the network path was not found.

I uncheck it, and it returns to prompting me for a password, but only allows access for slates and not for samba.

The Samba log tells me the reason was permission denied. This doesnt surprise me at a basic level since, since the shared drive is listed as being owned by slates with permissions for only the owner. I cannot chnage these (ie cannot add group or other permssions) but Im guessing this is because its managed by samba.

Can someone please point me to why Im getting permission denied (when Ive added access via the GUI) ?

 

Im unsure of which steps are necessary

---

