---
title: "How to 'reown' a faulty drive"
date: 2011-11-13
forum: General Help
---

### Post by futurefjp on 2011-11-13
Hi, 

I currently have a partition on my HD that I can't access at due to the permissions being greyed out: I can't take ownership: it was from a previous install that went wrong.

Is there a way of resetting, realigning the read write settings on this HD without losing all my stuff in the files that I don't have permission to/

TIA

Daniel

---

### Post by satanselbow on 2011-11-13
find the mount point by either having a look in gparted or 

```
sudo blkid
```


Your partition will be listed as "/dev/sdXY" where "X" is a letter and "Y" is a number.

Then take ownership of the partition with:

```
sudo chown -R <user>:<user> /dev/sdXY
```

where "<user>" is your current username ;)

---

### Post by futurefjp on 2011-11-13
> **satanselbow said:**
> find the mount point by either having a look in gparted or 
 
```
sudo blkid
```
 
 
your partition will be listed as "/dev/sdxy" where "x" is a letter and "y" is a number.
 
Then take ownership of the partition with:
 
```
sudo chown -r <user>:<user> /dev/sdxy
```
 
where "<user>" is your current username ;)
 
 
thanx duder!

---

### Post by futurefjp on 2011-11-13
> **satanselbow said:**
> find the mount point by either having a look in gparted or 

```
sudo blkid
```
Your partition will be listed as "/dev/sdXY" where "X" is a letter and "Y" is a number.

Then take ownership of the partition with:

```
sudo chown -R <user>:<user> /dev/sdXY
```where "<user>" is your current username ;)


had a chance now but i can't reown root or lost/found and the home user folder either:

have any further suggestions?

---

