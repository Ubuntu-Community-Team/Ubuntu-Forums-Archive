---
title: "file permissions"
date: 2009-09-05
forum: General Help
---

### Post by koushiro on 2009-09-05
Hi all,

I'm trying to make a public folder that all my users can read/write to. For example, usera creates a file filea, I want to have userb open and modify filea. Right now I have a cron job chmod-ing everything in that folder to 766  every minute but it seems very dirty. How do I do this the proper way?

thanks

---

### Post by Liolikas on 2009-09-05
Other way I can think is configure local, public ftp and everyone lftp localhost or use gui ftp soft.

---

### Post by wojox on 2009-09-05
Try:

```
sudo chmod 0666 DirectoryName
```

All have r+w only.

Do this from the parent directory of the said directory.

---

### Post by The Cog on 2009-09-05
I would probably create a directory (for example called **pool**) and a group **poolusers** for people who use the pool. Then make all pool users members of the pool group.
> sudo mkdir /pool
sudo groupadd poolusers
sudo chgrp poolusers pool
sudo useradd -G poolusers user1
sudo useradd -G poolusers user2

If you also set the setgrp bit on the pool directory then any other directories created inside it will have the same behaviour.
> sudo chmod g+s /pool

---

### Post by amac777 on 2009-09-05
The way I solved this problem was similar to what The Cog suggested with the additional first step of changing the umask so new file's can be modified with by other members of the group:

1. Change the umask in /etc/profile so that new files created by users will have write access granted to the group that owns the file:

```
sudo nano /etc/profile
```

change the last line so it looks like this:

```
umask 002
```

2. Make a new group (for example called "family") and include the usernames of your family members (for example) you want to be able to share the files in your shared directory in that group.

System->Administration->Users and Groups->[Manage Groups]->[Add group]

3. Make the shared directory, set its group to be the name of the group you just created in step 2, give all users in the group full access to the directory, and tell it make all files created within that directory to the group of the directory:

```
sudo mkdir /sharedfolder
sudo chgrp family /sharedfolder
sudo chmod 775 /sharedfolder
sudo chmod g+s /sharedfolder
```

4. Logout and log back in to make the group changes take effect.

At this point, all users that you added to the family group should be able to create files in the shared folder, and also edit files created in the shared folder by other users in the family group.

Hope this helps.

---

### Post by koushiro on 2009-09-05
> **The Cog said:**
> I would probably create a directory (for example called **pool**) and a group **poolusers** for people who use the pool. Then make all pool users members of the pool group.


If you also set the setgrp bit on the pool directory then any other directories created inside it will have the same behaviour.

thanks for the suggestions. this seems the best fit to what i need. i'll go try this one out

---

### Post by bodhi.zazen on 2009-09-05
Some people feel ACL works best :

Share directory : [http://hep.pa.msu.edu/user/groups.html](http://hep.pa.msu.edu/user/groups.html)
    Set Group ID : chmod g+s dirname

    OR (ACL works better)

    ACL : [http://ubuntuforums.org/showthread.php?t=145741](http://ubuntuforums.org/showthread.php?t=145741)
      or [http://ubuntuforums.org/showpost.php?p=1193555&postcount=13](http://ubuntuforums.org/showpost.php?p=1193555&postcount=13)

---

