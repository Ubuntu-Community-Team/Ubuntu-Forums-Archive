---
title: "Lots of small errors"
date: 2009-08-07
forum: General Help
---

### Post by callumacrae on 2009-08-07
Hello,

In the last hour I have had quite a lot of problems with my laptop running Ubuntu, and I have no idea what to do.

I think the cause of my problem was when I was experimenting with repartitioning my hard drive, as it is in two partitions and I can't work out how to make them into one big one. I did not manage to do this, and as far as I am aware I didn't change anything.

From then I was getting a lot of small errors:

Software wouldn't install
Applications randomly crashed
Took me quite a few attempts to log on, saying the hard drive was full (it wasn't, I have 500mb of space left on the main partition)
Software wouldn't update
Trash won't empty
Firefox isn't working: I suspect this won't have any line breaks, and neither the back or forward button are working, among other errors. It also won't submit forms. It's taken me ages to submit this one. UPDATE: Same with Opera
And others (which I can't remember - I'll write them down next time)

When the software wouldn't update, it came up with the error:

> VirtualBox will not start until this problem is fixed.

Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them (the package name is probably linux-headers-[version] whereby [version] can be determined by 'uname -r') and execute

/etc/init.d/vboxdrv setup

as root.

There was no error when I tried to delete trash, and I can't remember any of the other errors.


If anyone can help me, thanks.

~Callum


Also, is it alright to shut down? My dad is getting annoyed :]

---

### Post by michy99 on 2009-08-07
What is the output of:```
df -h
```

---

### Post by callumacrae on 2009-08-07
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.1G  7.1G     0 100% /
tmpfs                 498M     0  498M   0% /lib/init/rw
varrun                498M  220K  497M   1% /var/run
varlock               498M     0  498M   0% /var/lock
udev                  498M  144K  498M   1% /dev
tmpfs                 498M   76K  498M   1% /dev/shm
lrm                   498M  2.2M  496M   1% /lib/modules/2.6.28-14-generic/volatile
overflow              1.0M  1.0M     0 100% /tmp

---

### Post by michy99 on 2009-08-07
Your Ubuntu partition is 7.1 Gigs and it is full. You can delete some stuff to make room or expand your partition. If you want to expand your partition, I recommend this guide:

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by callumacrae on 2009-08-08
I have downloaded GParted, and it is saying that I have more than one device.

This can't be right, as who would install and 8gb hard drive?

Its a netbook, so I doubt it has more than one hard drive.

Does anyone know what is happening?

---

### Post by callumacrae on 2009-08-09
Bump.

Can anyone help?

~Callum

---

