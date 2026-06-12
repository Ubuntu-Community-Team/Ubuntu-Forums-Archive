---
title: "Automount not working in 9.10"
date: 2010-01-18
forum: General Help
---

### Post by prem1er on 2010-01-18
My automount is not working. When I boot up 2 external drives should be mounting (nfs, and samba). These drives do not mount. When I run sudo mount -a in the terminal both drives mount without a problem. Why won't they mount on startup? Here is my /etc/fstab file.

```

//xxx/music /home/xxx/drives/xxx smbfs username=xxx,password=xxx 0 0

xxx:/opt/sybhttpd/localhost.drives/HARD_DISK /home/xxx/drives/xxx  nfs  rw,hard,intr    0 0

```

---

### Post by prem1er on 2010-01-18
...Or even where in the logs I should be looking for the root of this problem?

---

### Post by john newbuntu on 2010-01-19
I am not sure either.  But as a workaround, edit your /etc/rc.local.  Put a sleep of say 10 seconds and then do a mount -a (mount <your-specific-filesystems>)

---

### Post by prem1er on 2010-01-19
Thanks. But I've never edited that file before. Mount requires root, how do I add this to the rc.local file? Actually, I'm having a hard time finding this information anywhere. Can someone link me to a good explanation of the rc.local file. TIA.

---

