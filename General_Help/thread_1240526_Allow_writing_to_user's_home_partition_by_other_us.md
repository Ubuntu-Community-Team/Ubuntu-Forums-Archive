---
title: "Allow writing to user's home partition by other users"
date: 2009-08-14
forum: General Help
---

### Post by narnie on 2009-08-14
I hate to admit I don't know how best to do this as I've been a linux user for over 10 yrs off and on (very many remember Caldera?)

I want to be able to collaborate on files with select other users. I thought using my home directory and allowing read/write privalages to members of a group I created would be a good way to do this, but after making the directory read/write accessable to that group, I started getting the ".dmrc message and to not let other users write to your home directory" error message every time I login via GDM.

How is the best way to do this?

Also, what started me experimenting with this was making a separate wine directory for a program, and allowing write access to members of a "wine" group for that directory and all files contained to see if that is a way I could install a program once but allow other users to use the installation. It didn't work (why not?) and that is the first ever time I got the .dmrc message on login.

I would rather keep said files in the home directory (which I have on a separate partition for backup purposes and easier disto upgrades/changes) rather than using a location in a directory other than home.

Then I starting thinking about collaborating on files and how best to do that as well. Recommendations?

Thanks,
Narnie

---

### Post by jocampo on 2009-08-14
Allowing other users write on your own home directory and viceversa is not a good admin practice. But what you can do is, create a directory and grant users to a Group or Users to that particular directory. For instance ... let's say you have 3 peers who are working on a Project, this is what I suggest

Create folder

```
sudo mkdir /project
```

Create Group

```
sudo addgroup project-users
```

Once done, you can assign any existing user to that particular group and then, change the ownership of /project directory to that particular group, so anyone inside that group can write and read inside /project

---

### Post by narnie on 2009-08-14
I had thot of this, but not having it on the home directory means that I have to keep track of every shared folder I created when I backup or try a new distro. My home directory is on a separate partition that is "safe" during installs. What about creating the "project" dir in home. Is that poor practice, too? Also, what does a user who doesn't have root access do when they want to share write privileges with other users? Do they thus require admin's assistance?

With thanks,
Narnie

---

### Post by bodhi.zazen on 2009-08-15
> **narnie said:**
> I had thot of this, but not having it on the home directory means that I have to keep track of every shared folder I created when I backup or try a new distro. My home directory is on a separate partition that is "safe" during installs. What about creating the "project" dir in home. Is that poor practice, too? Also, what does a user who doesn't have root access do when they want to share write privileges with other users? Do they thus require admin's assistance?

With thanks,
Narnie

If you own the file you can assign permissions to it, otherwise you need root access.

Assuming you own the file you can assign permissions to the group or others.

[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

if you have many users and you need finer grain control then you use acl (access control lists).

Share directory : [http://hep.pa.msu.edu/user/groups.html](http://hep.pa.msu.edu/user/groups.html) 
    Set Group ID : chmod g+s dirname 
 
    OR (ACL works better) 
 
    ACL : [http://ubuntuforums.org/showthread.php?t=145741](http://ubuntuforums.org/showthread.php?t=145741) 
      or [http://ubuntuforums.org/showpost.php?p=1193555&postcount=13](http://ubuntuforums.org/showpost.php?p=1193555&postcount=13)

---

### Post by Mardoct909 on 2009-08-15
I'm pretty sure that running "chmod 777 -R /home/username" as root would do it. As stated, though, bad admin practice.

---

### Post by bodhi.zazen on 2009-08-16
> **Mardoct909 said:**
> I'm pretty sure that running "chmod 777 -R /home/username" as root would do it. As stated, though, bad admin practice.

Please do not run that command , it will cause much trouble. Many files in $HOME need more specific permissions.

ACL are actually quite easy and there is even a gui tool available to manage them if you need.

---

