---
title: "Configure Samba for use with Active Direcotry users/groups"
date: 2010-12-13
forum: General Help
---

### Post by gunther123 on 2010-12-13
I am trying to setup an Ubuntu 10.10 desktop box to share a folder using Samba.  My environment consists of Windows Active Directory (AD) and some Windows clients.  I would like to configure Samba to recognize the AD users and groups.

So far, I have installed Likewise Open and integrated the Ubuntu box to the AD.  I am able to login to Ubuntu using an AD user.  I am also able to access Windows shares from my Ubuntu box, so the AD integration seems to be working fine.

I have also installed Samba and setup a file share.  I can see the file share from my Windows box but it seems that the only access level I have to the share is in regard to the "other" permission.  The owner of the share is my AD user and the owner has read/write access.  When I access the share from my Windows box and I am logged into the Windows box as my AD user, I still only have the "other" permission which is read only.  If I change the "other" permission to read/write, then when I access the share from my Windows box, I have read/write access.

I'm pretty sure that my hang up is configuring Samba to recognize/use the AD users/groups.  I have found several references to configuring Samba but I haven't found anything with enough detail on this particular subject.  Additionally, I have found several different options for configurations and each option has its own set up software packages to use.  I'm uncertain as to which option is the most appropriate for Ubuntu 10.10 and my situation but they all seem to be overly complicated.

Can anyone point me in the direction of some instruction on how to configure Samba for my needs and that is appropriate for my environment?

Thank you in advance.

---

### Post by gunther123 on 2010-12-17
So I was able to setup a share on Ubuntu.  I was able to access the share from my Windows boxes.  I got Ubuntu added to my Active Directory (AD).  I was able to login to Ubuntu using my AD account.

Now...  When I am logged in with my AD user and setup my share, the owner of the share is my AD user.  The only groups that I can configure for the share are the groups that my AD user is a member of on the Ubuntu box AND the "domain users" AD group.  My AD user is a member of other AD groups but these other groups do not show up as a possible option for my "Group" setting.

I am a bit new to permission in linux.  Perhaps I am overlooking something simple.  I want to be able to configure my share permissions with an AD group.  How do I do this?  My ultimate goal is to configure the share so that AD users can access the share from Windows boxes without having to enter in credentials.

---

