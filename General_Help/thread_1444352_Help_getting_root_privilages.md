---
title: "Help getting root privilages"
date: 2010-04-01
forum: General Help
---

### Post by Steve Danahey on 2010-04-01
I know its frowned upon but I need root privileges to enable sharing with my main folder which is called /Media and is for all storage (950gigs) but since I have no root privileges I can not save or move anything into this directory. Could someone possibly give me some help? Thanks.

---

### Post by k33bz on 2010-04-01
if you going to work in the directory VIA command line just type this in ```
su root
```I am imagining you have already set a password for root.

If you want to work in the directory VIA GUI, then do this
Go to your terminal and type in```
gksudo nautilus
```
after you type that in along with your password the window will pop open that is enabled as root

---

### Post by nothingspecial on 2010-04-01
Rather than working as root you may be better owning the drive.

```
sudo chown -R username:username /Media
```

Do not put a space inbetween / and Media or you will really mess stuff up.

put your username where it says username.

Then if you want to share the stuff on the drive

```
sudo chmod -R 755 /Media
```

Again don`t put a space.

That means that other users and applications can use the stuff on there but can`t delete it by accident.

---

### Post by new_tolinux on 2010-04-01
> **nothingspecial said:**
> Then if you want to share the stuff on the drive

```
sudo chmod -R 755 /Media
```Again don`t put a space.

That means that other users and applications can use the stuff on there but can`t delete it by accident.

If you want other users to change anything on the drive, you can type 777 instead of 755.

---

### Post by Steve Danahey on 2010-04-01
Worked like a charm nothingspecial! Also thanks for the tip on the 777 deal it was useful. Now to rip 523 cd's!!!:popcorn:

---

