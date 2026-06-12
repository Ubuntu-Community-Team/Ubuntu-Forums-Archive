---
title: "Mount subfolders in samba?"
date: 2010-07-08
forum: General Help
---

### Post by lazychris2000 on 2010-07-08
Here is my problem, which I have been playing around with on and off for the past couple days.  I have an ubuntu file server (10.04 server edition x64, if it matters) and I am trying to mount a subfolder on my ubuntu desktop (10.04 Desktop x86).
I have a share on the server called 'data', which has a few dozen subfolders.  I am trying to mount //server/data/Tools to my downloads folder on my desktop, but I can't seem to make it work.
I added this to my fstab:
```

//192.168.177.243/data/Tools /home/chris/Downloads cifs auto,username=******,password=******,uid=1000,umask=000,users 0 0

```
but when I try to mount it, I get 
```

mount: //192.168.177.243/data/Tools is not a valid block device

```
When I mount //192.168.177.243/data, it works fine, but anytime I try to mount a subfolder, I get that error.  I am trying to avoid making a share for each individual share, but I can't find a solution, I might just have to do that.
Any help would be appreciated!

Edit: I guess I could just mount the data folder to like /media/server then symlink the folders to where I want them, but that also seems rather inconvenient.

---

### Post by Atroban on 2012-05-31
Same problem with a shared folder like:

```
mount -t cifs //172.16.1.4/SRV_Backup&/Dir /media/nas_max1/ -o username=USER,password=PASS,domain=DOMAIN,iocharset=utf8,file_mode=0777,dir_mode=0777

```
Doesn't work!

if I put:
```
mount -t cifs //172.16.1.4/SRV_Backup& etc...
```

everything will work! :confused:

---

### Post by Atroban on 2012-05-31
Find a stupid (but working) solution [here]("http://www.craigmayhew.com/blog/2010/12/mounting-a-windows-share-on-linux/")

you have to install Samba FS!
```
sudo apt-get install smbfs
```

---

### Post by lazychris2000 on 2012-05-31
Holy thread resurrection, Batman!

It's been so long, I forgot how I eventually solved the problem, but I'm pretty sure that was how I did it.  I've since upgraded the server to 12.04 and switched from samba to nfs, but thanks for the reply.  Hopefully it will help someone who is searching for the same solution :D

---

