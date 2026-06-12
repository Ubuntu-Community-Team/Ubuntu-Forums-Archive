---
title: "2 computers, one /home"
date: 2010-02-24
forum: General Help
---

### Post by gfuggs on 2010-02-24
I just got a second computer, and would like to use the same /home for both of them, be able to use them interchangeably, etc. 

I set up a nfs server, and while I still have a few questions about some of the options in /etc/exports, I am able to mount /home from the old computer on the new computer in /etc/fstab.  

My main question is about GID/UIDs, and how to handle users.  Is there a way to have a single set of users/groups instead of a separate set on each machine?  Right now, I have a user account set up on the new computer with the same name/UID as the old computer. 

How is this sort of thing usually done?

---

### Post by snkiz on 2010-02-24
> **gfuggs said:**
> I just got a second computer, and would like to use the same /home for both of them, be able to use them interchangeably, etc.

I've been thinking you could do that with Ubuntu's cloud implementation, set up a local cloud. That way you could sync home folders across many machines and still be mobile. But I haven't had a chance to look into it yet.
 
> **gfuggs said:**
> 
My main question is about GID/UIDs, and how to handle users.  Is there a way to have a single set of users/groups instead of a separate set on each machine?  Right now, I have a user account set up on the new computer with the same name/UID as the old computer. 

How is this sort of thing usually done?
Thats how I do it seems to work well

---

### Post by gfuggs on 2010-02-24
I should probably add that this is just a basic home setup, both computers connected to a router.

---

### Post by snkiz on 2010-02-24
well then you don't need the complexity of cloud stuff. Just make /home shared with samba or nfs on one machine. Then mount the share as /home on the other machine with fstab.

I can help you do that if you need.

---

### Post by dabl on 2010-02-24
> **gfuggs said:**
> I just got a second computer, and would like to use the same /home for both of them

That's a bad idea, to try it literally.  What you want is for each system to have its own /home directory, and then you need either a directory within one of the /home directories, or even better a separate partition on one of the hard drives, and in that one you want a folder named "OURDATA" or something, and keep your shared data in there.  Then you can symlink the OURDATA folder into every /home/user/ directory in the house.

The /home directory is a defined part of the Linux filesystem, owned by root and unique for each system -- you'll bugger things quickly if you try making it a shared user directory.

---

### Post by snkiz on 2010-02-24
I'm not sure about that. The home folder is just an empty dir until you put user dir's in it. it can still be own by root

Edit:
If it worries you you can mount /home/<your username> through fstab as well. I'm guessing you want to share your home config files for the same user on both machines, in witch case a shared data directory wont help.

---

### Post by gfuggs on 2010-02-24
I appreciate the responses, but did you guys actually read my post, or only the title of the thread?

---

### Post by cjhabs on 2010-02-24
Check out this link:
[https://help.ubuntu.com/community/OpenLDAPServer](https://help.ubuntu.com/community/OpenLDAPServer)

---

### Post by SecretCode on 2010-02-24
What makes you think the above posters didn't read your post? The answers are spot on.

How will you use these two computers? Same applications installed? Same person using both? Same browser bookmarks, same email, etc?

---

### Post by snkiz on 2010-02-24
LDAP looks like a much better way to go.

---

### Post by sgosnell on 2010-02-24
I think you would be better off using separate /home partitions, and syncing them via rsync and cron.  That way you have less risk, and can sync just the data you need shared.

---

### Post by rnerwein on 2010-02-24
hi
i think that is want do want to have: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

whit automount/nis/nfs you are able to set up hundreds of computers. it's quite good if you start with your small cofiguration. but don't try to handle permissions/usr/group by hand. i promise you  -> this don't  work.
ciao

---

### Post by bodhi.zazen on 2010-02-24
I would also echo sharing /home is not the best of ideas. It will work, but keep in mind, /home contains a bunch of config files and as such there can be conflicts if there are different versions of software on different boxes.

I suggest using NFS or Samba (samba is more secure, but slower) for a shared data partition.

With that said, the links you have been given already are all very good.

I would add:

[http://www.brennan.id.au/19-Network_File_System.html](http://www.brennan.id.au/19-Network_File_System.html)

[http://www.vanemery.com/Linux/NFS-Van.html](http://www.vanemery.com/Linux/NFS-Van.html)

---

### Post by gfuggs on 2010-02-24
Thank you cjhabs and rnerwein.  LDAP/NIS is exactly what I need.  Now that I know what it's called I should be able to google my way to getting it set up.  Perfect.

---

