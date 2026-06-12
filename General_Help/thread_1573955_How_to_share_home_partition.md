---
title: "How to share /home partition?"
date: 2010-09-13
forum: General Help
---

### Post by andres-bracho on 2010-09-13
Hi,

I just want to know if I can share my /home partition... I mean, I have 3 partitions swap, / with Ubuntu NBR and /home and want to install another distro (in a 4 partition), double boot and share /home.

If my /home partition is encrypted by Ubuntu, can I share it with another distro?

What I want to "also" use is Ubuntu Moblin Remix or meego.

---

### Post by jerome1232 on 2010-09-13
Generally it's a bad idea to share your users ~/ with other distro's since per user application settings are stored in there (including gnome/kde preferences and such) and those settings can cause conflicts.

It would be better to have a separate data partition. I add symlinks inside my home that point to respective places in my data partition.

```
ie /home/jeremy/Videos -> /mnt/data/Videos
   /home/jeremy/Documents -> /mnt/data/Documents
```


and etc...

---

### Post by ajgreeny on 2010-09-13
> **jerome1232 said:**
> Generally it's a bad idea to share your users ~/ with other distro's since per user application settings are stored in there (including gnome/kde preferences and such) and those settings can cause conflicts.

It would be better to have a separate data partition. I add symlinks inside my home that point to respective places in my data partition.

```
ie /home/jeremy/Videos -> /mnt/data/Videos
   /home/jeremy/Documents -> /mnt/data/Documents
```and etc...
+1
Sharing your /home partition using the same username and password is asking for trouble; some distros have different UUIDs for users, some store the configurations of programs in different folders, and I think it will/may cause all sorts of problems for you.

Have a separate /home for one distro and then mount that home partition at boot of the second distro, and link the data files of the first and second distros to avoid replication of all your files.  All you will need is a line in the /etc/fstab of the second distro to mount first distro's home at boot, and everything will be seamless.  

If you still want a separate /home for the second distro, it will not need to be very large at all, as it will contain only the configuration folders/files, not any data files.

---

### Post by srs5694 on 2010-09-13
I disagree with the previous two posters, at least up to a point. First, though, it's important that you understand the distinction between the /home directory and individual users' home directories. The latter reside inside the former. That is, if your username is andres, your home directory is likely to be /home/andres, which is a subdirectory inside /home. If you've got /home on its own partition, then /home/andres is just a directory on that partition. If this is at all confusing, remember that Linux is a multi-user system. You could have /home/andres, /home/fred, /home/judie, and dozens of other user home directories all in /home and on one system. Many Ubuntu systems have just one user, but the capability is there for much more.

There's absolutely nothing wrong with sharing a /home partition between different distributions. Sharing users' home directories, though, can cause problems because configuration files for specific programs may point to different icons, require different formats (because of different software versions on the different distributions), or be otherwise incompatible. Another issue is that user ID (UID) numbers may differ between distributions, which can make files that are owned by the same person appear to be owned by different users. Thus, if you want to share the /home partition, you should ensure that each user has different home directories in each distribution. The easiest way to do this is to use a different username in each distribution; however, it's possible to use a single username and alter the home directory that's used in one of the distributions. The UID issue (which is shared with jerome1232's solution) can be overcome by using the text-mode usermod and chown commands or by GUI tools that accomplish the same task.

Creating a separate /mnt/data partition (or whatever), as jerome1232 suggests, will work; but it adds a layer of complexity with its symbolic links and provides no benefit over creating separate user home directories in a /home partition. What's more, if done *exactly* as jerome1232 suggests, it doesn't adapt well if/when you want to add more user accounts (for family members, roommates, employees, your own experimentation, or whatever). To be adaptable for that, you'll have to manually create and manage subdirectories for each user in /mnt/data; essentially, you'll be manually doing what the standard Ubuntu account-creation tools are designed to do automatically, therefore creating more work for yourself than if you used a shared /home partition.

---

### Post by dcstar on 2010-09-14
> **srs5694 said:**
> I disagree with the previous two posters, at least up to a point. First, though, it's important that you understand the distinction between the /home directory and individual users' home directories.
........

Agree with most - **but** sharing the same /home user folder even between different releases of the same Distro will cause problems.

If I dual boot and use my normal 10.04 /home account with my old 9.04 system it will stuff up quite a few Gnome and app settings that I have to fix when I next boot 10.04 (because of the different versions used).

Yes, you **can** share /home but it is a bad idea to share /home user folders - set up different user accounts for each distro/version you want to boot.

The best way I have found to use different distros etc is to install (the free) VMware Player and set up as many VMs as I need.

---

### Post by andres-bracho on 2010-09-14
Ok, I understand... thank you very much for your answers.

Then I'm going to install the second distro with / and /home in one partition.

Thank you very much.

---

### Post by srs5694 on 2010-09-14
> **dcstar said:**
> Agree with most - **but** sharing the same /home user folder even between different releases of the same Distro will cause problems.

I said that, except that I was attempting to keep things clear by using the leading-slash directory indicator ("/home") only in reference to specific directories. Hence I referred to "the /home directory" as the entire directory, including all individual users' home directories; and when referring to users' home directories, I did *not* include the leading slash, except when referring to that specific directory ("/home/fred" or whatever).

The terminology about this can be very confusing to new users because of the subtle but important distinctions between things like "/home directory" and "user home directory" -- and of course there are many other variant terms.

---

