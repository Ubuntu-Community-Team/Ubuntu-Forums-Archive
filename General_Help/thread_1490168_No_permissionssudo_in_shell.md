---
title: "No permissions/sudo in shell"
date: 2010-05-21
forum: General Help
---

### Post by aviceda on 2010-05-21
Just added a new 250g internal-drive in my karmic box, all seems OK and I formatted the partition with Gparted as ext4 but now can't create folders. Unfortunately I don't seem to be able to use a bash shell either, if I type anything in I get no problems until I attempt sudo and then I'm unable to type in a password! Any clues would be appreciated.

---

### Post by marshmallow1304 on 2010-05-21
The sudo password authentication does not give visual feedback as the password is being entered, but the password is accepted nonetheless.  You'll probably need to chown the new partition so you can write to it.

```
sudo chown -R <username> <mountpoint>
```

The mountpoint is probably /media/stringofcharacters unless you set it in fstab.

---

### Post by aviceda on 2010-05-21
Thanks Marshie, that works and I can create folders etc on that partition, however I've never noticed the password to remain invisible, until now.

Cheers,

Tom

---

