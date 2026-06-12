---
title: "mounting sshfs with fstab, usercredentials"
date: 2009-10-06
forum: General Help
---

### Post by artheus on 2009-10-06
Hi!

I've got a little problem.. I'm reading this thread

[http://ubuntuforums.org/showthread.php?t=270806](http://ubuntuforums.org/showthread.php?t=270806)

And I'm wondering, what can I do to make this mount with my user credentials for the ssh-server?

I mean, so that the ssh mounts, and gives the password automagically?

Cheers

---

### Post by artheus on 2009-10-06
and one more thing... How can I get the permissions of the ssh user I mount with, in the mount-point? Now I get

```

The folder contents could not be displayed.

You do not have the permissions necessary
to view th econtents of "remote".

```

---

### Post by KeyserSoze93 on 2009-10-06
Well, the best way to do that is with a public/private key authentication set up.

The barebones would be:

Client:
```
sudo apt-get install sshfs
sudo mkdir /media/server
ssh-keygen -t rsa
scp ~/.ssh/id_rsa.pub server:/home/user

```

Server:
```
cat ~/id_rsa.pub >>.ssh/authorized_keys
```

Then add a line like this to your fstab:
```
sshfs#user@server:/home/user    /media/server   fuse    user,noauto,transform_symlinks 0 0
```

That way, you can simply type "mount /media/server" as you (no sudo), and it will mount without either the client or the server asking for your password.

Please note though, SSH pubkey authentication seems to be a bit dodgy to set up on some systems (I expect to be contradicted here, but hey), and you should make sure you "apt-get update && apt-get upgrade" both systems to the same version of openssh client and server (i.e. if one is using openssh from backports, enable them temporarily on the other server too)

I assume this is because of the openssh security fix, circa 2008, which caused the key generation system to be changed, and seems to make older versions no longer generate valid keys.

Apart from that though, it pretty easy to set up.

---

### Post by artheus on 2009-10-07
It Works!
BUT! How can I get this to mount itself on startup? So that I don't have to use the

```
mount /media/server
```

everytime I need to get access to that folder, and have restarted my computer.

Does this work for multiple server-folders too?

Cheers and Thanks,
Artheus

---

### Post by artheus on 2009-10-07
I just tested for multiple folders.. And that Works like a charm! :)

But I still don't know how to make it mount automatically at start-up?

Cheers,
Artheus

---

### Post by zkeng on 2009-10-23
Try removing the "noauto" argument from the string in fstab. The noauto option in fstab prevents the mount point from being mounted automatically.

/Cheers

---

### Post by Stonedancer on 2010-09-28
Hi guys, 
How would you run these key generation commands if your server is not on the default port 22.  I was advised to switch it to something else plus I've picked a port that is open on the work firewall because ssh is shut off.

I can't find any way of specifying the alternative port for my remote address.

I must have read a hundred guides and forums for trying to do this. I've given up on fstab/credentials file so maybe these keys will work.

Cheers

---

### Post by narcisgarcia on 2010-10-07
A new guide to configure better the client and the server:
[http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses](http://wiki.lapipaplena.org/index.php/How_to_mount_SFTP_accesses)

(with special care with owners and permissions questions)

---

### Post by Stonedancer on 2011-03-14
Ah I've found the answer to my question.
the line

scp ~/.ssh/id_rsa.pub server:/home/user

needs to have the -P port switch then alternative port.

scp -P 443 ~/.ssh/id_rsa.pub server:/home/user

I still get a "/home/******/.ssh/id_rsa.pub: Permission denied" once I've connected with the correct password. 

Are their any idiot guides that explain how these keys work and where on your server you need to place your key?

Cheers.

---

