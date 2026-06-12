---
title: "Basic Folder Permissions Manipulation"
date: 2010-02-22
forum: General Help
---

### Post by cpressland on 2010-02-22
Hi all,

I've setup a basic SFTP Server and four user accounts all with thier home directories residing in the /home folder

```

/home/user1
/home/user2
/home/user3
/home/user4

```

Now I've setup all the accounts with 'chmod 700' so that when somebody SFTPs into the server they can only access the files in thier specific folder and nobody elses.

Now I want to setup a fifth user 'Master' with access to all Read and Write access to all four folders.

Can somebody walk me through this?

Thanks

---

### Post by mcduck on 2010-02-22
Here's one way:

set the directory permissions to 760 instead of 700, giving the group read & write privileges. Then add your "master" user to "user1", "user2", "user3" and "user4" groups.
```

sudo useradd -G user1,user2,user3,user4 master
```

---

### Post by cpressland on 2010-02-22
Thanks dude,

You really saved my bacon there :)

I'd spent hours chowning stuff to no avail.

---

