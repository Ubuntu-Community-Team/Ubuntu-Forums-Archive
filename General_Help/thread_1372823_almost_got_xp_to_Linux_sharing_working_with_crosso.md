---
title: "almost got xp to Linux sharing working with crossover cable, need help"
date: 2010-01-05
forum: General Help
---

### Post by violetdream on 2010-01-05
I used some tutorials online, set up a user, manually set IPs (10.0.0.1 for win, 10.0.0.2 for ubuntu, gateway 255.255.255.0, crossover cable), and put this in my samba conf:

```
  security = user
   
    hosts allow =
 
 [homes]
 comment = Home Directories
 browseable = no
 writable = yes
 
 [share]
 comment = File Server
 path = /media/winback
 force user = bk
 force group = samba
 public = Yes
 read only = No
 guest ok = Yes
 browseable = Yes
 create mask = 0666
 directory mask = 0777

```

My user bk can log in and I can see the empty home directory and do stuff with it fine. I don't really care about that, what I care about is my /media/winback which is an ntfs formatted backup 1tb drive. When I navigate to that on windows, it tells me I don't have permissions. I'm worried that I didn't put user bk into the right groups or something but it would seem to me that everyone could write to that folder. What am I doing wrong?

---

### Post by dcstar on 2010-01-05
> **violetdream said:**
> 
.........
My user bk can log in and I can see the empty home directory and do stuff with it fine. I don't really care about that, what I care about is my /media/winback which is an ntfs formatted backup 1tb drive. When I navigate to that on windows, it tells me I don't have permissions. I'm worried that I didn't put user bk into the right groups or something but it would seem to me that everyone could write to that folder. What am I doing wrong?

Log on with bk and see if you access the drive.

---

### Post by zaphod777 on 2010-01-05
try adding in the security permissions of the folder you are sharing and adding the guest account as having access.

---

### Post by jamesisin on 2010-01-05
Can any other user access winback across the share and what kind of share are you using?

---

### Post by violetdream on 2010-01-05
that user can access the folder fine, and as you can see I have guest access allowed. I even tried changing the line to "security = share" which should allow everyone. Is it because it's a different file system?? I have no problem with any user on my linux machine. What do you mean what kind of share is it? I just configured both IPs manually and connected a crossover cable, installed samba with the parameters above.

---

### Post by violetdream on 2010-01-06
Ah, forgot to mention that xp gave a certain error when trying to access the folder:

"the group name could not be found"

I tried various fixes I found online like commenting out group or user, but that didn't help. Ideas?

---

### Post by jamesisin on 2010-01-06
So you are using a Samba share.

You will need to provide permissions in two areas.  First under Samba (which it sounds like you have already done) and second under Ubuntu.

You will want to give at least rw r r permissions in all likelihood.  If your user can view the share, that's good.  But without the r r permissions no one besides the owner on the Ubu box will be able to access files.

---

