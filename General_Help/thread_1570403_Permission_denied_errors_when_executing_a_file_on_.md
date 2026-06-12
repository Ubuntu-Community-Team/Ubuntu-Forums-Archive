---
title: "Permission denied errors when executing a file on a different hard drive"
date: 2010-09-08
forum: General Help
---

### Post by tyfius on 2010-09-08
I installed Ubuntu 10.10 beta yesterday and most of it is working very well. However, I ran into a problem with permissions today.

I have a HDD containing my home folder and a HDD containing my data folder. The HDD with the data folder is mounted on /media/data/data_1.

```
jensen@jensen-desktop:~$ ll /media/data/ | grep data_1
drwxrwxrwx  8 jensen jensen 4.0K 2010-09-07 23:10 data_1/
```

Inside that data_1 folder I have a folder called Downloads which I mounted to the Downloads folder in my home directory. This is done in the same way I did it on 10.04 and 9.10.

From /etc/fstab:
```
/media/data/data_1/Downloads /home/jensen/Downloads none user,bind 0 0
```

When I tried to install VMWare this morning I got a permission denied error:```
jensen@jensen-desktop:~/Downloads/internet$ ./VMware-Workstation-Full-7.1.1-282343.x86_64.bundle 
bash: ./VMware-Workstation-Full-7.1.1-282343.x86_64.bundle: Permission denied

```

I made sure I had set a+x rights on the file, tried executing it as root but the permission error stayed. When I copy that same file to my Desktop folder I can perfectly execute it. When it's located on the other hard drive I can't. I tried several command line scripts and they all work when I execute them from my OS hard drive, but not from another hard drive. How can I fix that?

I must be overlooking something, but I can't figure out what so any pointers are greatly appreciated.

---

### Post by coffeecat on 2010-09-08
Instead of mounting your /media/data/data_1/Downloads  folder to /home/jensen/Downloads in fstab, have you tried making /home/jensen/Downloads a link to /media/data/data_1/Downloads?

---

### Post by tyfius on 2010-09-08
No, I did not think of that. But it works though. Thanks.

---

