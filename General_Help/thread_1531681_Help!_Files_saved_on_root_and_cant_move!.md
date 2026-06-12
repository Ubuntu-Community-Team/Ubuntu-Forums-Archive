---
title: "Help! Files saved on /root and cant move!"
date: 2010-07-15
forum: General Help
---

### Post by cizin on 2010-07-15
Hi! if some one can help me!  I downloades some files with jdownloader, i choose a a folder on my windows partition, but the files where saved on /root/Desktop/V .  i'm trying to cut them into other folder, but it fails. Now my free space on ubuntu is 0!!!!  Help??

---

### Post by RiceMonster on 2010-07-15
In the future, make sure you do not run jdownloader as root.


you can either open nautilus as root
```
gksudo nautilus
```
and copy them over, then change the owner to you.


Or, you can do is from the command line
```
cd ~/Desktop
sudo mv /root/Desktop/V ./
chown -R YOUR_USER_NAME V/*
```

With that, they'll be on your desktop in a folder called V

if you just want to delete them, do this:
```
sudo rm -r /root/Desktop/V
```

---

