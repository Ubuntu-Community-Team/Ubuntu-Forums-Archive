---
title: "Mount UDF ISO"
date: 2010-09-25
forum: General Help
---

### Post by watupgroupie on 2010-09-25
I have backed up my Starcraft 2 installation disk because I was having problems mounting the Windows side of it. I backed it up inside windows and it's in UDF format. How do I mount it in Ubuntu? I mounted it perfectly fine with Daemon tools in Windows. I've tried using the default image mounter but it's completely useless besides just giving it an icon inside nautilus. I've also tried giso mount which is just as useless. Any ideas?

---

### Post by robsoles on 2010-09-25
take a look at [http://agnipulse.com/2008/08/easily-mount-iso-files-as-virtual-drives-in-ubuntu/](http://agnipulse.com/2008/08/easily-mount-iso-files-as-virtual-drives-in-ubuntu/)

---

### Post by watupgroupie on 2010-09-25
Tried it. The script doesn't do anything. Guess this is something I just took for granted in Windows.

---

### Post by robsoles on 2010-09-25
so, you placed the script and then you called it with the filename of your iso from terminal?

---

### Post by watupgroupie on 2010-09-25
No, you can right click the file, select mount script on the iso and it will supposevly mount but it doesn't work. 

I've figured it out though. The Starcraft 2 disk is weird and auto-mounts the Mac side of the disk whether it be the DVD or an ISO. Guess I never really had a problem with UDF. I couldn't get the mount command that mounted the windows side with the DVD. Eventually I got the idea to try it with the ISO and now it works. The command I used was ```
sudo mount -t udf -o loop,ro,unhide,uid=$(id -u) /path/to/iso /mount/point
```

If that made any sense XD

---

### Post by robsoles on 2010-09-25
sounds solved well enough for me.

please consider using 'thread tools' in red above to mark this thread as solved.

---

