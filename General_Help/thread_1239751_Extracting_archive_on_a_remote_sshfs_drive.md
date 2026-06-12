---
title: "Extracting archive on a remote sshfs drive"
date: 2009-08-13
forum: General Help
---

### Post by vaerer on 2009-08-13
When you run a command against a sshfs mounted drive it's the command on your computer that is run against the data on the remote drive ?

So you can do this, even if vim isn't installed on the remote server:

```
vim /mnt/sshfs/server/root/.bashrc
```
Would that mean that uploading and extracting an archive is a waste of time?

Take this example:

```
mv big-file.tar.gz /mnt/sshfs/server/root
cd /mnt/sshfs/server/root
tar xvzf big-file.tar.gz
```
Also, what happens if you scp a file from the mounted drive to another server?

 ```
scp /mnt/sshfs/server/root/big-file.tar.gz root@123.123.123.123:/root
```

---

### Post by Penguin Guy on 2009-08-26
> **vaerer said:**
> When you run a command against a sshfs mounted drive it's the command on your computer that is run against the data on the remote drive ?
Yes. If you mount a remote partition with sshfs then it will act pretty much the same as any other partition on your computer. And yes, I believe you can transfer files between two remote servers using the [COLOR="Green"]scp[/COLOR] method above.

---

