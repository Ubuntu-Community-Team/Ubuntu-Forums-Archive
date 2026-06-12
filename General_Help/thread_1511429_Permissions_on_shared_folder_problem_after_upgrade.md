---
title: "Permissions on shared folder problem after upgrade to 10.04"
date: 2010-06-16
forum: General Help
---

### Post by blur xc on 2010-06-16
I had a shared music folder set up on my system in 9.04.  I have the sticky bit set and all the music files and folders belong to group shared. Both user acounts are added to the shared group according to the /etc/groups file and in system- administration- users & groups.  But the output of groups from the command line does not show that either user belongs to the shared group. That being said both users are denied permission when trying to modify files owned by the other user.  All hte files have read and write pesmissions set for both user and group.

Thanks
BM

---

### Post by cariboo on 2010-06-17
> **blur xc said:**
> I had a shared music folder set up on my system in 9.04.  I have the sticky bit set and all the music files and folders belong to group shared. Both user acounts are added to the shared group according to the /etc/groups file and in system- administration- users & groups.  But the output of groups from the command line does not show that either user belongs to the shared group. That being said both users are denied permission when trying to modify files owned by the other user.  All hte files have read and write pesmissions set for both user and group.

Thanks
BM

Try adding the users to the share group with the following command:

```
sudo gpasswd -a <user> shared
```

---

### Post by blur xc on 2010-06-17
> **cariboo907 said:**
> Try adding the users to the share group with the following command:

```
sudo gpasswd -a <user> shared
```


that's wicked awesome!  thanks- worked like a charm.  I'll read up the man pages on the gpasswd command.

thanks again-  I get a massive headache when messing with something that should work one way that isn't doing what I expect and can't figure out...

BM

---

