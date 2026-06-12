---
title: "File permission"
date: 2009-09-13
forum: General Help
---

### Post by Strega on 2009-09-13
Hello,

I'm trying to make a file wich will execute some other files.
But my problem is that even my root has a permission denied warning when executing the file.
I just did
```
touch restart_servers
nano restart_servers
```
After that I just entered the lines to execute other files and it gave me the "Permission denied" warning.
Any idea why?

Regards, Strega

---

### Post by sisco311 on 2009-09-13
make it executable:
```
chmod +x restart_servers
./restart_servers
```

---

### Post by Strega on 2009-09-14
Omg, that I missed that xD
Thank you very much :D

Regards, Strega

---

### Post by sisco311 on 2009-09-14
You're welcome!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

