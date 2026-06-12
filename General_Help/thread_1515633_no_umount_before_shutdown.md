---
title: "no umount before shutdown"
date: 2010-06-22
forum: General Help
---

### Post by vascot on 2010-06-22
Hi,
i did recently upgrade to lucid on my dual boot system with windows xp. After upgrading the ifs windows driver cannot mount my ext3 partitions anymore, because they are not clean. Shutting down ubuntu using the shutdown button in gnome doesn't work. How can I get ubuntu umounting my disks before shutting down?

---

### Post by Yarui on 2010-06-22
If all else fails you could just write a short script that unmounts all your drives and run that before you shut down.

---

### Post by ajgreeny on 2010-06-22
Did you upgrade and keep ext3 or did you move to ext4?   I don't think there are any windows drivers yet that work properly for ext4, so wonder if that is your problem.

---

### Post by vascot on 2010-06-23
It is still ext3. When you unmount it manual before shutting down windows can mount the partition.

@Yarui: How can you make a script execute on shutdown?

---

### Post by Yarui on 2010-06-23
Well, you probably can have a script execute at shutdown, but I just meant to manually run the script.  Just leave it on your desktop or in your launcher panel.  It's not a perfect solution, but it's better than typing the commands every time you want to shut down.

There may be a way to edit the function of the shutdown button itself to execute your own script.  Just have the script umount all your mounted drives then run "shutdown -hP now", or something to that effect.  You can change values and functions of a lot of menus if you can find the configuration files, so it may be doable.

---

### Post by khairat on 2010-10-25
why is it important to unmount before shutting down?

---

### Post by vascot on 2011-02-06
> **khairat said:**
> why is it important to unmount before shutting down?

When you want to mount a filesystem in windows using ifsext2 driver, the filesystem should be clean.

---

