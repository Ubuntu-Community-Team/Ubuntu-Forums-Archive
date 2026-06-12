---
title: "Unable to access linux(ubuntu 10.10) share drive on my windows PC"
date: 2011-06-29
forum: General Help
---

### Post by Barada on 2011-06-29
Unable to access linux(ubuntu 10.10) share drive on my windows PC
In my office we have few linux (obuntu 10.10) computers and 3 computers running on windows. We have data stored on one of the shared drives of a linux(ubuntu 10.10) system which has samba installed and we are able to access that folder from other linux systems and 1 windows xp system where it asks for user name and password and is able to access the data while in other 2 windows systems (with 1 having xp and 1 having windows 7) we are unable to access the folder because it does not ask for user name and password and it shows an error network drive not accessible as you may not have the permission. 
Can anyone please suggest as to how we can access this data stored on linux system from a windows PC in a network.

---

### Post by nzjethro on 2011-06-29
Hi Barada, welcome to the forums. What are the file types of your systems? I know Windows will be a ntfs, which can be read and written to by Linux systems. However, it is likely that your Linux partition will be formatted as ext4. This filesystem cannot be read by Windows OSes. To check, type into a terminal

```
sudo fdisk -l
```
(that's a lower case L). This will tell you your filesystems (ntfs or Linux/ext4).

---

### Post by Barada on 2011-06-29
u can;t understand my problemmy problem is thatwhen i access the file server it does not ask for user name and password and it shows an error network drive not accessible as you may not have the permission.

---

### Post by seawolf167 on 2011-06-29
You'll have to take a look at your Samba configuration file

```
gksu gedit /etc/samba/smb.conf
```

Some things you should check:

[LIST]
[*]do you have guest access enabled?
[*]is the shared path browse-able?
[*]do you have your valid users/groups set correctly?
[*]is the share path public?
[/LIST]
You can try clearing the saved passwords on your windows machine using the keymanager and see if it re-prompts for a password. Its been a while, but I think the command is:

```
rundll32.exe keymgr.dll, KRShowKeyMgr
```

then clear the appropriate passwords

---

