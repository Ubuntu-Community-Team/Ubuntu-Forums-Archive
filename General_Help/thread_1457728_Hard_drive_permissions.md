---
title: "Hard drive permissions"
date: 2010-04-19
forum: General Help
---

### Post by Velvet Karuda Leopard on 2010-04-19
Ok.  I have two (2) hard drives on my computer.  One for the OS and one for storage purposes.

I need to have the storage drive accessible by both the user accounts on this machine.

Right now only root can do anything with the drive period.

How can I make it so any user can use this drive?

Thanks much for any help.

---

### Post by Roasted on 2010-04-19
Depends what you want to do. There's a few options here.

You could set permissions to 777 to the drive, which gives full access to ANYBODY. The three 7's each represent a different thing.

1st - Owner
2nd - Group
3rd - Others

7 = Full Access

So 777 means Owner/Group/Others can have full access. To do this you issue:

sudo chmod -R 777 /path/of/drive

If you want a little more security, you can just add the user1 as owner and user2 as group. Say your two users are Fred and Bob. You can run:

sudo chown -R fred:bob /path/of/drive

Then change the permissions to:

sudo chown -R 770 /path/of/drive

This gives the owner/group full blown access, and nothing to others. Or you could change 770 to 775 so owner/group has full access and others can at least read.

It's really up to you, but the examples above should at least give you some idea on what road to take.

---

### Post by arrimapirate on 2010-04-19
sudo gedit /etc/fstab in terminal (will let you edit the fstab file where mount options are set)
Find the drive you want readable by everybody, follow that line of text and where it says "defaults" change it to "auto,user,rw" without quotes. 
auto - will mount it at boot
user - makes it mountable by any user
rw - mounts it in read/write mode

---

### Post by romeroc24 on 2010-04-19
Well man, I think your second drive (storage) is mounted on /media/sda2 and you can set privileges for all user like this.

```

$sudo chmod -R /media/sda2

```

Tha access for all users will be open for write, read, etc.

---

### Post by romeroc24 on 2010-04-19
Sorry 

```

$sudo chmod -R 777 /media/sda2

```

---

