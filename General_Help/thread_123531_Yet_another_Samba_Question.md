---
title: "Yet another Samba Question"
date: 2006-01-30
forum: General Help
---

### Post by chaser001 on 2006-01-30
Ok here's my situation...I have samba running my shared drive is mapped to an empty 250gb HD...I can log into the samba box named FILESERVER from my XP box.  When I do I can see 3 folders the big HD (Shared) my home folder (tchase) and one named Printers and Faxes.  I can open each of these folders however when I try to access a subfolder or move a file into these folders I get an error message that says "You do not have permissions. Contact the system administrator."  

To set up the sever I used ubuntu's gui for file sharing then ran the sudo smbpasswd -a 'user' and sudo smbpasswd -e 'user' 

What didn't I do?

Thanks

---

### Post by rmjokers on 2006-01-30
You have to make sure that this 'user' has permissions to read/write in the directory that is being shared.  By default, it is probably owned by root.  The easiest thing to do would be change the owner:

sudo chown -R 'user' 'shared folder'
sudo chgrp -R 'user' 'shared folder'

---

### Post by chaser001 on 2006-02-01
i don't think that would help in my situation...i'm trying to give 3 users access to it.

---

### Post by sect2k on 2006-02-01
I don't exactly recall the solution, but reading the SAMBA HOW-TO and relevant documentation on [www.samba.org](www.samba.org) will help you understand how SMB works and how to set it up.

But if my memory still serves me well, you have to set up a file and directory mask for the shared files. Like i said, read the docs at samba.org.

the man page for smb.conf might be give you some more insight also.

Cheers,
/me

---

### Post by chaser001 on 2006-02-03
um yeah i read through the before and I still don't get it...hence the fact that I asked for someone to help me figure out what I missed...and RTM post doesn't help any.

---

### Post by wrtrdood on 2006-02-03
Do all of the directories (on the server) have 755 permissions?  Execute is required for access.

---

### Post by soulestream on 2006-02-03
If its on a homenetwork, then chmod -R 777 /mnt/foldername

that will give all users rwx

if you want only those 3 users, then put them in a group like "myusers", then chgrp those folders recursively to give those users permissions.

soule

---

### Post by chaser001 on 2006-02-06
Thanks Soul that did it. Everythings working great now!!!

---

