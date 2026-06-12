---
title: "ecryptfs setup private dir"
date: 2009-12-17
forum: General Help
---

### Post by sgoranov on 2009-12-17
Hello,
I'm trying to setup private directory using ecryptfs. I have to mention that I'm using ubuntu from 7.04 so my home directory was created for first time when I installed 7.04 - which was long time ago :)
I'm using:

```
ecryptfs-setup-private -w
```

When I type the pass I've got the following error response:

```
Enter your wrapping passphrase: 
Enter your wrapping passphrase (again): 
Enter your mount passphrase [leave blank to generate one]:
Enter your mount passphrase (again):

************************************************************************
YOU SHOULD RECORD YOUR MOUNT PASSPHRASE AND STORE IT IN A SAFE LOCATION.
  ecryptfs-unwrap-passphrase ~/.ecryptfs/wrapped-passphrase
THIS WILL BE REQUIRED IF YOU NEED TO RECOVER YOUR DATA AT A LATER TIME.
************************************************************************


Done configuring.

Testing mount/write/umount/read...
Sessions still open, not unmounting
ERROR: Could

```

So after that I can't unmount the directory using:

```
ecryptfs-umount-private
```

I mean the command is executed without any errors but the directory is still mounted ! I can unmount it only with root account which is strange. I tried to setup Private directory for a brain new user on my system. So with the new user ecryptfs works fine. Maybe I've got something in my home dir and maybe that's the problem ? Any suggestions ?

Regards,
S.G.

---

