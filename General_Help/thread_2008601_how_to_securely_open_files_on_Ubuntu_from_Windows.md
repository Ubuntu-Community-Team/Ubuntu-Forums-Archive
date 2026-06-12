---
title: "how to securely open files on Ubuntu from Windows?"
date: 2012-06-22
forum: General Help
---

### Post by anon0 on 2012-06-22
I wish to access certain files on Ubuntu from the network, but I also wish to avoid security risks. Right now I've edited /etc/samba/smb.conf to share the directory, which allows me to open the files directly in Windows, but this means that anyone who has access to Windows can open the files, which is not safe. What would be some safer ways to work with Ubuntu files from Windows?

I know I can edit files directly on Ubuntu by SSH, but basically I like using Notepad++.

---

### Post by Rebelli0us on 2012-06-22
In nautilus you select any dir or partition, right click, Properties, Share, create share. Then any machine on your network can access but they have to login.

---

### Post by anon0 on 2012-06-23
I don't have access to GUI at the moment but I'm using Samba to set up the share to require authorization. 

I did: net usershare add sharename [path] "comment" everyone:F guest_ok=n

If I enable guest_ok then I can access it. However, I wish to require user credentials, so I used guest_ok=n, but then it won't let me access it using my username and password. 

After the net usershare command, it says usershare_acl=S-1-1-0:F in /var/lib/samba/usershares/sharename. 

I did set up a password for Samba: smbpasswd -a username
I also restarted Samba: sudo smbd reload

Any ideas?

Update: Nautilus didn't work either.

---

