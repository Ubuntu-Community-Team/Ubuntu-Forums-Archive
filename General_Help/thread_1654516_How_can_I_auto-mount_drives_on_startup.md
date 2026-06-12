---
title: "How can I auto-mount drives on startup?"
date: 2010-12-28
forum: General Help
---

### Post by GRIN2B on 2010-12-28
Hello all,

I've been trying to unsuccessfully auto-mount my drives when starting up. I've made a script that sets me to the root using "sudo -s" and then mounts the drives. The commands to mount the drives work properly when entered into the command line, but when I try running them from an executable, they don't work. What might I be missing?

I've looked at this thread:
[http://ubuntuforums.org/showthread.php?t=785263&highlight=auto+mount+startup](http://ubuntuforums.org/showthread.php?t=785263&highlight=auto+mount+startup)
However, both of the drives I want to mount are FAT. And, I suspect my difficulties are far simpler.

Thanks!

---

### Post by lungten on 2010-12-28
You can use the /etc/fstab to mount your drives at startup.

For example, append a line like this to your /etc/fstab
```
/dev/hda2 /media/data1 vfat defaults,user,exec,uid=1000,gid=1000,umask=000 0 0
```

Here's the [Ubuntu official documentation]("https://help.ubuntu.com/community/Fstab")

---

### Post by seawolf167 on 2010-12-28
You'll have to edit /etc/fstab to have drives mounted automatically upon startup

See the fstab link in my sig for more info

---

