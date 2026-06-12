---
title: "Permision issues External HD"
date: 2011-06-05
forum: General Help
---

### Post by nextstopearth on 2011-06-05
I have a 2 TB external firewire hard drive that I am trying to access over the network from windows and ubuntu machines. I am having trouble accessing it and I think it is due to the permissions set on the external drive. 

If I 

ls -la

It shows that the drive has rwx permisions for the owner but none for anyone else. If I 

sudo chmod 777 /media/harddrive

nothing is output but if I check the permissions again, they remain unchanged. Does anybody know what the problem is? Thanks.

---

### Post by garvinrick4 on 2011-06-05
Is it drwx and a NTFS or are you formatted in ext ?

---

### Post by garvinrick4 on 2011-06-05
If want to see from windows box  using samba in linux box. open your /etc/samba/smb.conf
in root and add to bottom of file as such below and save: click on thumbnail. comment is whatever you want to call it.
Edit: This is for making samba shares, I have not worked with firewire so really should not have commented on that.

---

### Post by nextstopearth on 2011-06-06
> **garvinrick4 said:**
> Is it drwx and a NTFS or are you formatted in ext ?

Yes, it is drwx for owner and formatted as NTFS. Windows machines seem to be able to see it, just not access it without logging on to the windows machine with the same login name as the linux machine. Even then it still wants a password when accessing it the first time, which I would like to avoid.

---

