---
title: "Can't apply updates"
date: 2009-06-30
forum: General Help
---

### Post by snifferpro on 2009-06-30
Hi. Linux Noob here.

Just installed Ubuntu 9.04 to a 100.5gb partition on a new 500gb hard drive.

Was just poking around after install to get my feet wet when I got a
pop up about updates.

Selected to apply updates and got message "not enough space to install
updates - empty trash and run sudo command".

I emptied the trash and ran the sudo command and tried again.

Got same results.

I thought I allocated 100.5gb partition for Unbuntu but message indicates
I only have about 348mb.

Any help appreciated.

Thanks

---

### Post by kpkeerthi on 2009-06-30
Post the output of
```
df -h
```

---

### Post by Celauran on 2009-06-30
Also this:

```
sudo du -sh /*
```

---

### Post by snifferpro on 2009-06-30
Screen shots attached

---

### Post by Soul-Sing on 2009-06-30
PLease run ```
sudo gparted
``` to make visible how you did partition your harddisk.
Via an Ubuntu live-cd you can add more space to the partition you installed ubuntu on.
(Or download the gparted iso, burn it, run as a live-cd, and more space to the partition with Ubuntu.)

---

### Post by snifferpro on 2009-06-30
Here is output of sudo gparted.

Am I correct in assuming that the install only carved out enough space
for Linux and the rest of the volume is NTFS format which is how I
formatted the drive under windows.

I'd like a 100.5 gb partition for Linux and the rest free for eventual
install of Win 7 RC.

Can I use gparted to do this or would it be easier to just reinstall
Ubuntu and select whole drive, then use gparted to reduce Linux space?

---

### Post by Soul-Sing on 2009-06-30
> **snifferpro said:**
> Here is output of sudo gparted.

Am I correct in assuming that the install only carved out enough space
for Linux and the rest of the volume is NTFS format which is how I
formatted the drive under windows.

I'd like a 100.5 gb partition for Linux and the rest free for eventual
install of Win 7 RC.

Can I use gparted to do this or would it be easier to just reinstall
Ubuntu and select whole drive, then use gparted to reduce Linux space?

If you consider to reinstall Ubuntu, then I recommend to install Vista/w-7 first. Remember Vista/w-7 takes more then 10 GB! Reserve for Ubuntu [COLOR="Red"]more[/COLOR] then 4GB. Maybe with a seperate /home partition.(20GB?)
I recommend reading the off. Ubuntu documentation howto set-up a dualboot situation.

edit: your partition with Ubuntu installed is "full".( The ext3 partition)

---

