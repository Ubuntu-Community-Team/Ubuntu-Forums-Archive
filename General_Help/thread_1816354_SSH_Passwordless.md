---
title: "SSH Passwordless"
date: 2011-08-01
forum: General Help
---

### Post by Groover20 on 2011-08-01
Hello,

I'm in need of some help...  I have 2 laptops currently connected to a multimedia server.  On my main laptop, I followed this [HOW-TO]("http://ubuntuforums.org/showthread.php?t=430312") to seti it up, so it mounts automatically.  It works wonderfully.

Now, on my second laptop, even if I'm following the same steps, it doesn't work.  I have to type the password everytime.  I even went as to copy the FSTAB entry from the working computer over to the other laptop, and it doesn,t work either.

Here's the FSTAB:
sshfs#server@192.168.1.102:/media/multimedia /media/Multimedia fuse fsname=sshfs#server@192.168.1.102:/media/multimedia,port=2222,comment=sshfs,noauto,users,exec,uid=1000,gid=1000,allow_other,reconnect,transform_symlinks,BatchMode=yes 0 0


I'm running 11.04 on both.

Thanks in advance for you help,

Groover

---

### Post by Groover20 on 2011-08-03
I read severals HOW-To for the passwordless login, but nothing works.  Is there a known bug or anything that I might be missing?

---

