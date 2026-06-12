---
title: "Symbolic Links."
date: 2011-09-19
forum: General Help
---

### Post by creata.physics on 2011-09-19
So I recently got a fresh install of ubuntu going on, and I've tried to make sure everything was going as soon as possible.

Anyway, everything was perfect until I installed xampp. 

For some strange reason, I decided to link my Public folder to my htdocs folder using:
```
sudo ln -s ~/Public /opt/lampp/htdocs/$USER
```

Well now my issue is that I cannot remove Public folder in terminal using rm /home/matthew/Public, but I also cannot setup a symbolic link to my actual public_html folder.

Any thoughts on how I can resolve this issue?

---

### Post by creata.physics on 2011-09-19
bump, still experiencing difficulties resolving this issue.

---

### Post by SeijiSensei on 2011-09-19
Are you trying to delete the link as root?  Since you created the link with sudo, it's going to be owned by root, not by you.  Try "sudo rm Public".

---

### Post by creata.physics on 2011-09-19
Yes I have, this is what I get:
```

matthew@matthew-Dimension-3000:~$ sudo rm /home/matthew/Public
[sudo] password for matthew: 
rm: cannot remove `/home/matthew/Public': Is a directory

```

---

### Post by SeijiSensei on 2011-09-19
> **creata.physics said:**
> Yes I have, this is what I get:
```

matthew@matthew-Dimension-3000:~$ sudo rm /home/matthew/Public
[sudo] password for matthew: 
rm: cannot remove `/home/matthew/Public': Is a directory

```

You need to use "rm -rf /home/matthew/Public" to remove a directory.

From reading your post again, it sounds like Public was already a directory, not a symbolic link.  In fact, I don't think you understand the notion of links correctly.  You don't "link" a directory to another directory.  Think of a symlink as an alias.

So, for instance, you could make /home/matthew/Public be another name for /opt/lamp/htdocs/matthew by using:

```

cd /home/matthew
ln -s /opt/lamp/htdocs/matthew Public

```

Now /home/matthew/Public is another way of referring to /opt/lamp/htdocs/matthew.  Is that what you were trying to accomplish?

You don't need root to make this link either unless you have no permissions to /opt/lamp/htdocs/matthew.  (Of course, in that situation creating the link would be useless since you wouldn't be able to use it without becoming root first.) Ordinary users can create symlinks if they have read/list privileges on the source and write privileges into the target.

---

### Post by creata.physics on 2011-09-20
> **SeijiSensei said:**
> You need to use "rm -rf /home/matthew/Public" to remove a directory.

From reading your post again, it sounds like Public was already a directory, not a symbolic link.  In fact, I don't think you understand the notion of links correctly.  You don't "link" a directory to another directory.  Think of a symlink as an alias.

So, for instance, you could make /home/matthew/Public be another name for /opt/lamp/htdocs/matthew by using:

```

cd /home/matthew
ln -s /opt/lamp/htdocs/matthew Public

```

Now /home/matthew/Public is another way of referring to /opt/lamp/htdocs/matthew.  Is that what you were trying to accomplish?

You don't need root to make this link either unless you have no permissions to /opt/lamp/htdocs/matthew.  (Of course, in that situation creating the link would be useless since you wouldn't be able to use it without becoming root first.) Ordinary users can create symlinks if they have read/list privileges on the source and write privileges into the target.

Public and public_html were already directories.

You may not be reading my post correctly. I stated that I'm trying to make the folder Public be another name for /opt/lampp/htdocs.

With the code you provided, is the same thing I've already done.

When you gave me that code, and said, "Now /home/matthew/Public is another way of referring to /opt/lamp/htdocs/matthew.  Is that what you were trying to accomplish?" 

That was already accomplished, as stated in the first post.

My issue is that, when I go to [http://localhost/matthew](http://localhost/matthew), it will show me everything that is in the Public directory.

Well, I want to remove the reference from Public to my htdocs folder, and make my htdocs folder reference to /home/matthew/public_html instead.

**Edit: I have fixed the issue.  What I did was go to my /opt/lampp/htdocs folder and remove the file matthew, I then created a new symbolic link between my public_html and htdocs folder, so now everything shows up the way it's needed.**

A moderator can switch this threads prefix to solved if they'd like.

---

