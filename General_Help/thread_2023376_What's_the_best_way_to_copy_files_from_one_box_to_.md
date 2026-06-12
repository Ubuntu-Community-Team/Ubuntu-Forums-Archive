---
title: "What's the best way to copy files from one box to another over the wire"
date: 2012-07-12
forum: General Help
---

### Post by AlexBooton on 2012-07-12
Hi,

Using Nautilus I was able to connect to a server via ssh.

Once doing that I can use Nautilus to explore and copy files.  All using the GUI.

But what if I want to use cp to copy files?  Is the SSH file system automatically mounted?  Where?  Or can I mount it?  How?  Or can cp be use to refer to the external system?  How?

Is there a better way to copy files from one box to another?

I actually tried to do the copy (newer files only) using the GUI and it didn't copy all newer files!  There are some 520,000 files.  Could that "overwhelm" the GUI?  Something seems wrong and I grasping at straws.

This is U 12.04

Thanks,

AB

---

### Post by AlexBooton on 2012-07-12
I was just watching the file copy operation (using the GUI).  It runs through about 20,000 files (out of 520,000) and just dies (exits) with no error message.

Could it be a corrupted file that's killing the copy?

If I could use cp maybe I could find the problem.

---

### Post by Vaphell on 2012-07-12
use scp

---

### Post by Morbius1 on 2012-07-12
If you are connecting to the server using "Connect to Server" it is mounting at the following location:

> /home/your-user-name/.gvfs/SFTP for user-name on 192.168.0.100

---

### Post by AlexBooton on 2012-07-12
> **Morbius1 said:**
> If you are connecting to the server using "Connect to Server" it is mounting at the following location:

Found it right where you said!  

Thanks,


AB

---

### Post by LewisTM on 2012-07-12
I'd say use rsync. It will copy over SSH and has the advantage of sending only the parts of a file that have changed, greatly speeding transfers. It's very robust.

Something like:

```
rsync -v files user@server:/path
```
-v is for verbose output. Use -av to copy all file attributes as well.

Cheers!

---

