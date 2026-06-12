---
title: "Urgent Partition error"
date: 2011-04-07
forum: General Help
---

### Post by Habeouscorpus on 2011-04-07
I was trying to move my home partition on Ubuntu, and the computer hibernated on me. I restarted it up on the live disk to survey the damage, to find that the home partition, according to fsck, "Superblock has an invalid journal (inode 8) Clear? <y>"

It cannot be mounted, either.

What do I do?

---

### Post by Habeouscorpus on 2011-04-07
Okay, I quit fsck, and did it again, resolving to suck it up and do it since no one responded. 

I got an all clean message. I mounted home successfully. Now I have a lost+found folder and all my stuff is in there. What now?

---

### Post by aktiwers on 2011-04-07
Just move the stuff back where you want it.

This lost+found is a folder created with files that was lost during the error, and now found again.

If you dont have rights to it, just:
```
sudo chown username:username -R /path/to/lost+found 
```
Where "username" is your ubuntu username.

Then:
```
sudo chmod 777 -R /path/to/lost+found
```

You should now own them and have permission to do what you want with them.

---

### Post by Habeouscorpus on 2011-04-07
I'm seeing a lot of the files I deleted previously. 

What are socket files and pipe files? Can I recover them?

---

