---
title: "Hello, im new and and struggeling with some problems"
date: 2011-02-14
forum: General Help
---

### Post by loydhisse on 2011-02-14
Hello,

I'm loyd and i've been using Ubuntu 10.10 for a couple of weeks now. I enjoy it a lot, however iv'e got a few things i cant figure out on my own.

1. 
i keep getting this warning message:
"(chromium-browser:2140): IBUS-WARNING **: The owner of /home/loyd/.config/ibus/bus is not loyd!"

I tried giving loyd the ownership with chown however when i chick it with "ls -l" the owner is still root. I don't really know if this is a serous warning or not.

2.
the second thing i'm struggling with is the sound on my laptop (EleteBook 8530W). When i click on the volume icon at the right top of the screen and choose sound preferences i get a popup : "Waiting for sound system to respond".

Here is some other information about this problem:

loyd@loyd-pc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
Home directory /home/loyd not ours.
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


I hope someone can help me with one of those problems.
Thanks in advance and i hope i can learn a lot around here.

Loyd

---

### Post by ankspo71 on 2011-02-14
Hi,
Does the chromium-broswer error effect Chromium in any way? If it doesn't then it probably isn't very important. To the best of my knowledge, everything in your home folder is supposed to be owned by you.

I don't have that particular file on my Kubuntu system. Can you check to see if that file is a symlink (a shortcut). The reason why I ask is because using chown (on my system) has no effect on symlinks when trying to change ownership of the symlinks. (Edited: See quote below)

To check if it is a symlink you can run the command:
ls -l /home/loyd/.config/ibus/bus

If it has "->" in the results, then the file is a symlink. 

-----

Oh, I just found this... I didn't know this either: (good tip for symlinks)
[http://manpages.ubuntu.com/manpages/jaunty/man7/symlink.7.html](http://manpages.ubuntu.com/manpages/jaunty/man7/symlink.7.html)
 > Symbolic link ownership, permissions, and timestamps
       The owner and group of an existing symbolic link can be  changed  using
       lchown(2).  The only time that the ownership of a symbolic link matters
       is when the link is being removed or renamed in a  directory  that  has
       the sticky bit set (see stat(2)).


Anyways, that quoted bit of info and link might help.:D

---

### Post by ankspo71 on 2011-02-14
Hi Again,
lchown is obsolete, so try chown -h instead (assuming the file is a symlink)

```
sudo chown -h loyd:loyd /home/loyd/.config/ibus/bus
```

That's the command to change ownership permissions of given symlink

---

### Post by loydhisse on 2011-02-14
Hi ankspo71,

thanks for your (fast) reply. I tried the things you said without any effect. The weird thing is that the location /home/loyd/.config/ibus/bus is a empty folder. I couldn't change the permissions, not even with ```
sudo chown -h loyd:loyd /home/loyd/.config/ibus/bus
```

The thing you said about ownership of your home folder triggered me to do 
```
loyd@loyd-pc:~$ ls -l
total 73
drwxrwxrwx 1 root root     0 2011-02-10 12:07 Desktop
drwxrwxrwx 1 root root  4096 2011-02-13 16:24 Documents
drwxrwxrwx 1 root root  4096 2011-02-14 17:44 Downloads
-rwxrwxrwx 1 root root   178 2011-02-12 14:33 examples.desktop
drwxrwxrwx 1 root root 65536 2011-02-10 17:58 Music
drwxrwxrwx 1 root root     0 2011-02-10 20:34 Pictures
drwxrwxrwx 1 root root     0 2011-02-10 12:07 Public
drwxrwxrwx 1 root root     0 2011-02-10 12:07 Templates
drwxrwxrwx 1 root root     0 2011-02-11 00:16 Videos
drwxrwxrwx 1 root root     0 2011-02-12 12:13 workspace

```

I don't own anything on my home folder!

Does anyone know how to fix this? I mounted an other partition (which is also used by windows) to /home, something might went wrong doing that. 

Chromium-browser is running fine (getting same error on firefox), i was just wondering how to get rid of the warnings, now i'm wondering why i don't own my home :(

help anyone?

thanks, loyd

---

### Post by matt_symes on 2011-02-14
Hi

> I mounted an other partition (which is also used by windows) to /home, something might went wrong doing that. 

Is it formatted as NTFS or fat ?

Post the output of 

```
cat /etc/fstab
``` 

Booth issues could well be connected to permissions.

Kind regards

---

### Post by loydhisse on 2011-02-14
it is ntfs...

```


loyd@loyd-pc:/home$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=8791045e-126a-4338-8e58-0cf73dde1fe6 /               ext3    errors=remount-ro 0       1
/dev/sda4	/home		ntfs	nodev,nosuid	0	2

```

---

### Post by matt_symes on 2011-02-14
Hi

```
UUID=8791045e-126a-4338-8e58-0cf73dde1fe6 /               ext3    errors=remount-ro 0       1
/dev/sda4	/home		ntfs	nodev,nosuid	0	2
```

Yes. You don't want to use NTFS formatting for you home folder. It can mess with the permissions. Use one of the native Linux formats. (extX or some such).

You can always mount another NTFS parition and have a symbolic link to it in your home partition or folder.

Kind regards

---

### Post by loydhisse on 2011-02-14
thanks!

if was a total mystery for me why i couldnt change the permissions.

So, what filesystem format would be the best for both ubuntu and windows7?

Would ext3 work on windows7?

loyd

---

### Post by matt_symes on 2011-02-14
Hi

> Would ext3 work on windows7?

Not unless you use third party software. This is one of a number. Just Google a search

[http://ubuntuextreme.blogspot.com/2009/01/how-to-mount-ext3-filesystem-in-windows.html](http://ubuntuextreme.blogspot.com/2009/01/how-to-mount-ext3-filesystem-in-windows.html)

Personally, i have an NTFS partition that is used for sharing files between windows and Linux but is not my home directory. I mount it at startup thought under /mnt/share and i have a symbolic link to it in my home directory so it's easy to get to.

You also might want to have a look at your mount options for an NTFS partition.

Kind regards

---

