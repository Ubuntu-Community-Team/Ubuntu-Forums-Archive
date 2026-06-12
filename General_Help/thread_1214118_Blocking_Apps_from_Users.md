---
title: "Blocking Apps from Users"
date: 2009-07-15
forum: General Help
---

### Post by tdexor on 2009-07-15
I am making an Edubuntu LTSP server and I have gotten to the point were I want to lock out some users from certain programs (Italc and some system admin programs). Is there any way to block programs from users? Also can you duplicate the settings of programs such as Main Menu?

---

### Post by mike555 on 2009-07-15
you might try "lock Down Editor " ..........

---

### Post by jerome1232 on 2009-07-15
> **tdexor said:**
> I am making an Edubuntu LTSP server and I have gotten to the point were I want to lock out some users from certain programs (Italc and some system admin programs). Is there any way to block programs from users? Also can you duplicate the settings of programs such as Main Menu?

As for the system admin programs if they are not in the 'admin' group they can't use any program which would normally require a password to use. If you wanted to grant access to specific administrative tasks you could do this via the sudoers file.

here is a small guide about the sudoers file made by the Ubuntu community.
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

For normal programs you would have to adjust permissions for each individual program, but nothing is preventing a user from installing a local copy of the program into their home directory and running it from there.

---

### Post by tdexor on 2009-07-15
Thank you very much for the quick responses. But the Pessulus Lockdown editor isn't quite enough. And I'll check out more about the sudoers guide after this. Is there any way to copy settings from one user to another?

---

### Post by tdexor on 2009-07-15
I've done some searching and found some answers so I'm going to close the forum thank both of you very much for your help.

---

### Post by t4thfavor on 2009-07-15
Please post the "answers" here for the benefit of others.

---

### Post by tdexor on 2009-07-17
Well for stopping users from access in programs I have just been only giving rights to owner and groups for the file using sudo chmod 770 <file name>. Then when they go to access the program nothing happens. That's the best I have found so far and I still haven't found much on copying user settings. It seems like quite a few people are looking at that (even on these forums). And the thread is getting off topic which is why I was going to close it...... but how do you close a thread?

---

### Post by CatKiller on 2009-07-17
> **tdexor said:**
> how do you close a thread?

Only admins can close a thread. You could edit the title of the first post or add a tag to say [solved] so that people searching for an answer to a similar problem will know that this thread is one to look at.

The main thing to look at for generic user settings is /etc/skel. This is the template from which new Home folders are made, so you can change startup settings (by providing application configurations) by placing appropriate files in this folder. There are a couple of other places that I can't remember at the moment for default startup entries and the like.

---

### Post by tdexor on 2009-07-21
I've tried to look at the /etc/skel (and info about it) but it's missing the files that everything is referencing? Because it is suppose to be the base structure for new users correct? So they will all start the same way with the same settings correct? So any idea why it is missing those files?

---

### Post by CatKiller on 2009-07-21
> **tdexor said:**
> I've tried to look at the /etc/skel (and info about it) but it's missing the files that everything is referencing? Because it is suppose to be the base structure for new users correct? So they will all start the same way with the same settings correct? So any idea why it is missing those files?

For applications that use a configuration file in the Home directory, if that configuration file does not exist it is created from the program defaults when that program is run. But if you want a program to have certain defaults for a user you can create the appropriate configuration file first and put it in their Home directory. And if you want that file to be created in each new user's Home folder when that user is created, you put it in /etc/skel.

That's the principle.

Also, the other thing that I mentioned before, but couldn't remember the location; the default startup applications are stored as .desktop files in /etc/xdg/autostart.

---

### Post by tdexor on 2009-07-29
Sorry about the delayed response but that makes sense I'll check it out when I have free time. Thanks

---

