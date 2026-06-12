---
title: "make a swap file"
date: 2011-10-11
forum: General Help
---

### Post by jemadux on 2011-10-11
dont have many swap ?? just make a swap file 
The trick is to make a file and then tell the swapon program to use it. Here's how to create, for example, a 64
megs swap file on your root partition (of course make sure you have at least 64 megs free):
```
dd if=/dev/zero of=/swapfile bs=1024 count=65536
```
This will make a 64 megs (about 67 millions bytes) file on your hard drive. You now need to initialize it:
```
mkswap /swapfile 65536
```
```
sync
```
And you can then add it to your swap pool:
```
swapon /swapfile
```
With that you have 64 megs of swap added. Don't forget to add the swapon command to your startup files so
the command will be repeated at each reboot.

---

