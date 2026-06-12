---
title: "Automount no longer working"
date: 2009-12-07
forum: General Help
---

### Post by prem1er on 2009-12-07
I edited my fstab file a few weeks ago to include two drives on the network that I want mounted at start up. The auto mount worked for about a week and no longer mounts the drives at start up. I can manually mount the drives without a problem. One is mounted through Samba and the other through NFS. I have checked in /var/log/messages for errors, but I'm not exactly sure what I'm looking for. Is this the right log file? If so, what should I be looking for?

---

### Post by prem1er on 2009-12-08
bump.

---

### Post by fuzzai on 2009-12-08
Im not advanced in linux by any means, however i was following a tutorial to create a raid, and it mounted fine in ubuntu 9.04, at 9.10 it did not mount, and this was a solution.

"To fix it change the /etc/fstab file entry
From: /dev/md0 /var/media auto defaults 0 3
To: /dev/md0 /var/media ext3 defaults 0 0"

Changed the file system from auto detect (i assume thats what it means) to stating its ext3.

Could this be what is giving you your issues?

---

### Post by prem1er on 2009-12-16
bump.

---

### Post by whiteychs on 2009-12-16
Are you sure your fstab is correct?

If all else fails, you could just create a startup bash script to mount when you login.

---

### Post by prem1er on 2009-12-16
Thanks. I'm almost positive that the fstab file is correct as it worked for about a week or two. I will post it when I am at my computer.

---

### Post by prem1er on 2009-12-16
Ok, here is the contents of my /etc/fstab. It doesn't work with the IP address or the hostname map. The IP is mapped to the hostname in /etc/hosts.

```
192.168.1.101:/opt/sybhttpd/localhost.drives/HARD_DISK /home/xxx/drives/randy  nfs  rw,hard,intr    0       0
```

and

```
randy:/opt/sybhttpd/localhost.drives/HARD_DISK /home/xxx/drives/randy  nfs  rw,hard,intr    0 
```

Both don't work when mounting automagically in /etc/fstab. When I mount the drive manually I don't have a problem with.

```
sudo mount randy:/opt/sybhttpd/localhost.drives/HARD_DISK /home/xxx/drives/randy/

```

Where is the log for the automount?

---

### Post by VitaLiNux on 2009-12-16
You might try [http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14](http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14)

---

### Post by prem1er on 2009-12-16
Thanks for the reply, but I don't think you read exactly what I posted. I'm mounting over NFS to a ext3 drive. There is no NTFS involved at all.

---

### Post by prem1er on 2009-12-17
bump.

---

### Post by prem1er on 2009-12-18
bump.

---

