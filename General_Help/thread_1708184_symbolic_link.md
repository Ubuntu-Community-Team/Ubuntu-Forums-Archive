---
title: "symbolic link"
date: 2011-03-16
forum: General Help
---

### Post by Drenriza on 2011-03-16
I know how to make symbolic links on the same or between two different partitions. But is it possible to make symbolic links between two different servers, that are on the same lan?

Thanks on advance.
kind regards.

---

### Post by r.osmanov on 2011-03-16
What if you mount network location some where like 
```
$ sudo mount //192.168.1.10/shared_folder /media/shared10
```?

---

### Post by mssever on 2011-03-16
You have to have a filesystem path available. The most obvious way is to mount the remote filesystem somewhere, then symlink to it.

---

### Post by Drenriza on 2011-03-16
server A has location
/home/user/folder1

I would like to sym-link to folder1 from

Server B
/home/user/folder2

Cant i do that somehow?

---

### Post by r.osmanov on 2011-03-16
> **Drenriza said:**
> server A has location
/home/user/folder1

I would like to sym-link to folder1 from

Server B
/home/user/folder2

Cant i do that somehow?

Install **apache2** Web server and create a virtual host on source machine. For instance, it could be /etc/apache2/sites-available/lanshare:
```

ServerName server.lanshare

<VirtualHost 127.0.0.5:80>
DocumentRoot /var/www/lanshare
ServerName lanshare
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.php5 
</VirtualHost>

```Then make a link /var/www/lanshare pointing to /home/user/folder

---

### Post by r.osmanov on 2011-03-16
Then you need smth like 
```

$ sudo mount //192.168.1.10/lanshare /media/lanshare10

```
of course

---

### Post by mssever on 2011-03-17
I don't see how installing Apache helps the situation at all. The point is, you can only make a symlink to a file/directory on the local machine. If you want to symlink to a remote machine, you must first mount an appropriate directory on the local machine. Common ways to mount remote directories include NFS and Samba.

The solution r.osmanov gave won't work in the general sense. Perhaps it will work with Samba, but I haven't used Samba recently enough to remember the details. And installing Apache is a useless step that won't do anything to move you closer to your goal.

Actually, creating symlinks might be unnecessary, after all. Since you already have to mount the remote directory, why not just mount it where you want it? Remember that you can specify any directory as a mount point. You don't have to put it in /mnt or /media if another location makes more sense.

---

### Post by r.osmanov on 2011-03-17
> **mssever said:**
> I don't see how installing Apache helps the situation at all.
If he wants just  a file listing, he don't need apache2 or any other web server at all, indeed. However, a web server allows manipulate requests flexibly, ex. using RewriteRule.. Isn't it?

---

### Post by r.osmanov on 2011-03-17
You should have find it useful to add an entry like 
192.168.0.10 lanhost10
to your /etc/hosts

---

### Post by SeijiSensei on 2011-03-17
Step-by-step

1)  You need to export the directory on Server B so it can be mounted on Server A.  The easiest method to accomplish this is [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo").

2)  You'd then mount server B's exported directory to a "mount point" in server A's filesystem tree.  Then you could make a symlink.

You will need to learn how to run a file sharing server on one of these machines.  NFS is best for *nix-only configurations.  If you need to mount files on Windows machines, you'd need to look into [Samba]("https://help.ubuntu.com/community/Samba").

---

### Post by mssever on 2011-03-18
> **r.osmanov said:**
> If he wants just  a file listing, he don't need apache2 or any other web server at all, indeed. However, a web server allows manipulate requests flexibly, ex. using RewriteRule.. Isn't it?
The whole point of symlinks isn't merely a file listing. It's to access files at another location. A webserver is completely unrelated. Using Apache's mod_rewrite is useless in the OP's situation. He isn't trying to make a flexible website; he's trying to create a symlink to a remote host so that he can access remote files as if they were local. Apache and/or mod_rewrite can't possibly help in such a situation.

> **r.osmanov said:**
> You should have find it useful to add an entry like 
192.168.0.10 lanhost10
to your /etc/hosts

Again, this is unrelated. It may well be useful to set up a hosts file. But it isn't necessary for the problem at hand. And, depending on the situation, it might not be useful. Or, it might be useful.

---

### Post by r.osmanov on 2011-03-18
> **mssever said:**
> The whole point of symlinks isn't merely a file listing. It's to access files at another location. A webserver is completely unrelated. Using Apache's mod_rewrite is useless in the OP's situation. He isn't trying to make a flexible website; he's trying to create a symlink to a remote host so that he can access remote files as if they were local. Apache and/or mod_rewrite can't possibly help in such a situation.

Again, this is unrelated. It may well be useful to set up a hosts file. But it isn't necessary for the problem at hand. And, depending on the situation, it might not be useful. Or, it might be useful.

Okay, he should have probably got that all he should do is to mount "remote" location as
```
$ sudo mount //192.168.1.10/shared_folder /media/shared10
```Then he may, or may not apply further tricks with Apache, nginx or something else... I'd apply a Web server, for instance. However, here is an obvious solution, despite criticism it deserves... ;)

We're human beings, not computers. And it is normal to mention things that indirectly regard to the main topic.

---

