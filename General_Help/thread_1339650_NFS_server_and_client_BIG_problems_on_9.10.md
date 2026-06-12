---
title: "NFS server and client BIG problems on 9.10"
date: 2009-11-27
forum: General Help
---

### Post by mothes on 2009-11-27
Hello, I had a little problems with installation of NFS server. But I've fixed it. I hope this short manual will help you don't have some problems with NFS. 

**Server and client side.**
First off all you most install all packages.
```
# aptitude search nfs-server nfs-kernel-server nfs-common nfs-client
```

**Server side.**
You need to create directory that you'll share: 
```
user@server:$ mkdir share
```

After you must edit file with NFS preferens /etc/exports
```
user@server$ sudo nano /etc/exports
/home/user/share/ 192.168.1.102(rw,sync,no_subtree_check)
```

*Please don't forget to check rights on your directory. (I forgot to do it and that's why I had a problems)*

where: 
**/home/user/share/ **- directory that you'll share:
**192.168.1.102** - IP address of machine that will get access to the server. 
**(rw,sync,no_subtree_check)** - parametrs of sharing
**rw** - rights (read\write)
**ro** - rights (only read)

For example you can give access to all computers in a network: 
```
/home/user/share/ *(rw,sync,no_subtree_check)
```

where: 
***** - all computers

or you can give access for few computers with different rights for them: 
```
/home/user/share/ 192.168.1.101(rw,sync) 192.168.1.102(ro,sync)
```


This is it. Restart your server: 
```
user@server$ sudo /etc/init.d/nfs-kernel-server restart
```

**Client side.**
First you must create a folder where to mount remote directories from server: 
```
user@client$ mkdir /home/user/data/
```

Do mounting: 
```
user@client$ sudo mount.nfs 192.168.1.100:/home/booch/share /home/mothes/data/ -rw
```

where: 
**192.168.1.100** - server IP address
**/home/user/share** - share folder on server
**/home/user/data/** - mounting point on client 
**-rw **- to mount system with rights read\write

Also you can make small *bash script* to do it automaticaly: 
```
$ sudo nano connect.sh
user@client$ sudo mount.nfs 192.168.1.100:/home/booch/share /home/mothes/data/ -rw
```

After just write in console: 
```
sh connect.sh
```

Remount all the systems: 
```
sudo mount -a 
sudo umount -a
```

**This is it!**
[[img] http://www.linuxspace.org/wp-content/uploads/2009/11/linuxspace.jpg [/img]](http://linuxspace.org)
[[IMG]http://brainstorm.ubuntu.com/idea/21593/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/21593/)

---

### Post by Dinodoc on 2009-11-28
On the server side, what are the permissions on that directory, I have had this happen to me where I share something with rw and mount with rw, but forget to set permissions to allow write for other users.

On server, go to home folder, right click on Shara - Properties/Permissions tab - Folder = Others Create and Delete and Files = Read and Write, then apply settings to enclosed files.

Not sure both Folders and Files is needed but I do it.

You could also use chmod on the command line

chmod -R 666 Shara 

Would set the folder to Read and Write for User, Group and Other

Hope I explained this at least moderately coherently :)

---

### Post by mothes on 2009-11-28
Thanks this is a problem! It was wrong rights on my Shara directory on the server.

---

### Post by Dinodoc on 2009-11-28
Yeah been there way too many times to want to admit to it :)

I seem to always forget that.

---

### Post by mothes on 2009-11-28
Yeah! Really thank you so much, also me usally forget about this small but important detail. Now it is ok and I modify the question in how to, I hope it will help some people.

---

