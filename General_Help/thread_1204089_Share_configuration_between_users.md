---
title: "Share configuration between users"
date: 2009-07-04
forum: General Help
---

### Post by glo on 2009-07-04
Hi there.

I would like to share some applications' configuration files (usually located at home folder) between multiple users.

For example,
[LIST]
[*]I have VirtualBox installed.
I only want to set it up once so all users will be able to use the same virtual machine;
[*]Though I also want every user to have his own Firefox profile.
[/LIST]
How do I go about doing this?
Thanks

---

### Post by blueridgedog on 2009-07-04
I can think of two ways.  One, move the virtual box to a location that everyone can access.  For example, you could set it up in /home/virtualbox.  Give everyone permission to the directory, chmod 777 /home/virtualbox.

The second would be to setup the items you want in your profile/home directory and then copy them to each user's home directory.  You could update this each time you log off with rsync.  

Just guessing...

---

### Post by Himsagar on 2009-07-04
First permit everyone to have access to all the folders in virtualbox.
Have separate login features to everyone to share common resources.
Ask everybody to have a firefox profile entered for them.

---

### Post by glo on 2009-07-04
Thanks for the ideas,

What I finally did was to create a SharedConfigs folder where shared configs are saved.
Then I created links such as .VirtualBox inside everyone's home folder that point to the SharedConfigs folder.

This seems to work.

---

