---
title: "How do I share files between users on one computer?"
date: 2009-10-02
forum: General Help
---

### Post by Gosport on 2009-10-02
I have a huge photo library.  My wife and I use the same computer but log in as different users.  I don't want to create duplicate photo libraries.  How and where do I create a folder where we both have equal access (write/delete) to the files?  I would rather not have this folder in either one of our Home folders.  What is the normal convention?

---

### Post by StuartN on 2009-10-02
> **Gosport said:**
> What is the normal convention?

/share is used for shared material, such as sound files, documentation and program data, but I would imagine that photographs are really a user property.

I would put photos in each user's ~/photographs and create a symlink to the other users' ~/photographs folders, then set the appropriate permissions - so everybody has a photographs folder and within it will be all their own photographs and virtual subfolders to every other users' photographs.

An alternative is to create a brand new photographs user and store all photographs in this user's home, so everyone looks to /home/photographs/<username>/ for their own photographs.

The reason I would do it this way (rather than using /share) is that the /home partition can be backed up or migrated to a new operating system very easily, without having to disentangle it from system material.

---

### Post by Discus on 2009-10-02
You can create a new user group, and add both you and your wife to it. 

You can then change the group (chgrp command) of the folder/directory you want to share and then give the appropriate permissions (chmod) to the new shared group.  

If this sounds like greek to you, I suspect this page: 
[http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups](http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups)
will be helpful.

---

