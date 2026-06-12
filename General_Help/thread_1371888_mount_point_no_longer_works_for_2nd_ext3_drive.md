---
title: "mount point no longer works for 2nd ext3 drive"
date: 2010-01-03
forum: General Help
---

### Post by tamccullough on 2010-01-03
64-bit ubuntu
I added this to my fstab according to instructions;
/dev/sdb1    /media/driveNAME   ext3    defaults     0        2

It was working before today. Now it no longer mounts. 

I did update this evening and I am not sure if it worked before that, since I wasn't really using the machine. Just had it running.

Help me please!?

Thanks

---

### Post by tamccullough on 2010-01-03
More info;

error message

Error mounting: mount exited with exit code 1: helper failed 
with:
mount: only root can mount /dev/sdb1 on /media/driveNAME

---

### Post by dcstar on 2010-01-03
> **tamccullough said:**
> 64-bit ubuntu
I added this to my fstab according to instructions;
/dev/sdb1    /media/driveNAME   ext3    defaults     0        2

It was working before today. Now it no longer mounts. 

I did update this evening and I am not sure if it worked before that, since I wasn't really using the machine. Just had it running.

Help me please!?

Thanks

UUIDs are more reliable than /dev/ identifiers, do a search for detailed instructions on how to use them in the fstab file or just install the **pysdm** package and use that to set up the mount.

---

### Post by tamccullough on 2010-01-03
Thanks dcstar,
I just discovered that there looks to be new(to me) info on fstab in the community info
I change the fstab to use UUID and copied the info from the info page into it like this -

UUID=id /   ext3    defaults,errors=remounts-ro,noatime     0        1

seems to be working now

---

