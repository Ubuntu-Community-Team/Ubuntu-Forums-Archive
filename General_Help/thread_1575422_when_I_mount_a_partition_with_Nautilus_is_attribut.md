---
title: "when I mount a partition with Nautilus is attributed to another user"
date: 2010-09-15
forum: General Help
---

### Post by fr4nko on 2010-09-15
Hi all,

I have a really odd problem when I mount a partition with Nautilus is attributed to another user, I don't know why.

I've tried by adding the following like in /etc/fstab


/dev/sda2       /media/windoze  ext3 user,noauto,rw 0 0

then I can mount the partition but in this case it is attributed to the root and I don't have the permission to read it. I cannot understand why since I've given the 'user' option.

Please help me to clarify this strange problem :-)

Francesco

---

### Post by coffeecat on 2010-09-15
You can make use of a seemingly little known feature of Ext filesystems - that you can "own" them with the ownership set in the root of the filesystem. In this way you don't need anymore than defaults for the options field in /etc/fstab.

Try this:

fstab line:

```
/dev/sda2     /media/mountpoint    ext3    defaults    0 2
```(I believe it's best to have a 2 rather than a 0 at the end of a non-root ext filesystem fstab line.)

Mount the partition on /media/mountpoint, and now:

```
sudo chown username: /media/mountpoint
```Change 'username' to whatever your login name is and don't forget that trailing colon. Clearly the ownership of the mountpoint is changed, but so is the whole filesystem. Of course, this confuses things if you have more than one account, but useful if you're the only user.

You can extend this to removable USB drives. If you have an ext2/3/4 drive automounted, simply chown the mountpoint and next time it is automounted it will already be owned by you.

---

### Post by fr4nko on 2010-09-15
Hi,

thank you for the help, but I've done what you suggest and it doesn't work. Here the line in /etc/fstab:

> /dev/sda2       /media/windoze  ext3 defaults 0 2

and here the results of "ls -l /media":

> total 8
lrwxrwxrwx 1 root   root      6 2008-06-01 13:42 cdrom -> cdrom0
drwxr-xr-x 2 root   root   4096 2008-06-01 13:42 cdrom0
drwxr-xr-x 2 franko franko 4096 2010-09-16 00:14 windoze


My username is "franko" and I've given the command "chown" with the semicolon as you suggested.

Then, when I do "mount /dev/sda2" I get this message:


> mount: only root can mount /dev/sda2 on /media/windoze

I believe it is because I didn't give the user option if fstab.

Francesco

---

### Post by fr4nko on 2010-09-15
bump

---

### Post by coffeecat on 2010-09-16
You've done it in the wrong order. The partition must be mounted before you chown otherwise the chown command will only change the ownership of the mountpoint - which is what I see you've done. You need to have the filesystem mounted for it to be owned. More importantly, **only root can mount**, even when everything is owned by an ordinary user.

So - mount it as root:

```
sudo mount /dev/sda2 /media/windoze
```**Now** chown it again to own the filesystem:

```
sudo chown franko: /media/windoze
```Now try writing to it using drag and drop in the GUI. It works, correct?

Do you still have this line in fstab?

```
/dev/sda2          /media/windoze     ext3     defaults     0 2                      
```And have you removed or commented out your original 'users' line? If that is still there it might confuse the system having two lines for the same device and mountpoint.

Now unmount sda2:

```
sudo umount /dev/sda2
```Now remount it using the fstab line:

```
sudo mount -a
```And now try it again. If it doesn't work, you've made an error somewhere, so post back if so.

---

