---
title: "Updating apps and shutting down"
date: 2009-07-12
forum: General Help
---

### Post by TimEnid on 2009-07-12
When i click the running man icon, the system doesnt shut down, instead, the tool bars disappear and only my desktop is visible.

second, when i try to update apps, i get this message:

e: dpkg was interrupted. you must manually run 'dpkg --configure-a to correct the problem/
e:_cache_>open()failed. please report.

any help

thanks

---

### Post by philinux on 2009-07-12
Open and terminal and use.

```
sudo dpkg --configure-a
```

---

### Post by TimEnid on 2009-07-12
> **philinux said:**
> Open and terminal and use.

```
sudo dpkg --configure-a
```

after doing this it now says :
dpkg: unknown option --configure-a
Options marked 
[*] produce a lot of output - pipe it through 'les' or 'more'

---

### Post by mgranet on 2009-07-12
That should read ```
sudo dpkg --configure -a
```

---

### Post by philinux on 2009-07-12
> **mgranet said:**
> That should read ```
sudo dpkg --configure -a
```

Hah, I copied and pasted the OP's text. :lolflag:

---

### Post by TimEnid on 2009-07-12
> **philinux said:**
> Hah, I copied and pasted the OP's text. :lolflag:
now it says :
dkg: failed to write available record about 'xserver-xorg-video-cyrix' to '/var/lib/dpkg/available': No space left on device

---

### Post by mgranet on 2009-07-12
Hrm. That's odd. It sounds like you are running out of space on /. How much disk space did you assign for Ubuntu?

---

### Post by TimEnid on 2009-07-12
> **mgranet said:**
> Hrm. That's odd. It sounds like you are running out of space on /. How much disk space did you assign for Ubuntu?

i have no idea. its actually my finaces machine. im still having trouble with the shutting down issue as well. That running man icon is not doing what its supposed to to. Im just going to by a cd drive and re-install ubuntu, or just switch to wndows xp.

---

### Post by philinux on 2009-07-12
Looks, or could be, like your root partition is full. Post the output of this.

```
df -h
```

---

### Post by TimEnid on 2009-07-12
> **philinux said:**
> Looks, or could be, like your root partition is full. Post the output of this.

```
df -h
```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             3.4G  3.4G     0 100% /
varrun                501M   64K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   36K  501M   1% /dev
devshm                501M   12K  501M   1% /dev/shm
lrm                   501M  1.9M  499M   1% /lib/modules/2.6.24-22-lpia/volatile
overflow              1.0M   20K 1004K   2% /tmp
gvfs-fuse-daemon      3.4G  3.4G     0 100% /home/enid/.gvfs
enid@enid:~$

I would like to delete some files to make space, but not sure what should be deleted

---

### Post by TimEnid on 2009-07-12
bump

---

### Post by rob2uk on 2009-07-12
First off, please don't bump a thread until you've waited 24 hours for a reply.

Secondly, your hard drive has no space left on it at all.
Are you able to move some stuff from the home directory to another disk?

---

### Post by oldos2er on 2009-07-12
Are you dual-booting with Windows? Perhaps you could post the output of **sudo fdisk -l** so we can get an idea of your hard disk(s) setup.

 In the meanwhile, here's some info on clearing hard disk space: [http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

### Post by michy99 on 2009-07-12
> **TimEnid said:**
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             3.4G  3.4G     0 100% /
varrun                501M   64K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M   36K  501M   1% /dev
devshm                501M   12K  501M   1% /dev/shm
lrm                   501M  1.9M  499M   1% /lib/modules/2.6.24-22-lpia/volatile
overflow              1.0M   20K 1004K   2% /tmp
gvfs-fuse-daemon      3.4G  3.4G     0 100% /home/enid/.gvfs
enid@enid:~$

I would like to delete some files to make space, but not sure what should be deleted

3.4G is very small for an Ubuntu installation. I recommend at least 10G. You can delete a few things to make some room, but you will run into the same problem over and over.

---

