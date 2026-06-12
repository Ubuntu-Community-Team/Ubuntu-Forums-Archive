---
title: "HDD permissions."
date: 2009-08-05
forum: General Help
---

### Post by Biopyro on 2009-08-05
I am having [a problem installing ubuntu]("http://ubuntuforums.org/showthread.php?t=1231539"), and someone suggested that I change something in grub/menu.lst, but apparently I don't have permissions to save changes. 

I've looked around and found these commands:

ubuntu@ubuntu:~$ sudo chmod u+w /media/disk
ubuntu@ubuntu:~$ sudo chown root /media/disk

but neither have worked (or shown errors).

How do I make it so that I can alter this file?

---

### Post by nothingspecial on 2009-08-05
> **Biopyro said:**
> I am having [a problem installing ubuntu]("http://ubuntuforums.org/showthread.php?t=1231539"), and someone suggested that I change something in grub/menu.lst, but apparently I don't have permissions to save changes. 

I've looked around and found these commands:

ubuntu@ubuntu:~$ sudo chmod u+w /media/disk
ubuntu@ubuntu:~$ sudo chown root /media/disk

but neither have worked (or shown errors).

How do I make it so that I can alter this file?

Well you shouldn`t really have run those but never mind. They are not what you need.

I take it you are trying to edit your installed /boot/grub/menu.lst from a live cd.

First you need to mount your ubuntu to the live disk.
```

sudo mkdir /ubuntu
```

```
sudo mount -t ext3 /dev/sda1 /ubuntu
```

```
sudo nano /ubuntu/boot/grub/menu.lst
```

Make your alterations then press Ctrl+O to save, Return to confirm and Ctrl+X to exit.

Please don`t make multiple threads for the same issue.
Iwill put a duplicate reply in your original thread.

---

