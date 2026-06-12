---
title: "I set up samba but read onl andi want to mount"
date: 2006-06-28
forum: General Help
---

### Post by CameronCalver on 2006-06-28
hey i set up samba on my ubuntu box but when i access it on my windows box i cant do anything it says access denied and also i want to mount the shared folder on the ububntu box in fstab

---

### Post by brownrl on 2006-06-28
Samba is always tricky. Its the fact that windows sometimes does encrypted passwords and I swear Bill builds in some SMB detection that makes things hairy... ;)

I understand your first part. For a small home/office network, samba work really well when you run it in:

security = share
guest account = your_user_name

mode... YES YES YES I KNOW ITS NOT SAFE. But do you have a router with a firewall? Also any decent ISP won't let you have port 139 open anyway. Are you running a wireless network with no WEP encryption?

Trust me though only with FreeBSD and Webmin do I get Samba running with passwords and home directories proper. With this Ubuntu those lines above in the smb.conf just makes everything work.

The second part of you thing is weird, you want to mount a locally server smb shared directory? Why not just access normally?

Rob

---

### Post by CameronCalver on 2006-06-29
ok i dont care about mounting all i want to do is be able to edit the files in the share on the windows box

---

### Post by CameronCalver on 2006-06-29
lol lol i feel like a n00b i did not set the shared folder permissions to allow from other but still that is not good enough becuase it is not safe saying that others can write read and execute and also if someone creates a  folder on one of the network computers it says on the server that the owner is nobody and the group is nobody and i cant delete the folder or files that i created on the windows machine so is it possible that even if i creat a folder on the windows computer i will still be able to delete it and modify it on the ubuntu box?

---

