---
title: "Most GUI tools failing because of permission problems"
date: 2011-10-11
forum: General Help
---

### Post by kesten on 2011-10-11
This is slightly off topic, but i cant find a "new post" button anythere, only "new reply"

It is on the topic of permissions:
 
A lot of gui tools are failing because of permissions.
For example, if i try to download or extract a .gzip to /opt i get an  error that i don't have permission to extract to it (no write access).  I read that the gui's are supposed  to pop up a password dialog box for permission issues, but this doesn't happen for me.  For now, i'm  going to the terminal, using sudo and chmoding things and then apt-getting from the  command line, but it's a lot of extra work.  

Know of any way to fix the GUIs so i can have sudo like power?
I am the sole user and its an asus 2010 laptop with ubuntu 11.04

kesten

---

### Post by lisati on 2011-10-11
> **kesten said:**
> This is slightly off topic, but i cant find a "new post" button anythere, only "new reply"

I've moved your post to its own thread. In future, go to [http://ubuntuforums.org](http://ubuntuforums.org), click on a category, and then on the "new thread" button.

---

### Post by bab1 on 2011-10-11
> **kesten said:**
> This is slightly off topic, but i cant find a "new post" button anythere, only "new reply"

It is on the topic of permissions:
 
A lot of gui tools are failing because of permissions.
For example, if i try to download or extract a .gzip to /opt i get an  error that i don't have permission to extract to it (no write access).  I read that the gui's are supposed  to pop up a password dialog box for permission issues, but this doesn't happen for me.  For now, i'm  going to the terminal, using sudo and chmoding things and then apt-getting from the  command line, but it's a lot of extra work.  

Know of any way to fix the GUIs so i can have sudo like power?
I am the sole user and its an asus 2010 laptop with ubuntu 11.04

kesten

The tools are run with your UID.  They do not have built in sudo rights.  You as a user have those rights and you either need to use sudo for text based apps or gksudo for GUI apps.  You can also safely modify the /opt directory permissions.  My /opt directory has root:admin user:group ownership and permissions of 775.

With just those 2 changes I (as an admin) can use the /opt directory while limiting regular users to read only use.

---

