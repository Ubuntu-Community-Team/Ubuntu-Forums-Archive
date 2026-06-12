---
title: "Transmission Web UI"
date: 2009-09-09
forum: General Help
---

### Post by prem1er on 2009-09-09
I just installed Transmission on my headless ubuntu server with 

```
sudo apt-get install transmission
```

This installed transmission as well as the web cli.  I have it up and running by visiting [www.xxx.com:9091](www.xxx.com:9091).  This is working fine.  I found located the configuration file and changed the directory that transmission downloads to.  I am getting a permission error.  I'm assuming transmission doesn't have the correct permissions to write to this directory.  When I checked 

```
ls -lrt
```

on the default download directory the owner is set to transmission-daemon. The directory I wish to download to is under my users ownership.  What is the safest way to allow access for 'tranmission-daemon' to write to a directory under my user home folder?  Thanks.

---

### Post by credobyte on 2009-09-09
```
drwxr-xr-x 2 dainis dainis    4096 2009-09-09 15:43 Transmission

```

Haven't had any problems with downloading/uploading via Transmission. Indeed, default directory is Desktop, so .. there's no way it could be owned by Transmission daemon.

---

### Post by prem1er on 2009-09-09
My default directory is not Desktop though. I'm not at my computer right now, but it is somewhere in /var. I would like it to be in my home directory.

---

### Post by credobyte on 2009-09-09
```
sudo chown -R transmission-daemon:group /var/somewhere

```

Replace group with your main users group ( your username ). Not sure if it'll bet but .. it's better than nothing - give it a try :)

---

### Post by prem1er on 2009-09-09
> **credobyte said:**
> ```
sudo chown -R transmission-daemon:group /var/somewhere

```

Replace group with your main users group ( your username ). Not sure if it'll bet but .. it's better than nothing - give it a try :)

Thanks credobyte. I was actually trying to change the ownership of the directory I wanted to download into instead of the default.  So for anyone looking at this post simply add the transmission-daemon user as an owner of the directory where you want to download.

```
sudo chown transmission-daemon /path/to/downloads
```

---

